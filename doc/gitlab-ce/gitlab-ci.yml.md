### ci.yml
stages:
  - test
  - build
  - deploy

test:
  stage: test
  script: echo "Running tests"
  only:
  - tags

build:
  stage: build
  script: echo "Building the app"
  only:
  - tags

deploy_staging:
  stage: deploy
  script:
    - echo "Deploy to staging server"
  environment:
    name: staging
    url: https://staging.example.com
  only:
  - tags

deploy_prod:
  stage: deploy
  script:
    - echo "Deploy to production server"
  environment:
    name: production
    url: https://example.com
  when: manual
  only:
  - tags
  
  ### doc
    https://docs.gitlab.com/ee/ci/yaml/README.html
    https://blog.csdn.net/xl_lx/article/details/78329089