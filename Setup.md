# ApiFlows Setup

[TOC](./README.md#table-of-content) | [NEXT GUIDE](./Tasks.md)

* [Create a user](#create-a-user)
* [Download ApiFlows CLI](#download-apiflows-cli)
* [Get CLI access token](#get-cli-access-token)


.
## Create a user
ApiFlows MVP2 users are authentified with an Azure Active Directory B2C Authentication Server.
To create a user , you need a web browser and an email-address
* navigate to [apivalley.org](https://apivalley.org)
* click on **Try ApiFlows** on top right
* click on **Create an account**
* fill in your **Email Address** then click on **Send verification code**

At this stage, you must receive an email with the following object : apiflows account email verification code.
It contains your email verrification code.

* fill in **Verification code** then click on **Verify code**

At this stage, your email was verrified. You can enter the fields needed to create a ApiFlows user, then click on **create**.
All fields are mandatory.

[Back to top](#apiflows-setup)


## Download ApiFlows CLI

* If you're a linux user, please download [apiflows linux binary](https://github.com/ApiValley/ApiFlows-CLI/raw/master/linux/apiflows)
* If you're a windows user, please download [apiflows.exe windows binary](https://github.com/ApiValley/ApiFlows-CLI/raw/master/windows/apiflows.exe)

[Back to top](#apiflows-setup)

## Get CLI access token

### Linux

* make apiflows binary executable
```bash
> chmod +x /path_to_apiflows_binary/apiflows
```
* add af path to your PATH environment variable
```bash
> export PATH=/path_to_apiflows_binary:$PATH
```
* execute init apiflows subcommand
```bash
> apiflows init
```


###  windows

[Back to top](#apiflows-setup)

[TOC](./README.md#table-of-content) | [NEXT GUIDE](./Tasks.md)