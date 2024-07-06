# PR Contribution to Code Repo: [My PR](https://github.com/code100x/daily-code/pull/424) [100x-dailycode repo](https://github.com/code100x/daily-code)

## Error: Seed Command Failed Due to Unique Constraint Error While Seeding DB for Project Setup

- **Description**: While setting up the project locally, which included a couple of steps like:
  - Prisma migrate and Prisma seed.
  there was an error occurring due to a unique constraint issue when `npx prisma db:seed` command was executed.

- **Analysis**: 
  The reason for this was that if an error occurred while seeding, the program would exit. 
  This error could be due to an error in the seed file itself or if some unknown error occurred while seeding the DB. The logic which seeded the DB wasn't checking for the presence of unique data in tables. Due to this, when the seed command ran again, it threw a unique constraint error which would resolve if the DB was reset completely, removing the volumes in the case of Docker containers. This led to unnecessary overhead for developers. This problem of unique constraint could be solved by adding the Prisma function `upsert` which checks for the presence of data in the DB before populating the data and if it exists it won't update that particular data, thereby avoiding the unique constraint issue.

- **Program Changes**: 
  - Added `upsert` function to check for data presence.
  - Optimized the seed file logic to avoid DRY (Don't Repeat Yourself) of code by using loops and arrays for the data that was used to seed.

- **Issue Addressed in PR**: 
  - [PR Contribution](https://github.com/code100x/daily-code/pull/424)
