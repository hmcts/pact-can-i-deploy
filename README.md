## 📦 Pact Can I Deploy Action

This GitHub Composite Action checks whether a Pact-icipant version can be safely deployed to a given environment using the Pact Broker CLI.

> ℹ️ Use this when you want to block deployment unless a pact version has been verified by all required consumers or providers in the target environment.

### 🚀 Usage

```yaml
- uses: ./.github/actions/pact-can-i-deploy
  with:
    artefact_version: 0.0.1
    pact_application_name: ProviderApplicationName
    pact_broker_base_url: https://hmcts-dts.pactflow.io
    pact_env: dev/pactTest
  secrets:
    PACT_BROKER_TOKEN: ${{ secrets.PACT_BROKER_TOKEN }}
```

### ✅ What It Does

1. Installs the Pact CLI
2. Tags the given artefact version with the environment
3. Runs `can-i-deploy` check and fails the job if it cannot be deployed

### 📝 Inputs

| Name                  | Required | Description                                                  |
|-----------------------|----------|--------------------------------------------------------------|
| `artefact_version`    | ✅       | The specific version of the pacticipant                      |
| `pact_application_name` | ✅     | The name of the pacticipant (e.g. `ProviderApplicationName`) |
| `pact_broker_base_url` |         | Optional. Defaults to the HMCTS-DTS organisation URL, i.e. https://hmcts-dts.pactflow.io  |
| `pact_env`            |         | Optional. Defaults to `dev/pactTest`                         |

### 🔐 Secrets

| Name                 | Required | Description                     |
|----------------------|----------|---------------------------------|
| `PACT_BROKER_TOKEN`  | ✅       | Token used to authenticate with the Pact Broker |
