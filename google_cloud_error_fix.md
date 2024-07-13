# Google CLoud errors fix

When making Ci-cd of the microservices orders, I had several problems with the google Cloud permissions, which I solved with the following commands:


## get project YOUR_PROJECT_ID
```bash
gcloud projects list
```

## add permissive to write container logs
```bash
gcloud projects add-iam-policy-binding microservices-shop-nestjs \
    --member="serviceAccount:74874566665-compute@developer.gserviceaccount.com" \
    --role="roles/logging.logWriter"
```

## Allowing the project access to secrets
```bash
gcloud projects add-iam-policy-binding microservices-shop-nestjs \
    --member=serviceAccount:74874566665-compute@developer.gserviceaccount.com \
    --role=roles/secretmanager.secretAccessor
```

## Allowing the project to create registers (images)
```bash
gcloud projects add-iam-policy-binding microservices-shop-nestjs \
    --member="serviceAccount:74874566665-compute@developer.gserviceaccount.com" \
    --role="roles/artifactregistry.writer"
```
