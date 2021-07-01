# Getting Started

## Requirements

- [Docker](https://www.docker.com/products/docker-desktop)
- [Stripe CLI](https://stripe.com/docs/stripe-cli)
- [PostgreSQL](https://www.postgresql.org/download)
- [Terraform](https://www.terraform.io/downloads.html)
- [act](https://github.com/nektos/act#installation)

## First steps

### Build [LocalStack][localstack] image and start

Run

```
docker-compose up --build
```

### Create tables, views, etc.

Run [`schema.sql`](schema.sql).

### Initialize Terraform

***Note:** you must run the following command inside the [terraform/local](terraform/local) folder.*

Run

```
terraform init
```

### Create Elasticsearch indeces

Run

```
curl -X PUT "http://localhost:4571/articles"
curl -X PUT "http://localhost:4571/publishers"
```

to create the `articles` and `publishers` indeces.

## Basics

### Stripe

#### Listen for events

Run

```
stripe listen -f localhost:4000/webhooks/stripe
```

#### Resend event

Run

```
stripe events resend EVENT_ID
```

where `EVENT_ID` is the id of the event to resend.

### Terraform

***Note:** you must run the following commands inside the [terraform/local](terraform/local) folder.*

#### See what changes will be applied

Run

```
terraform plan
```

#### Apply changes

Run

```
terraform apply
```

### GitHub Actions

#### Test

Run

```
act
```

[act]: https://github.com/nektos/act
[localstack]: https://github.com/localstack/localstack
[terraform]: https://www.terraform.io
