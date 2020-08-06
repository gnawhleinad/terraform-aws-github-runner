# Module - GitHub App web hook

This module creates an API gateway endpoint and lambda function to handle GitHub App webhook events.

## Usages

Usage examples are available in the root module. By default the root module will assume local zip files containing the lambda distribution are available. See the [download lambda module](../download-lambda/README.md) for more information.

## Lambda Function

The Lambda function is written in [TypeScript](https://www.typescriptlang.org/) and requires Node 12.x and yarn. Sources are located in [./lambdas/webhook].

### Install

```bash
cd lambdas/webhook
yarn install
```

### Test

Test are implemented with [Jest](https://jestjs.io/), calls to AWS and GitHub are mocked.

```bash
yarn run test
```

### Package

To compile all TypeScript/JavaScript sources in a single file [ncc](https://github.com/zeit/ncc) is used.

```bash
yarn run dist
```

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| aws\_region | AWS region. | string | n/a | yes |
| encryption | KMS key to encrypted lambda environment secrets. Either provide a key and `encrypt` set to `true`. Or set the key to `null` and encrypt to `false`. | object | n/a | yes |
| environment | A name that identifies the environment, used as prefix and for tagging. | string | n/a | yes |
| github\_app\_webhook\_secret |  | string | n/a | yes |
| lambda\_timeout | Time out of the lambda in seconds. | number | `"10"` | no |
| lambda\_zip | File location of the lambda zip file. | string | `"null"` | no |
| role\_path | The path that will be added to the role, if not set the environment name will be used. | string | `"null"` | no |
| role\_permissions\_boundary | Permissions boundary that will be added to the created role for the lambda. | string | `"null"` | no |
| sqs\_build\_queue | SQS queue to publish accepted build events. | object | n/a | yes |
| tags | Map of tags that will be added to created resources. By default resources will be tagged with name and environment. | map(string) | `{}` | no |

## Outputs

| Name | Description |
|------|-------------|
| endpoint\_relative\_path |  |
| gateway |  |
| lambda |  |
| role |  |

<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->

## Philips Forest

This module is part of the Philips Forest.

```

                                                     ___                   _
                                                    / __\__  _ __ ___  ___| |_
                                                   / _\/ _ \| '__/ _ \/ __| __|
                                                  / / | (_) | | |  __/\__ \ |_
                                                  \/   \___/|_|  \___||___/\__|

                                                                 Infrastructure

```

Talk to the forestkeepers in the `forest`-channel on Slack.

[![Slack](https://philips-software-slackin.now.sh/badge.svg)](https://philips-software-slackin.now.sh)