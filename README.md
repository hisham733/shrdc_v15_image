# SHRDC v15 Image

Custom ERPNext v15 Docker image with all migrated apps pre-installed.

## Apps Included

| App | Source |
|---|---|
| Autocount | hisham733/autocount_v15 |
| Short Courses | hisham733/short_courses_v15 |
| Frepple | hisham733/frepple_v15 |
| Barcode SHRDC | hisham733/barcode_shrdc_v15 |
| Telegram Integration | hisham733/erpnext_telegram_integration_v15 |
| HRMS | hisham733/hrms_v15 |
| Metabase Integration | hisham733/metabase_integration_v15 |
| Shopify | hisham733/shopify_v15 |
| SQL Accounting Software | hisham733/sql_accounting_software_v15 |

## Build the Image

This repo includes a GitHub Actions workflow that automatically builds and pushes the image when changes are pushed to `main`.

### Required Secret

Add a **Docker Hub access token** as a repository secret named `DOCKER_PAT`:

1. Go to https://hub.docker.com/settings/security
2. Create a new access token with Read & Write permissions
3. Add it to this repo: Settings → Secrets and variables → Actions → New repository secret
4. Name: `DOCKER_PAT`, Value: *(your token)*

### Trigger a Build

- Push to `main` branch, or
- Go to Actions → "Build and Push Custom Frappe Image" → Run workflow

The image will be pushed to `hisham733/erpnext-custom:v15`.

## Deploy

```bash
docker compose -f shrdc-compose.yml up -d
```

Wait a few minutes for the site to be created. Check progress:

```bash
docker compose -f shrdc-compose.yml logs create-site -f
```

Once complete, access ERPNext at http://localhost:8080

- **Username**: Administrator
- **Password**: admin

## Customize

Edit `apps.json` to add or remove apps, then push to trigger a new build.
