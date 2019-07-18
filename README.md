### Use google cloud build for a django-react project

I use this example project to try out google cloud build (with docker-compose).
A few tweaks are made to make it run again.

It creates a pipeline in cloud build to build images, run the services, and run a simple integration test.

The main juice is `cloudbuild.compose.yaml`, which is borrowed from [here](https://github.com/GoogleCloudPlatform/cloudbuild-integration-testing).

Steps:
After you [setup your gcloud](https://cloud.google.com/cloud-build/docs/running-builds/start-build-manually), 

use the following command to manually trigger a build:
```
gcloud builds submit --config=cloudbuild.compose.yaml .
```
You can certainly connect the github repo with cloud build as a trigger.

Todos:
- [ ] [Manage secrets](https://cloud.google.com/cloud-build/docs/securing-builds/use-encrypted-secrets-credentials)
- [ ] [Customized build logic](https://github.com/GoogleCloudPlatform/cloud-builders/issues/431)
- [ ] Deployment.
