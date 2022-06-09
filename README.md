# hitc-audit-demo -- Using ScoutSuite in AWS Azure, and GCP

## PREREQUISITES

This lab assumes that you have completed [Episode 10 - Demonstration of Terraform Modules; Deploy a VM in AWS, Azure and GCP at once](https://headintheclouds.site/episodes/episode10) so that you have environments to test.

## SETUP

First, ScouteSuite must be installed. These instructions assume that you are using Ubuntu. The following instructions come from [https://github.com/nccgroup/ScoutSuite/wiki/Setup](https://github.com/nccgroup/ScoutSuite/wiki/Setup):

```
git clone https://github.com/nccgroup/ScoutSuite
cd ScoutSuite
sudo apt install -y python3-virtualenv
virtualenv -p python3 venv
source venv/bin/activate
pip install -r requirements.txt
python scout.py --help

```

## Scan AWS using AWS Credentials

The credentials should already be set up if you completed [HitC Episode 10](https://github.com/nccgroup/ScoutSuite/wiki/Setup) as part of the setup. Simply run the following command:

```
python scout.py aws
```

If you are using a named profile, use:

```
python scout.py aws --profile default

```

Where `default` is the name of the profile that you would like to use.

## Scan Azure

This assumes that you have logged into Azure using `az login` as part of the set up.

To perform a scan, run:

```
python scout.py azure --cli

```

If you have not logged in yet, run:

```
python scout.py azure --user-account-browser

```

And this will allow you to log into Azure with your browser

## Scan GCP

For this scan, we will use the service account on the machine. In this example, we are assuming that the service account in in a directory named "accesskey" off the users home directory and that the key is named "service_account.json" as instructed in [HitC Episode 10](https://github.com/nccgroup/ScoutSuite/wiki/Setup).

Simply run the command:

```
python scout.py gcp --service-account "~/accesskey/service_account.json"

```

## Reviewing the Scans

After each scan is run, the process will open your default browser to a web page that will display the results. Take a moment to review the findings.
