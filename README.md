### Use google cloud build for a django-react project

I use this example project to try out google cloud build (with docker-compose).
A few tweaks are made to make it run again.

It creates a pipeline in cloud build to build images, run the services, and run a simple integration test.

The main juice is `cloudbuild.compose.yaml`, which is borrowed from [here](https://github.com/GoogleCloudPlatform/cloudbuild-integration-testing).

After you [setup your gcloud](https://cloud.google.com/cloud-build/docs/running-builds/start-build-manually), use the following command to trigger a build

```
gcloud builds submit --config=cloudbuild.compose.yaml .
```
You can certainly connect the github repo with cloud build as a trigger.

Todo
[ ] Manage secrets?
[ ] Customized build logic (e.g., certain actions on a certain branch etc.)?
[ ] Deployment.