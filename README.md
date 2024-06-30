# sfguide-terraform-sample
A repository containing a Terraform project that manages Snowflake account objects through code

# Create an RSA key for Authentication

``` bash
$ cd ~/.ssh
$ openssl genrsa 2048 | openssl pkcs8 -topk8 -inform PEM -out snowflake_tf_snow_key.p8 -nocrypt
$ openssl rsa -in snowflake_tf_snow_key.p8 -pubout -out snowflake_tf_snow_key.pub
```

# Add Account Information to Environment
For multiple project it is recommended to put snow.env file that you can sourc

``` bash
$ export SNOWFLAKE_USER="tf-snow"
$ export SNOWFLAKE_AUTHENTICATOR=JWT
$ export SNOWFLAKE_PRIVATE_KEY=`cat ~/.ssh/snowflake_tf_snow_key.p8`
$ export SNOWFLAKE_ACCOUNT="YOUR_ACCOUNT_LOCATOR"
```

# To generate an terraform documentation

Install "terraform-docs":

``` bash
sudo snap install terraform-docs
```

Generate documentation inside the folder terraform:


``` bash
terraform-docs markdown table . > terraform_documentation.md
```