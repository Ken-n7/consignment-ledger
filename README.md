# EFP Supply Chain

![EFP Supply Chain dashboard](https://ken-n7.github.io/portfolio/previews/consignment-ledger.jpg)

Stock control for a fresh-produce supplier that ships on consignment. The
goods sit on a retailer's shelf and only get paid for once they sell. The app
tracks what went out to each branch, what sold, what's near expiry and what
came back, so the monthly count is an actual number instead of a guess.

Made as a prototype for a management information systems course. It isn't
deployed anywhere.

[Watch the walkthrough](https://ken-n7.github.io/portfolio/previews/efp-presentation.mp4)

## What it does

- **Products and batches.** Tracks stock levels, SKUs, production and expiry
  dates, and flags low stock and near-expiry items.
- **Movements.** Records production in, delivery out to a branch, returns and
  losses, and keeps stock in sync with each one.
- **Reconciliation.** Compares delivered stock against reported sales per
  branch and tracks discrepancies until they're resolved.
- **Reports, dashboard and an audit log.**
- **Roles.** Admin, Warehouse, Sales and Accountant each see only their part.

| Role | Can do |
|---|---|
| Admin | Everything |
| Warehouse | Production in, losses |
| Sales | Deliveries out |
| Accountant | Reconciliation and reports |

## Stack

Django 5.1, MySQL 8.4, Bootstrap 5, crispy-forms, Docker Compose.

## Run it

```sh
docker compose up
docker exec supply-chain-match-web-1 python manage.py migrate
docker exec supply-chain-match-web-1 python manage.py seed_data   # sample data and demo users
```

The app runs at http://localhost:8000, and phpMyAdmin at http://localhost:8080.
The passwords in `docker-compose.yml` and `seed_data` are for local demos only.

## Docs

- [`USER_GUIDE.md`](USER_GUIDE.md): every screen, by role
- [`ARCHITECTURE.md`](ARCHITECTURE.md): models, views and stock rules
- [`DEV_COMMANDS.md`](DEV_COMMANDS.md): Docker and Django commands
- [`TROUBLESHOOTING.md`](TROUBLESHOOTING.md)
