# pypassbolt-api

## About

Python library for Passbolt API based on [httpx](https://www.python-httpx.org/) and [PGPy](https://pgpy.readthedocs.io/en/latest/).

You can also use [python-gnupg](https://docs.red-dove.com/python-gnupg/) if needed but it is not the default.

## How to install

```sh
python -m pip install pypassbolt-api
```

## How to use

### config.json configuration file

Basically, create a `config.json` file containing needed configuration. You will find samples:

* For PGPy (default): [config.json.PGPy.sample](https://gitlab.com/AnatomicJC/py-passbolt/-/blob/main/config.json.PGPy.sample)
* For python-gnupg: [config.json.gnupg.sample](https://gitlab.com/AnatomicJC/py-passbolt/-/blob/main/config.json.gnupg.sample)

Then have a look at [https://gitlab.com/AnatomicJC/py-passbolt/-/blob/main/example.py](example.py) python script.

### Environment variables

Mandatory:

* PASSBOLT_BASE_URL: Your passbolt URL

For PGPy:

* PASSBOLT_PRIVATE_KEY: Your passbolt private key in one-line format (See below about how to format)
* PASSBOLT_PASSPHRASE: Your passbolt passphrase

For python-gnupg:

* PASSBOLT_GPG_BINARY (Optional): path to your gpg binary, default to "gpg"
* PASSBOLT_GPG_LIBRARY: Set this to gnupg, otherwise it will be the default "PGPy"
* PASSBOLT_FINGERPRINT: The OpenPGP key fingerprint to use

## How to set OpenPGP key in config.json or environment variables

### Linux:

```sh
sed -z 's/\n/\\n/g' passbolt_private.txt
```

### MacOS

Install `gnu-sed` with brew:

```sh
brew install gnu-sed
```

Use gsed instead of sed:

```sh
gsed -z 's/\n/\\n/g' passbolt_private.txt
```

>Note: Almost all the source code has been obtained from the existing py-passbolt library, with some extra functions. [py-passbolt](https://github.com/passbolt/lab-passbolt-py.git)
