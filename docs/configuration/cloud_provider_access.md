# Cloud Provider Access

## Principles

Retrieving Cloud Projects requires some kind of rights on the Cloud Provider platform. You need to provide the platform with the credentials to access the Cloud Provider platform in order to retrieve the Cloud Projects.

Each supported Cloud Provider platform has its own way to provide access to the platform. The platform supports the following Cloud Provider platforms.

## Configuration

### Amazon Web Services

Requirements:

* Amazon Web Services Organization ID
* Amazon Web Services Project Name

Values that will be used in the following configuration:

* Amazon Web Services Organization ID: `123456789012`
* Amazon Web Services Account Name: `cloudia-project`
* Service Account Name: `cloudia-svc`
* Service Account Credentials:
    * Access Key ID: `xxxxxxxxxxxxxxxxxxxx`
    * Secret Access Key: `xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

Choose a Amazon Web Services Platform project to store the assets relating to Cloudia.

```bash
aws configure
```

Create a IAM User (that will be used as service account).

```bash
aws iam create-user --user-name cloudia-svc
```

```json
{
    "User": {
        "Path": "/",
        "UserName": "cloudia-svc",
        "UserId": "xxxxxxxxxxxxxxxxxxxx",
        "Arn": "arn:aws:iam::123456789012:user/cloudia-svc",
        "CreateDate": "2023-12-20T21:52:51+00:00"
    }
}
```

Attach IAM policy `AWSOrganizationsReadOnlyAccess` to the IAM User.

```bash
aws iam attach-user-policy --user-name cloudia-svc --policy-arn arn:aws:iam::aws:policy/AWSOrganizationsReadOnlyAccess
```

Generate the access key ID and secret access key.

```bash
aws iam create-access-key --user-name cloudia-svc
```

```json
{
    "AccessKey": {
        "UserName": "cloudia-svc",
        "AccessKeyId": "xxxxxxxxxxxxxxxxxxxx",
        "Status": "Active",
        "SecretAccessKey": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
        "CreateDate": "2023-12-20T21:55:50+00:00"
    }
}
```

The credentials `AccessKeyId` and `SecretAccessKey` will be used in the API through the `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` environment variable.

### Google Cloud Platform

Requirements:

* Google Cloud Organization ID
* Google Cloud Project Name

Values that will be used in the following configuration:

* Google Cloud Organization ID: `123456789012`
* Google Project Name: `cloudia-project`
* Service Account Name: `cloudia-svc`
* Service Account Key File: `gcp_service-account_key-file.json`

Choose a Google Cloud Platform project to store the assets relating to Cloudia.

```bash
gcloud config set project cloudia-project
```

Create a service account.

```bash
gcloud iam service-accounts create cloudia-svc --description="DESCRIPTION" --display-name="resource-manager-list"
```

Assign organizations level permission to the service account.

```bash
gcloud organizations add-iam-policy-binding 123456789012 --member="serviceAccount:cloudia-svc@cloudia-project.iam.gserviceaccount.com" --role="roles/resourcemanager.folderViewer"
```

Create the service account key file.

```bash
gcloud iam service-accounts keys create gcp_service-account_key-file.json --iam-account cloudia-svc@cloudia-project.iam.gserviceaccount.com
```

The service account key file `gcp_service-account_key-file.json` will be used in the API through the `GCP_SERVICE_ACCOUNT_JSON_KEY_FILE` environment variable.
