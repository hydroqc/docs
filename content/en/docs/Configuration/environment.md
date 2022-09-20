---
title: Environment Variable
linkTitle: Environment Variable
weight: 26
description: |
  Environment variables
lastmod: 2022-09-20T18:15:42.130Z
---


## MQTT configuration variables

| Variable | Syntax | Example | Comment |
|- | - | - | - |
MQTT_USERNAME | string | hydrqoqcuser | Optional |

```
MQTT_USERNAME='yourmqttusername'
MQTT_PASSWORD='yourmqttpassword'
MQTT_HOST='yourmqttserver'
MQTT_PORT='1883'
```
## Hydro-Quebec account variables

Account variables are configurable as an array which allows you to have more than one contract synced by the integration.

| Variable | Syntax | Example | Comment |
|- | - | - | - |
| HQ2M_CONTRACTS_0_NAME | lowercase string | maison | Will show up as the device name in Home-Assistant |

```
# Name of the contract, will appear in Home Assistant and in the hydroqc topics.
HQ2M_CONTRACTS_0_NAME='maison'

# Username for your HQ account
HQ2M_CONTRACTS_0_USERNAME='email@domain.tld'

# Your HQ account password
HQ2M_CONTRACTS_0_PASSWORD='Password'

# Customer number (Numéro de client) from your invoice.
# 10 digits, you may need to add a leading 0 to the value!!!
# Ex: '987 654 321' will be '0987654321'
HQ2M_CONTRACTS_0_CUSTOMER='0987654321'

# Account Number (Numéro de compte) from your invoice
HQ2M_CONTRACTS_0_ACCOUNT='654321987654'

# Contract Number (Numéro de contrat) from your invoice
# 10 digits, you may need to add a leading 0 to the value!!!
# Ex: '123 456 789' will be '0123456789'
HQ2M_CONTRACTS_0_CONTRACT='0123456789'
```
## Home-Assistant specific variables

```
#Enable importing hourly consumption from Hydro-Quebec (last 24h)
HQ2M_CONTRACTS_0_SYNC_HOURLY_CONSUMPTION_ENABLED="true"

# URL to your Home-Assistant installation websocket API
HQ2M_CONTRACTS_0_HOME_ASSISTANT_WEBSOCKET_URL=http://home-assistant:8123/api/websocket

# Long-lived Home-Assistant access token to be used to access the API
HQ2M_CONTRACTS_0_HOME_ASSISTANT_TOKEN=dqwdq23dqwd34q234dr
```