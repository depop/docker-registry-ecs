# docker-registry-ecs
Docker image to run Docker private registry (v2) on Amazon ECS

We originally extended the allingeek/registry:2-s3 base image but we needed to add HTTP Basic Auth (over TLS). We then decided to fork the Elastic.io Github repository to use our existing base image but benefit from their authorisation configuration, documentation and the fact that the config.yml didn't have credentials by default, we use IAM instance profiles so we wanted to send empty values through to the underlying library.

It is worth noting that we had to pass empty strings through to the YAML file using the following syntax in our TaskDefinition;

~~~
{
  "name": "REGISTRY_STORAGE_S3_ACCESSKEY",
  "value": "''"
}
~~~
