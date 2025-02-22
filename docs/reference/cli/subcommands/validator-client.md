---
title: validator-client, vc
sidebar_position: 5
---

# `validator-client`, `vc`

Run a validator client that connects to a remote beacon node.

## `beacon-node-api-endpoint`, `beacon-node-api-endpoints`

<!--tabs-->

# Syntax

```bash
teku vc --beacon-node-api-endpoint=<ENDPOINT>[,<ENDPOINT>...]...
```

# Example

```bash
teku vc --beacon-node-api-endpoint=http://192.138.10.12:5051,http://192.140.11.44:5051
```

# Environment variable

```bash
TEKU_BEACON_NODE_API_ENDPOINT=http://192.138.10.12,http://192.140.11.44:5051
```

# Configuration file

```bash
beacon-node-api-endpoint: ["http://192.138.10.12","http://192.140.11.44:5051"]
```

<!--/tabs-->

Endpoint of the beacon node's REST API. You can configure multiple beacon nodes by providing a comma-separated list of beacon node API endpoints.

If multiple beacon node endpoints are configured, the first one is used as primary and others as failovers.

:::note

This option cannot be used with the [sentry beacon nodes early access feature](../../../how-to/use-sentry-nodes.md).

:::

The default is `http://127.0.0.1:5051`.

## `beacon-node-ssz-blocks-enabled`

<!--tabs-->

# Syntax

```bash
teku vc --beacon-node-ssz-blocks-enabled=<BOOLEAN>
```

# Example

```bash
teku vc --beacon-node-ssz-blocks-enabled=false
```

# Environment variable

```bash
TEKU_BEACON_NODE_SSZ_BLOCKS_ENABLED=false
```

# Configuration file

```bash
beacon-node-ssz-blocks-enabled: false
```

<!--/tabs-->

Enable or disable the use of SSZ encoding for API requests to the beacon node to create blocks. The default is `true`.

## `config-file`

<!--tabs-->

# Syntax

```bash
teku vc --config-file=<FILE>
```

# Example

```bash
teku vc --config-file=/home/me/me_node/config.yaml
```

# Environment variable

```bash
TEKU_CONFIG_FILE=/home/me/me_node/config.yaml
```

<!--/tabs-->

Path to the YAML configuration file. The default is `none`.

## `data-base-path`, `data-path`

<!--tabs-->

# Syntax

```bash
teku vc --data-base-path=<PATH>
```

# Example

```bash
teku vc --data-base-path=/home/me/me_node
```

# Environment variable

```bash
TEKU_DATA_BASE_PATH=/home/me/me_node
```

# Configuration file

```bash
data-base-path: "/home/me/me_node"
```

<!--/tabs-->

Path to the Teku base directory for storage. The default directory is OS-dependent:

- macOS: `~/Library/teku`
- Unix/Linux: `$XDG_DATA_HOME/teku` if `$XDG_DATA_HOME` is set; otherwise `~/.local/share/teku`
- Windows: `%localappdata%\teku`.

The default Docker image location is `/root/.local/share/teku`.

## `data-validator-path`

<!--tabs-->

# Syntax

```bash
teku vc --data-validator-path=<PATH>
```

# Example

```bash
teku vc --data-validator-path=/home/me/me_validator
```

# Environment variable

```bash
TEKU_DATA_VALIDATOR_PATH=/home/me/me_validator
```

# Configuration file

```bash
data-validator-path: "/home/me/me_validator"
```

<!--/tabs-->

Path to the validator client data. The default is `<data-base-path>/validator` where `<data-base-path>` is specified using [`--data-base-path`](#data-base-path-data-path).

## `log-color-enabled`

<!--tabs-->

# Syntax

```bash
teku vc --log-color-enabled[=<BOOLEAN>]
```

# Example

```bash
teku vc --log-color-enabled=false
```

# Environment variable

```bash
TEKU_LOG_COLOR_ENABLED=false
```

# Configuration file

```bash
log-color-enabled: false
```

<!--/tabs-->

Specify whether status and event log messages include a console color display code. The default is `true`.

## `log-destination`

<!--tabs-->

# Syntax

```bash
teku vc --log-destination=<LOG_DESTINATION>
```

# Example

```bash
teku vc --log-destination=CONSOLE
```

# Environment variable

```bash
TEKU_LOG_DESTINATION=CONSOLE
```

# Configuration file

```bash
log-destination: "CONSOLE"
```

<!--/tabs-->

Specify where to output log information. Valid options are:

- `BOTH`
- `CONSOLE`
- `DEFAULT_BOTH`
- `FILE`

The default is `DEFAULT_BOTH`. When using `BOTH` or `DEFAULT_BOTH`, system updates such as blockchain events are displayed on the console, and errors and other information are logged to a file. Specify the log file with the [`--log-file`](#log-file) command-line option.

For production systems we recommend using the `CONSOLE` or `FILE` options to ensure all log information is available in one place.

:::note

Use `DEFAULT_BOTH` when using a [custom Log4J2 configuration file](../../../how-to/monitor/configure-logging.md#advanced-custom-logging). Any other option applies the custom logging changes on top of its default settings.

:::

## `log-file`

<!--tabs-->

# Syntax

```bash
teku vc --log-file=<FILENAME>
```

# Example

```bash
teku vc --log-file=teku_2020-01-01.log
```

# Environment variable

```bash
TEKU_LOG_FILE=teku_2020-01-01.log
```

# Configuration file

```bash
log-file: "teku_2020-01-01.log"
```

<!--/tabs-->

Relative or absolute location, and filename of the log file.

The default directory is OS-dependent:

- macOS: `~/Library/teku/logs`
- Unix/Linux: `$XDG_DATA_HOME/teku/logs` if `$XDG_DATA_HOME` is set; otherwise `~/.local/share/teku/logs`
- Windows: `%localappdata%\teku\logs`

The default Docker image location is `/root/.local/share/teku/logs`.

## `log-file-name-pattern`

<!--tabs-->

# Syntax

```bash
teku vc --log-file-name-pattern=<REGEX>
```

# Example

```bash
teku vc --log-file-name-pattern=tekuL_%d{yyyy-MM-dd}.log
```

# Environment variable

```bash
TEKU_LOG_FILE_NAME_PATTERN=tekuL_%d{yyyy-MM-dd}.log
```

# Configuration file

```bash
log-file-name-pattern: "tekuL_%d{yyyy-MM-dd}.log"
```

<!--/tabs-->

Filename pattern to apply when creating log files. The default pattern is `teku_%d{yyyy-MM-dd}.log`

## `log-include-events-enabled`

<!--tabs-->

# Syntax

```bash
teku vc --log-include-events-enabled[=<BOOLEAN>]
```

# Example

```bash
teku vc --log-include-events-enabled=false
```

# Environment variable

```bash
TEKU_LOG_INCLUDE_EVENTS_ENABLED=false
```

# Configuration file

```bash
log-include-events-enabled: false
```

<!--/tabs-->

Specify whether to log frequent update events. For example every slot event with validators and attestations. The default is `true`.

## `log-include-validator-duties-enabled`

<!--tabs-->

# Syntax

```bash
teku vc --log-include-validator-duties-enabled[=<BOOLEAN>]
```

# Example

```bash
teku vc --log-include-validator-duties-enabled=true
```

# Environment variable

```bash
TEKU_LOG_INCLUDE_VALIDATOR_DUTIES_ENABLED=true
```

# Configuration file

```bash
log-include-validator-duties-enabled: true
```

<!--/tabs-->

Specify whether to log details of validator event duties. The default is `true`.

:::note

Logs could become noisy when running many validators.

:::

## `metrics-enabled`

<!--tabs-->

# Syntax

```bash
teku vc --metrics-enabled[=<BOOLEAN>]
```

# Example

```bash
teku vc --metrics-enabled=true
```

# Environment variable

```bash
TEKU_METRICS_ENABLED=true
```

# Configuration file

```bash
metrics-enabled: true
```

<!--/tabs-->

Set to `true` to enable the metrics exporter. The default is `false`.

## `metrics-host-allowlist`

<!--tabs-->

# Syntax

```bash
teku vc --metrics-host-allowlist=<hostname>[,<hostname>...]... or "*"
```

# Example

```bash
teku vc --metrics-host-allowlist=medomain.com,meotherdomain.com
```

# Environment variable

```bash
TEKU_METRICS_HOST_ALLOWLIST=medomain.com,meotherdomain.com
```

# Configuration file

```bash
metrics-host-allowlist: ["medomain.com", "meotherdomain.com"]
```

<!--/tabs-->

A comma-separated list of hostnames to allow access to the [Teku metrics]. By default, Teku accepts access from `localhost` and `127.0.0.1`.

:::tip

To allow all hostnames, use `"*"`. We don't recommend allowing all hostnames for production environments.

:::

## `metrics-categories`

<!--tabs-->

# Syntax

```bash
teku vc --metrics-categories=<CATEGORY>[,<CATEGORY>...]...
```

# Example

```bash
teku vc --metrics-categories=BEACON,JVM,PROCESS
```

# Environment variable

```bash
TEKU_METRICS_CATEGORIES=BEACON,JVM,PROCESS
```

# Configuration file

```bash
metrics-categories: ["BEACON", "JVM", "PROCESS"]
```

<!--/tabs-->

Categories for which to track metrics. Options are `JVM`, `PROCESS`, `BEACON`, `DISCOVERY`, `EVENTBUS`, `EXECUTOR`, `LIBP2P`, `NETWORK`, `STORAGE`, `STORAGE_HOT_DB`, `STORAGE_FINALIZED_DB`, `REMOTE_VALIDATOR`, `VALIDATOR`, `VALIDATOR_PERFORMANCE`. All categories are enabled by default.

## `metrics-interface`

<!--tabs-->

# Syntax

```bash
teku vc --metrics-interface=<HOST>
```

# Example

```bash
teku vc --metrics-interface=192.168.10.101
```

# Environment variable

```bash
TEKU_METRICS_INTERFACE=192.168.10.101
```

# Configuration file

```bash
metrics-interface: "192.168.10.101"
```

<!--/tabs-->

Host on which Prometheus accesses Teku metrics. The default is `127.0.0.1`.

## `metrics-port`

<!--tabs-->

# Syntax

```bash
teku vc --metrics-port=<PORT>
```

# Example

```bash
teku vc --metrics-port=6174
```

# Environment variable

```bash
TEKU_METRICS_PORT=6174
```

# Configuration file

```bash
metrics-port: 6174
```

<!--/tabs-->

Specifies the port (TCP) on which [Prometheus](https://prometheus.io/) accesses Teku metrics. The default is `8008`.

## `network`

<!--tabs-->

# Syntax

```bash
teku vc --network=<NETWORK>
```

# Example

```bash
teku vc --network=auto
```

# Environment variable

```bash
TEKU_NETWORK=auto
```

# Configuration file

```bash
network: "auto"
```

<!--/tabs-->

Predefined network configuration. The default is `mainnet`.

Use `auto` to fetch the network configuration from the beacon node endpoint directly.

## `validator-keys`

<!--tabs-->

# Syntax

```bash
teku vc --validator-keys=<KEY_DIR>:<PASS_DIR> | <KEY_FILE>:<PASS_FILE>[,<KEY_DIR>:<PASS_DIR> | <KEY_FILE>:<PASS_FILE>...]...
```

# Example for directory

```bash
teku vc --validator-keys=/home/validator/keys:home/validator/passwords
```

# Example for file

```bash
teku vc --validator-keys=/home/validator/keys/validator_217179e.json:/home/validator/passwords/validator_217179e.txt
```

# Environment variable

```bash
TEKU_VALIDATOR_KEYS=/home/validator/keys:home/validator/passwords
```

# Configuration file

```bash
validator-keys: "/home/validator/keys:home/validator/passwords"
```

<!--/tabs-->

Directory or file to load the encrypted keystore file(s) and associated password file(s) from. Keystore files must use the `.json` file extension, and password files must use the `.txt` file extension.

When specifying directories, Teku expects to find identically named keystore and password files. For example `validator_217179e.json` and `validator_217179e.txt`.

When specifying file names, Teku expects that the files exist.

:::note

The path separator is operating system dependent, and should be `;` in Windows rather than `:`.

:::

## `validators-early-attestations-enabled`

<!--tabs-->

# Syntax

```bash
teku vc --validators-early-attestations-enabled[=<BOOLEAN>]
```

# Example

```bash
teku vc --validators-early-attestations-enabled=false
```

# Environment variable

```bash
TEKU_VALIDATORS_EARLY_ATTESTATIONS_ENABLED=false
```

# Configuration file

```bash
validators-early-attestations-enabled: false
```

<!--/tabs-->

Specify whether to use Teku's built-in early attestation production, which creates an attestation once a block is received. The default is `true`.

Set this option to `false` if running a validator client connected to a load balanced beacon node (including most hosted beacon nodes such as [Infura]), and validator effectiveness is poor.

:::note

Delaying attestation production increases the chances of generating a correct attestation when using a load balanced beacon node, but it increases the risk of inclusion delays.

:::

## `validators-external-signer-keystore`

<!--tabs-->

# Syntax

```bash
teku vc --validators-external-signer-keystore=<FILE>
```

# Example

```bash
teku vc --validators-external-signer-keystore=teku_client_keystore.p12
```

# Environment variable

```bash
TEKU_VALIDATORS_EXTERNAL_KEYSTORE=teku_client_keystore.p12
```

# Configuration file

```bash
validators-external-signer-keystore: "teku_client_keystore.p12"
```

<!--/tabs-->

The keystore that Teku presents to the external signer for TLS authentication. Teku can use PKCS12 or JKS keystore types.

Use the PKCS12 keystore type if connecting to Web3Signer.

## `validators-external-signer-keystore-password-file`

<!--tabs-->

# Syntax

```bash
teku vc --validators-external-signer-keystore-password-file=<FILE>
```

# Example

```bash
teku vc --validators-external-signer-keystore-password-file=keystore_pass.txt
```

# Environment variable

```bash
TEKU_VALIDATORS_EXTERNAL_KEYSTORE_PASSWORD_FILE=keystore_pass.txt
```

# Configuration file

```bash
validators-external-signer-keystore-password-file: "keystore_pass.txt"
```

<!--/tabs-->

Password file used to decrypt the keystore.

## `validators-external-signer-public-keys`

<!--tabs-->

# Syntax

```bash
teku vc --validators-external-signer-public-keys=<KEY>[,<KEY>...]
```

# Example

```bash
teku vc --validators-external-signer-public-keys=0xa99a...e44c,0xb89b...4a0b
```

# Environment variable

```bash
TEKU_VALIDATORS_EXTERNAL_SIGNER_PUBLIC_KEYS=0xa99a...e44c,0xb89b...4a0b
```

# Configuration file

```bash
validators-external-signer-public-keys: ["0xa99a...e44c","0xb89b...4a0b"]
```

<!--/tabs-->

List of validator public keys used by an external signer (for example, [Web3Signer]).

## `validators-external-signer-slashing-protection-enabled`

<!--tabs-->

# Syntax

```bash
teku vc --validators-external-signer-slashing-protection-enabled[=<BOOLEAN>]
```

# Example

```bash
teku vc --validators-external-signer-slashing-protection-enabled=false
```

# Environment variable

```bash
TEKU_VALIDATORS_EXTERNAL_SIGNER_SLASHING_PROTECTION_ENABLED=false
```

# Configuration file

```bash
validators-external-signer-slashing-protection-enabled: false
```

<!--/tabs-->

Specify whether to use Teku's built-in [slashing protection] when using an external signer such as [Web3Signer]. The default is `true`.

Set this option to `false` if using the slashing protection implemented by an external signer.

:::warning

Ensure the external signer has slashing protection enabled before disabling Teku slashing protection, otherwise a validator may get slashed.

:::

Built-in slashing protection can only be disabled for validators using external signers. Validators using Teku to sign blocks and attestations always uses its built-in slashing protection.

## `validators-external-signer-timeout`

<!--tabs-->

# Syntax

```bash
teku vc --validators-external-signer-timeout=<INTEGER>
```

# Example

```bash
teku vc --validators-external-signer-timeout=2000
```

# Environment variable

```bash
TEKU_VALIDATORS_EXTERNAL_SIGNER_TIMEOUT=2000
```

# Configuration file

```bash
validators-external-signer-timeout: 2000
```

<!--/tabs-->

Timeout in milliseconds for requests to the external signer. The default is 5000.

## `validators-external-signer-truststore`

<!--tabs-->

# Syntax

```bash
teku vc --validators-external-signer-truststore=<FILE>
```

# Example

```bash
teku vc --validators-external-signer-truststore=websigner_truststore.p12
```

# Environment variable

```bash
TEKU_VALIDATORS_EXTERNAL_TRUSTSTORE=websigner_truststore.p12
```

# Configuration file

```bash
validators-external-signer-truststore: "websigner_truststore.p12"
```

<!--/tabs-->

PKCS12 or JKS keystore used to trust external signer's self-signed certificate or CA certificate which signs the external signer's certificate.

## `validators-external-signer-truststore-password-file`

<!--tabs-->

# Syntax

```bash
teku vc --validators-external-signer-truststore-password-file=<FILE>
```

# Example

```bash
teku vc --validators-external-signer-truststore-password-file=truststore_pass.txt
```

# Environment variable

```bash
TEKU_VALIDATORS_EXTERNAL_TRUSTSTORE_PASSWORD_FILE=truststore_pass.txt
```

# Configuration file

```bash
validators-external-signer-truststore-password-file: "truststore_pass.txt"
```

<!--/tabs-->

Password file used to decrypt the [keystore](#validators-external-signer-truststore).

## `validators-external-signer-url`

<!--tabs-->

# Syntax

```bash
teku vc --validators-external-signer-url=<URL>
```

# Example

```bash
teku vc --validators-external-signer-url=http://localhost:9000
```

# Environment variable

```bash
TEKU_VALIDATORS_EXTERNAL_SIGNER_URL=http://localhost:9000
```

# Configuration file

```bash
validators-external-signer-url: "http://localhost:9000"
```

<!--/tabs-->

URL on which the external signer (for example, Web3Signer) is running.

## `validators-graffiti`

<!--tabs-->

# Syntax

```bash
teku vc --validators-graffiti=<STRING>
```

# Example

```bash
teku vc --validators-graffiti="Teku validator"
```

# Environment variable

```bash
TEKU_VALIDATORS_GRAFFITI="Teku validator"
```

# Configuration file

```bash
validators-graffiti: "Teku validator"
```

<!--/tabs-->

Graffiti to add when creating a block. Gets converted to bytes and padded to Bytes32.

The same graffiti is used for all validators started with this beacon node.

## `validators-graffiti-file`

<!--tabs-->

# Syntax

```bash
teku vc --validators-graffiti-file=<FILE>
```

# Example

```bash
teku vc --validators-graffiti-file=/Users/me/mynode/graffiti.txt
```

# Environment variable

```bash
TEKU_VALIDATORS_GRAFFITI_FILE=/Users/me/mynode/graffiti.txt
```

# Configuration file

```bash
validators-graffiti-file: "/Users/me/mynode/graffiti.txt"
```

<!--/tabs-->

File containing the validator graffiti to add when creating a block. The file content is converted to `bytes` and padded to `Bytes32`. The same graffiti is used for all validators started with this beacon node.

You can overwrite the file while Teku is running to update the graffiti.

This option takes precedence over [`--validators-graffiti`](#validators-graffiti).

## `validators-keystore-locking-enabled`

<!--tabs-->

# Syntax

```bash
teku vc --validators-keystore-locking-enabled=<BOOLEAN>
```

# Example

```bash
teku vc --validators-keystore-locking-enabled=true
```

# Environment variable

```bash
TEKU_VALIDATORS_KEYSTORE_LOCKING_ENABLED=true
```

# Configuration file

```bash
validators-keystore-locking-enabled: true
```

<!--/tabs-->

Locks the keystore files listed in [`--validator-keys`](#validator-keys). The default is `true`.

Attempts to lock all keystores in a directory if a directory is specified in [`--validator-keys`](#validator-keys).

## `validators-performance-tracking-mode`

<!--tabs-->

# Syntax

```bash
teku vc --validators-performance-tracking-mode=<STRING>
```

# Example

```bash
teku vc --validators-performance-tracking-mode=LOGGING
```

# Environment variable

```bash
TEKU_VALIDATORS_PERFORMANCE_TRACKING_MODE=LOGGING
```

# Configuration file

```bash
validators-performance-tracking-mode: LOGGING
```

<!--/tabs-->

Set the validator performance tracking strategy. Valid options are `LOGGING`, `METRICS`, `ALL`, and `NONE`. The default is `ALL`.

When `LOGGING` is enabled, attestation and block performance is reported as log messages. When `METRICS` is enabled, attestation and block performance is reported using [metrics] in the [`VALIDATOR_PERFORMANCE`](#metrics-categories) metrics category.

<!-- links -->

[environment variables or a configuration file]: ../index.md#specifying-options
[Web3Signer]: https://docs.web3signer.consensys.net/en/latest/
[slashing protection]: ../../../concepts/slashing-protection.md
[recent finalized checkpoint state from which to sync]: ../../../get-started/checkpoint-start.md
[metrics]: ../../../how-to/monitor/use-metrics.md
