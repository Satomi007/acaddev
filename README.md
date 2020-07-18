# Project Title.   @ hey my first commit :)

CI/CD pipeline - AWS - Jenkins - GitHub

## CD

- Head branch or master branch is related to the Prod pipeline jenkins
    - jenkins read into the jenkinfile script (gradle script) to construct the pipeline from the SCM - build - deploytoPROD stage.
        - jenkins first extract the target directory src and excecute a publishoverssh of the content of src to the default apache directory of the designated server (Prod web server) 

- dev branch is related to the Dev pipeline jenkins
    - jenkins read into the jenkinfile script (gradle script) to construct the pipeline from the SCM - build - deploytoDEV stage.
        - jenkins first extract the target directory src and excecute a publishoverssh of the content of src to the default apache directory of the designated server (DEV web server)


- for a instantaneous build now on jenkins after a new commit on the branch, a webhook has been created, which allow jenkins to be awared of a new commit.

- a personal access token is created in GitHub to allow jenkins to communicate with GitHub repositories

- Gradle is an open-source build automation tool focused on flexibility and performance. Gradle build scripts are written using a Groovy or Kotlin DSL.
