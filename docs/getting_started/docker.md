# Installation - with Docker

## Requirements

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- Cloud Provider account:
    - [Google Cloud Platform](https://cloud.google.com/) project
    - [Amazon Web Services](https://aws.amazon.com/) account

## Installation

Clone the repository:

```bash
git clone
```

Create a `.env` file from the `.env.example` file:

```bash
cp .env.example .env
```

Edit the `.env` file and fill in the environment variables:

Run the platform through Docker Compose:

```bash
docker compose up -d
```

## Usage

Open the web application in your browser: [http://localhost:3000](http://localhost:3000)
