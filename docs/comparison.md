# VM vs Managed MySQL – Comparison

For this homework, I deployed MySQL in GCP using two approaches: a self-managed VM and a managed Cloud SQL instance.

On the VM, I had to configure the operating system, install MySQL, open firewall ports (22 and 3306), edit mysqld.cnf to update the bind address to 0.0.0.0, create and authorize users, and manage security on my own. This setup took longer because I had to troubleshoot network connectivity and instance configuration, but I had full control over the environment. For a small student application, the VM is acceptable and inexpensive, though it still requires periodic updates and maintenance.

In contrast, the managed Cloud SQL instance was much faster to get running after networking and user permissions were configured. Although I initially had difficulty connecting, Google handles OS patches, automatic backups, and point-in-time recovery for me. My required steps were simpler: choose a machine tier, enable a public IP with an authorized network, create the assignmentdb database, and create a non-root user (xiao@%) with the appropriate privileges. For a departmental analytics database with multiple users, Cloud SQL is the better choice because scaling, monitoring, and user management are built in and significantly easier than maintaining a custom VM.

For a HIPAA-aligned workload, I would definitely choose the managed service. Security and data protection are critical, and Cloud SQL provides automatic backups, PITR, encryption at rest, fine-grained IAM controls, and the option to disable public IPs and use private networking. While a self-managed VM could be hardened to meet similar requirements, the operational burden and risk of misconfiguration are much higher compared to using a managed MySQL service.
