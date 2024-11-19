# Appwarden Monitoring Configuration

## Getting Started

This repository contains your Appwarden monitoring configuration files. Each file in `.appwarden/monitors` describes the monitoring configuration for a single domain like in the following diagram.

```
.appwarden/
└── .monitors/
    ├── your-api-com.yml
    ├── your-dapp-com.yml
    └── your-docs-com.yml
```

To generate pre-populated monitoring configurations for your domains, replace the example domains with your own in the following command:

```
npx appwarden init -d your-api.com -d your-dapp.com -d your-docs.com
```

A monitoring configuration file contains two top level sections, `dns` and `websites`, that contain lists of `monitors` like so

```yml
# your-api-com.yml

hostname: your-api.com
version: 1
dns:
  options:
    dashboardUrl: [your-dns-dashboard.com]
  monitors:
    - name: your-api.com
      type: A
      content:
        - content: 104.21.73.192
          comment: this is the first nested record
        - content: 172.67.165.113
websites:
  monitors:
    - url: your-api.com
      status: 200
      headers:
        - name: content-type
          value: application/json
          validator: starts-withxx
```

### Monitoring configuration rules:

- DNS records may be listed individually or grouped together for convenience
- Any monitor may contain a `comment` field to add information about the entry
- Any monitor may contain a validator field

To learn more about

## Finishing up

After generating your Appwarden monitor configuration files,

1. Ensure the Appwarden [Discord bot](https://appwarden.io/add-appwarden-to-discord) is installed in your Discord server
1. Ensure the Appwarden [Github app](https://github.com/apps/appwarden) is installed in your organization
1. Inspect and modify the configuration files to your satisfaction
1. Create a new branch with your monitoring configuration changes and open a pull request to the `main` brach. Then follow the instructions from the Appwarden bot.
