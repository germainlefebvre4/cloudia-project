# Environment Variables

## API Configuration

### Environment variables

The platform is configured through environment variables. The environment variables are defined in the `.env` file.

| Name | Description | Default value |
| --- | --- | --- |
| `BACKEND_CORS_ORIGINS` | List of allowed origins for the CORS headers | `["http://localhost", "http://localhost:4200", "http://localhost:3000", "http://localhost:8080", "http://localhost:8888", "https://localhost", "https://localhost:4200", "https://localhost:3000", "https://localhost:8080"]` |
| `GCP_SERVICE_ACCOUNT_JSON_KEY_FILE` | Path to the Google Cloud Platform service account JSON key file | `service-account-key-file.json` |
| `GCP_ORGANIZATION_ID` | Google Cloud Platform organization ID | `123456789012` |
| `AWS_ACCESS_KEY_ID` | Amazon Web Services access key ID | `xxxxxxxxxxxxxxxxxxxx` |
| `AWS_SECRET_ACCESS_KEY` | Amazon Web Services secret access key ID | `xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx` |
| `AWS_DEFAULT_REGION` | Amazon Web Services default region | `us-east-1` |
