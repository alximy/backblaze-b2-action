## Usage

### `workflow.yml` Example

Place in a `.yml` file such as this one in your `.github/workflows` folder. [Refer to the documentation on workflow YAML syntax here.](https://help.github.com/en/articles/workflow-syntax-for-github-actions)

```yaml
name: Sync B2 Bucket
on: push

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - uses: alximy/backblaze-b2-action@master
      env:
        SOURCE_DIR: './public'
        B2_BUCKET: ${{ secrets.B2_BUCKET }}
        B2_APPKEY_ID: ${{ secrets.B2_APPKEY_ID }}
        B2_APPKEY: ${{ secrets.B2_APPKEY }}
```

### Required Environment Variables

| Key | Value | Type | Required |
| ------------- | ------------- | ------------- | ------------- |
| `SOURCE_DIR` | The local directory you wish to sync/upload to B2. For example, `./public`. | `env` | **Yes** |


### Required Secret Variables

The following variables should be added as "secrets" in the action's configuration.

| Key | Value | Type | Required |
| ------------- | ------------- | ------------- | ------------- |
| `B2_BUCKET` | The name of the bucket you're syncing to. For example, `b2://YourMainBucket/YourRepositoryName`. | `secret` | **Yes** |
| `B2_APPKEY_ID` | Your Backblaze Application Key ID. [Generate it here.](https://secure.backblaze.com/app_keys.htm) | `secret` | **Yes** |
| `B2_APPKEY` | Your Backblaze Application Key — aka the "secret" key. [Generate it here.](https://secure.backblaze.com/app_keys.htm) | `secret` | **Yes** |
