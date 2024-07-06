# PR Contribution to Code Repo: [My PR](https://github.com/code100x/chess/pull/344) , [Code Repo](https://github.com/dishak/chess/tree/docker-n-hotreload)


## Error : Task to dockerise the application for its obvious usefulness.

-   Description : Dockerising helps in easy local setup of project without depending on host OS dependencies for application execution. Makes deploying an application to K8s a breeze.

-   Analysis    : Project repo Info - It's a monorepo project a monorepo has a project structure with shared package dependecies folder to facilitate seamless sharing of shared dependencies amongst different components in a project. (packages folder has all the shared dependencies).
Frontend, backend,WebSocket,Mobile app have their project folders under app folder.
For a monorepo project structure I found it best to have a single Dockerifle at root location for easier installation of  shared dependencies.
If it was repo w/o shared dependencies then, multiple dockerfiles depending on number of services would be created inside every apps/component root location. But, I would still prefer having just 1 Dockerfile as it's easier to handle and any code editing needed to make I dont have to keep navigating the file structure.
There is a docker-compose.yml file to start all the services or apps using just 1 command.

Coming back to the Dockerfile.It has root image,intermediate , frontend,backend,ws image as divisions this style of writing Dockerfile is referred as multi-stage builds one can refer to any image and build docker image from any section and each section can use other section as it's base image there by using docker caching for lower build time.
 ## root_img   :
    - Here set of dependencies and files used by all components / services in apps folder will be in the built root_image.
    The strategy of copying and installing only the required `package.json` files first, followed by the rest of the files, aims to increase the number of layers in the Dockerfile. This approach helps reduce build time by pushing the least frequently changed files to the top, thus avoiding unnecessary builds when code changes don't affect these files.

## intermediate_img:
    - Copies remaining files from root folder except /apps & /packages this effort is deliberately to keep the resulting image size minimal.

## backend_img , frontend_img , ws_img:
    - Uses root image & intermediate image then, copies & installs dependencies only related to backend from package folder & later copies rest backend files, this procedure helps to lower build time and docker caching.

## Docker-compose.yml file :
    - It starts the 4 services (incl Postgres DB) using compose up command.

For development HMR/ hot reloading is a great tool as it will reduce executing rebuilding manually after every code edit to check the effect. Just by saving the code rebuilding happens automatically without executing build command.
For frontend vite is used which provides inbuilt HMR 
For backend and Websocket nodemon was used for this feature. For this to take effect I wrote a nodemon.json file for each of them. nodemon.json which will define file to watch out for continuously (index.ts in our case) and when changes found to execute command of rebuilding and restarting the server.


    



