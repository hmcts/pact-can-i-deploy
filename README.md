## 📦 Pact Can I Deploy Action

This GitHub Composite Action checks whether a Pact-icipant version can be safely deployed to a given environment using the Pact Broker CLI.

> ℹ️ Use this when you want to block deployment unless a pact version has been verified by all required consumers or providers in the target environment.

### 🚀 Usage

```yaml
- uses: hmcts/pact-can-i-deploy
  with:
    pact_broker_token: ${{ secrets.PACT_BROKER_TOKEN }}
    pacticipant: ProviderApplicationName
    pacticipant_version: 0.0.1
    pact_env: dev/pactTest
    pact_broker_base_url: https://hmcts-dts.pactflow.io # Optional, defaults to HMCTS-DTS Pact Broker
```

### ✅ What It Does

1. Installs the Pact CLI
2. Tags the given Pacticipant artefact version with the environment
3. Runs `can-i-deploy` check and fails the job if it cannot be deployed

### 📝 Inputs

| Name                     | Required | Description                                                  |
|--------------------------|----------|--------------------------------------------------------------|
| `pact_broker_token`  | ✅       | Token used to authenticate with the Pact Broker |
| `pacticipant_version` | ✅     | The specific version of the pacticipant                      |
| `pacticipant`            | ✅       | The name of the pacticipant (e.g. `ProviderApplicationName`) |
| `pact_env`               | ✅       | The target environment for the deployment check              |
| `pact_broker_base_url`   |          | Optional. Defaults to the HMCTS-DTS organisation URL, i.e. https://hmcts-dts.pactflow.io |

