blobstore-perf
==============

This is a bosh deployment to test performance of webdav in different configurations.

## Usage

```
cp .envrc.example .envrc
# edit .envrc to use credentials to an AWS account

cp stubs/secrets.yml.example stubs/secrets.yml
```

Install bbl, the bosh bootloader. It is [here](https://github.com/pivotal-cf-experimental/bosh-bootloader).

```
./scripts/deploy-director
```

Target the director that it spins up.

```
bosh status --uuid
```

Put that into `stubs/secrets.yml`

Now, you can use the deployment:

```
scripts/deploy
```

To get into the downloader and download:

```
bosh ssh downloader --gateway_host ${DIRECTOR_IP} \
  --gateway_user vcap --strict_host_key_checking no \
  --gateway_identity_file ${PEM_FILE_FROM_BBL_OUTPUT}
```
