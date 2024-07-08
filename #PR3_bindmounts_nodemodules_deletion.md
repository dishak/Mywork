# PR Contribution to Code Repo: [My PR](https://github.com/ayush-oswal/Collaborative-code-editor/pull/2) ,  [code repo](https://github.com/ayush-oswal/Collaborative-code-editor)

## Error: Cloning the repository and running docker-compose up,  the containers exited with errors like "typescript 'tsc' not found". 

- **Description**: While setting up the project locally, using docker compose up the services containers were exiting. giving dependencies uninstalled error like tsc (typescript) not found error inspite of nodemodules present in the built docker images of the services.

- **Analysis**: 
  The reason for this was the nodemodules were not present in the containers when sshed into them. This should not happen because the base image indeed had the nodemodules in it from which container was created. Further analysis on this  I found that the bindmounts were the real problem. The bindmounts as written in docker compose file had the services host directory mounted at the root directory of the container.But, the host directory didn't had node_modules due to this the container directory was also updated with host directory as it was bind mounted there by deleting the container node_modules. The node_modules have all the dependenices for a project to run. As the node_modules were absent this caused in dependencies error like tsc not found (here tsc is typescript compiler being invoked). The solution found for this was : writing a script file which would check for node_modules presence in the container if not, install them  as soon as containers were started.This solution resolved the problem. The solution is provided in the PR link given.

- **Issue Addressed in PR**: 
  - [PR Contribution](https://github.com/ayush-oswal/Collaborative-code-editor/pull/2)
