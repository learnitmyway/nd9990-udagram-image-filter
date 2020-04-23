# Udagram Image Filter

An image filter that is part of the [Cloud Developer Nanodegree](https://www.udacity.com/course/cloud-developer-nanodegree--nd9990)

[Link to starter code](https://github.com/udacity/cloud-developer/tree/master/course-02/project/image-filter-starter-code)

## Project instructions

1.  Setup Node Environment
    You'll need to create a new node server. Open a new terminal within the project directory and run:

        Initialize a new project: `npm i`

    run the development server with `npm run dev`

2.  Create a new endpoint in the server.ts file

    The starter code has a task for you to complete an endpoint in `./src/server.ts` which uses query parameter to download an image from a public URL, filter the image, and return the result.

    We've included a few helper functions to handle some of these concepts and we're importing it for you at the top of the `./src/server.ts` file.

    ```
    import {filterImageFromURL, deleteLocalFiles} from './util/util';
    ```

3.  Deploying your system
    Follow the process described in the course to `eb init` a new application and `eb create` a new environment to deploy your image-filter service! Don't forget you can use `eb deploy` to push changes.

4.  Submit your project
    The project submission should include:

    - a Git repository
    - a screenshot of the elastic beanstalk application dashboard after deployement
    - a link to the endpoint URL for a running elastic beanstalk deployment either in the Project README or in the project submission notes.

## Run locally

- `npm install`
- `npm run dev`
- Go to `http://localhost:8082/filteredimage?image_url=https://res.cloudinary.com/developerdavo/image/upload/f_auto,q_70,w_1000/v1566583881/learnitmyway/jan-tinneberg-tVIv23vcuz4-unsplash_by3gwy.jpg`

## Brew Fromulae

- awscli
- awsebcli

## AWS Setup

### AWS IAM

#### Add user that has access to AWS Elastic Beanstalk

- Add user (eg. udagram-david-dev) with programmatic and console access

  - Add Permissions
    - AWSElasticBeanstalkFullAccess
    - AdministratorAccess (Apparently this is only needed for setting up the load balancer at the beginning and it should be removed after deploying the load balancer)

### Configure locally

- `aws confgiure`
- Check everything is ok in `~/.aws`

### AWS Elastic Beanstalk

- `eb init` (node, ssh)
- Add the following to `.elasticbeanstalk/config.yml`, before and at the same level as `global:`

```yaml
deploy:
  artifact: ./www/Archive.zip
```

#### Deploy environment for the first time

- `npm run build`
- `eb create`
  - Choose application load balancer when prompted

## Deployment

- `npm run build`
- `eb deploy`
- Go to `http://nd9990-udagram-image-filter-dev-dev.us-east-1.elasticbeanstalk.com/filteredimage?image_url=https://res.cloudinary.com/developerdavo/image/upload/f_auto,q_70,w_1000/v1566583881/learnitmyway/jan-tinneberg-tVIv23vcuz4-unsplash_by3gwy.jpg`

## Terminate

- `eb terminate`
