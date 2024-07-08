# PR Contribution to Code Repo: [My PR](https://github.com/ayush-oswal/Collaborative-code-editor/pull/2), [code repo](https://github.com/ayush-oswal/Collaborative-code-editor)

## Error: Cloning the repository and running `docker-compose up`, the containers exited with errors like "typescript 'tsc' not found".

- **Description**: While setting up the project locally using `docker-compose up`, the service containers were exiting due to dependencies not being installed, with errors like "tsc (TypeScript) not found" despite `node_modules` being present in the built Docker images.

- **Analysis**:
  The `node_modules` were not present in the containers when accessed via SSH. This should not happen because the base image indeed had the `node_modules` from which the container was created. Further analysis revealed that the bind mounts were the real problem. The bind mounts in the Docker Compose file had the service's host directory mounted at the container's root directory. However, the host directory didn't have `node_modules`. Consequently, the container's directory was updated with the host directory, deleting the container's `node_modules`. The `node_modules` directory contains all the dependencies for the project. Their absence caused dependency errors like "tsc not found" (here, `tsc` is the TypeScript compiler being invoked).

  The solution was to write a script that checks for the presence of `node_modules` in the container and installs them if not present as soon as the containers start. This solution resolved the problem. The implementation is provided in the PR link given.

- **Issue Addressed in PR**:
  - [PR Contribution](https://github.com/ayush-oswal/Collaborative-code-editor/pull/2)
