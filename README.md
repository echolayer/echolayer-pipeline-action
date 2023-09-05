# Using EchoLayer GitHub Action

## Adding the Action to your Workflow'

The EchoLayer GitHub Component Discovery action is available to you inside your existing workflows. You can add it to any workflow you want to use it in. Here’s an example of a workflow that will run the action on every push to the main branch of your repository:

```
on: [merge_group, workflow_dispatch, push]

jobs:
  echo_layer_pipeline:
    runs-on: ubuntu-latest
    name: Import Backstage Catalog to EchoLayer
    steps:
      # To use this repository's private action,
      # you must check out the repository
      - name: Checkout
        uses: actions/checkout@v3
      - name: Sync Backstage Catalog
        uses: usecodex/echolayer-pipeline-action@HEAD
        with:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          apiPath: "https://api.echolayer.com/api"
          apiKey: ${{ secrets.ECHOLAYER_API_KEY }}
```

### Environment Variables

#### `GITHUB_TOKEN`

This environment variable is provided by GitHub and is required for the action to run. You can read more about it [here](https://docs.github.com/en/actions/reference/authentication-in-a-workflow#about-the-github_token-secret).

#### `apiPath`

This environment variable calls for the API path for your EchoLayer instance. This is a required variable. If you are using the hosted version of EchoLayer, you can use the value `https://api.echolayer.com/api`.

#### `apiKey`

This environment variable calls for your EchoLayer API key which you can obtain by following the steps below. This is a required variable.

1. Visit <https://app.echolayer.com> to create your organization with EchoLayer. We only ask for a name for your org. Yes, that’s really it.

    `👉 You’ll need to authenticate with GitHub prior to this. We only ask for your email address so we can create a user account in EchoLayer for you.`

2. Once created, you’ll be redirected to the homepage for your organization in EchoLayer. Click on the link to visit the [API Key page](https://app.echolayer.com/app/account/api-keys)
    1. Generate a new API key
    2. Click the copy button
    3. Paste the value of the token temporarily somewhere you’ll have access to as you’ll need it momentarily (or just leave this open so you can come back and copy it)

## Contributing

Make changes to files in `/src`

Run `npm run build`
