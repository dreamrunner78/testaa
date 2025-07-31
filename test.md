Subject: Documentation for Kubernetes Job: Dynamic Injection of Scripts into NiFi Volumes

Hello Team,

Please find below detailed documentation explaining how to use the Kubernetes Job designed to dynamically load scripts and custom files into shared volumes accessible by the NiFi cluster, without requiring a restart of the NiFi pods.

### Job Overview:

The primary function of this Kubernetes Job is to dynamically inject scripts or other required files into a shared volume that the NiFi cluster can access directly. This approach eliminates the need to restart NiFi pods, ensuring continuous availability and streamlined updates.

### Prerequisites:

- Ensure the Kubernetes Job is deployed in the same namespace as your NiFi cluster.
- All files and scripts injected via this Job will be available at the path:
  ```
  /opt/nifi/shared
  ```

### Configuration Guide:

#### 1. ConfigMap Section:

- Use the `ConfigMap` section to specify your scripts.
- Under the `data` field, provide each script's name and its corresponding content.

Example:

```yaml
data:
  my-script.sh: |
    #!/bin/bash
    echo "Hello, NiFi!"
```

#### 2. Job Section:

This section includes critical fields to adjust based on your environment:

- **2.1 Annotations:**

  - Specify Illumio annotations that match your target deployment environment.

  Example:

  ```yaml
  annotations:
    illumio/environment: production
  ```

- **2.2 Labels:**

  - Assign appropriate labels corresponding to your specific environment.

  Example:

  ```yaml
  labels:
    app: nifi
    environment: production
  ```

- **2.3 imagePullSecrets:**

  - Define the secret for pulling Docker images relevant to your Kubernetes environment.

  Example:

  ```yaml
  imagePullSecrets:
    - name: my-registry-secret
  ```

- **2.4 containers.command:**

  - Define the commands executed at Job startup. These can include:
    - Git commands to clone required repositories.
    - Shell commands to manage files, such as backing up previous scripts, creating directories, or moving files.

  Example:

  ```yaml
  command:
    - "/bin/sh"
    - "-c"
    - |
      git clone https://git.example.com/nifi-scripts.git /tmp/scripts
      mkdir -p /opt/nifi/shared/backup
      cp /opt/nifi/shared/*.sh /opt/nifi/shared/backup/
      cp /tmp/scripts/*.sh /opt/nifi/shared/
  ```

- **2.5 volumes.sharedvolume:**

  - Ensure this volume references the actual volume shared with your NiFi cluster.

  Example:

  ```yaml
  volumes:
    - name: sharedvolume
      persistentVolumeClaim:
        claimName: nifi-shared-pvc
  ```

By following these guidelines, you can efficiently inject scripts and configuration files into your NiFi environment without interruptions.

Please reach out if you require further clarification or assistance.

Best regards,

