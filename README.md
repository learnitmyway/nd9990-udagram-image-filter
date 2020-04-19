# Udagram Image Filter

An image filter that is part of the [Cloud Developer Nanodegree](https://www.udacity.com/course/cloud-developer-nanodegree--nd9990)

[Link to starter code](https://github.com/udacity/cloud-developer/tree/master/course-02/project/image-filter-starter-code)

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

## Run locally

- `npm install`
- `npm run dev`
- Go to `http://localhost:8082/filteredimage?image_url=https://res.cloudinary.com/developerdavo/image/upload/f_auto,q_70,w_1000/v1566583881/learnitmyway/jan-tinneberg-tVIv23vcuz4-unsplash_by3gwy.jpg`
