# PR Contribution to Code Repo: [My PR](link here) ,  [code repo](link here)

## Error: N/A (This document describes the CI/CD pipeline setup, not a specific error)

- **Description**: 
  - This document provides an overview of setting up Continuous Integration (CI) and Continuous Deployment (CD) pipelines for automating code quality checks and deployment processes.

- **Analysis**: 
  - **Continuous Integration (CI)**:
    - Objective: Ensure code quality and consistency by automatically testing and validating code changes before they are merged into the main branch.
    - Steps:
      1. **Triggering the Workflow**: The CI workflow is triggered when a Pull Request (PR) is raised in a repository.
      2. **Cloning the Repository**: The workflow begins by cloning the repository to ensure it has the latest codebase.
      3. **Building the Code**: Build the code to verify that it compiles correctly without errors.
      4. **Linting and Formatting**: Use tools like ESLint and Prettier to check for code linting and formatting issues, ensuring the code adheres to the project's coding standards.
      5. **Testing and Future Enhancements**:
         - Future: Implement additional steps such as ensuring comprehensive test coverage and validating edge cases. These enhancements can increase the reliability and robustness of the CI pipeline but are not currently implemented in the existing workflow.Run automated tests to validate that the new changes do not break existing functionality.
      6. **Validation and Notification**: If any step fails, mark the PR as failed and notify the reviewer. This makes it easier for maintainers to identify issues and decide whether the PR should be merged or not.

  - **Continuous Deployment (CD)**:
    - Objective: Automate the process of deploying applications to production environments, ensuring that every change that passes the CI pipeline is automatically deployed.
    - Steps:
      1. **Triggering the Workflow**: The CD workflow is triggered on every push to the main branch of the repository.
      2. **Cloning the Repository**: The workflow starts by cloning the repository to get the latest codebase.
      3. **Signing In to DockerHub**: Authenticate with DockerHub using access keys stored in GitHub secrets to securely manage credentials.
      4. **Building and Pushing Docker Images**: Build Docker images for each application and push them to DockerHub, ensuring they are available for deployment.
      5. **Deploying to EC2**: SSH into the EC2 instance using provided secrets, pull the latest Docker images from DockerHub, and deploy the application by running the Docker containers on the EC2 instance.

- **Program Changes**: 
  - Set up CI and CD pipelines using GitHub Actions.
  - Configured workflows to automate the building, testing( scope in future), and deployment processes.

- **Issue Addressed in PR**: 
  - N/A (This document describes the CI/CD pipeline setup, not addressing a specific issue).
  - [PR Contribution](link here)
