### Use google cloud build for a django-react project

I use this example project to try out google cloud build (with docker-compose).
A few tweaks are made to make it run again.

It creates a pipeline in cloud build to build images, run the services, and run a simple integration test.

The main juice is `cloudbuild.compose.yaml`, which is borrowed from [here](https://github.com/GoogleCloudPlatform/cloudbuild-integration-testing).

Steps:
1. [Setup your gcloud](https://cloud.google.com/cloud-build/docs/running-builds/start-build-manually)
2. Install docker-compose into your project's registry
```
git clone https://github.com/GoogleCloudPlatform/cloud-builders-community.git
cd docker-compose
gcloud builds submit --config=cloudbuild.yaml .
```
3. Use the following command to manually trigger a build:
```
gcloud builds submit --config=cloudbuild.compose.yaml .
```
You can certainly connect the github repo with cloud build as a trigger.

Todos:
- [ ] [Manage secrets](https://cloud.google.com/cloud-build/docs/securing-builds/use-encrypted-secrets-credentials)
- [ ] [Customized build logic](https://github.com/GoogleCloudPlatform/cloud-builders/issues/431)
- [ ] Deployment

#### Troubleshooting
- Google provides [tool](https://github.com/GoogleCloudPlatform/cloud-build-local) for local debugging.
