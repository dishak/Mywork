# CI/CD Pipeline Issues and Solutions when executing scp (secure copy command)

## Error: Permission Denied on `mkdir`

**Issue:** Execution of the `mkdir` command resulted in a "permission denied" error when trying to access the folder.

**Solution:** Use `chown` to change the ownership of the folder to allow access.

## Error: EC2 Instance IP Address Change

**Issue:** When the EC2 instance is stopped and started, the IP address changes, causing SSH and the CD pipeline to fail with a "host connection lost" error.

**Solution:** Use `ssh-keyscan` to add the new host to the known hosts list in the runner environment.

## Error: Directory Not Found for `scp` Command

**Issue:** The `scp` command failed with a "directory not found" error when the destination directory for the remote host was not absolute or complete (e.g., `scp -i key.pem docker-compose.yml ${{ secrets.EC2_SSH_USERNAME }}@${{ secrets.EC2_SSH_HOST }}:/docker/`).

**Solution:** The `scp` command is executed from the root of the EC2 instance. Therefore, the correct `scp` command should be:
```sh
scp -i key.pem docker-compose.yml ${{ secrets.EC2_SSH_USERNAME }}@${{ secrets.EC2_SSH_HOST }}:/home/ubuntu/docker/
