# Getting Started

## Install [localstack][localstack]

### Install Docker

See [here](https://www.docker.com/products/docker-desktop).

### Build image and start

Run

```
docker-compose up --build
```

## `Stripe`

### Install CLI

See [here](https://stripe.com/docs/stripe-cli).

### Listen for events

Run

```
stripe listen -f localhost:4000/webhooks/stripe
```

### Resend event

Run

```
stripe events resend EVENT_ID
```

where `EVENT_ID` is the id of the event to resend.

## Create database

### Install PostgreSQL

See [here](https://www.postgresql.org/download/).

### Create tables, views, etc.

Run [`schema.sql`](schema.sql).

## [Terraform][terraform]

### Install

See [here](https://www.terraform.io/downloads.html).

***Note:** you must run the following commands inside the [terraform/local](terraform/local) folder.*

### Initialize

Run

```
terraform init
```

### Apply

Run

```
terraform apply
```

## Elasticsearch

Run

```
curl -X PUT "http://localhost:4571/articles"
curl -X PUT "http://localhost:4571/publishers"
```

to create the `articles` and `publishers` indeces.

## GitHub Actions

#### Install [act][act]

See [here](https://github.com/nektos/act#installation).

#### Test

Run

```
act
```

[act]: https://github.com/nektos/act
[localstack]: https://github.com/localstack/localstack
[terraform]: https://www.terraform.io
