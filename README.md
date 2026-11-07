# EFP Supply Chain

![EFP Supply Chain dashboard](https://ken-n7.github.io/portfolio/previews/consignment-ledger.jpg)

Stock control for a fresh-produce supplier that ships on consignment to six
supermarket branches.

## Why

On consignment, the goods sit on the retailer's shelf, and the supplier only
gets paid for what sells. The supplier knows what it sent out, and the store
reports what it sold, but nothing lined the two up. So at the end of the
month nobody could say for sure where the missing units went: unsold, spoiled
or expired, returned, or just never recorded. With fresh produce, that gap is
real money.

This app records every unit going in and out (production, deliveries to each
branch, returns, losses), and the stock count updates with each one.
Reconciliation puts each branch's reported sales next to what was actually
delivered, works out the difference, and keeps it open until someone resolves
it. Expiry dates are tracked per batch, so stock nearing expiry gets flagged
before it's lost. Each role gets its own part: warehouse logs production and
losses, sales logs deliveries, and accounting handles reconciliation. An
audit log records who changed what.

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
