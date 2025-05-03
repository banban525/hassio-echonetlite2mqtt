# ECHONETLite2MQTT-alpha

This page explains the parameters specified in "Settings".

(日本語の説明は、ページ下部にあります。)

## How to set it up

__MQTT parameters__

| parameter           | description |
| ------------------  | ----------- |
| `MQTT_BROKER`       | The MQTT broker's URL. starts with "mqtt://" or "mqtts://".  |
| `MQTT_PORT`         | The MQTT broker port number. (Default: 1883) |
| `MQTT_CLIENT_ID`    | The MQTT client id. (Default: empty)|
| `MQTT_USERNAME`     | The MQTT user name. (Default: empty)|
| `MQTT_PASSWORD`     | The MQTT password. (Default: empty)|
| `MQTT_OPTION_FILE`  | the MQTT option file path. The schema is [MQTT.js](https://github.com/mqttjs/MQTT.js) ClientOptions. See the "file path" section for file locations. (Default: empty)  |
| `MQTT_CA_FILE`      | The MQTT CA file path. If this file exists, it will be loaded and set as an "ca" option. See the "file path" section for file locations. (Default: not load)  |
| `MQTT_CERT_FILE`    | The MQTT cert file path. If this file exists, it will be loaded and set as an "cert" option. See the "file path" section for file locations. (Default: not load)  |
| `MQTT_KEY_FILE`     | The MQTT key file path. If this file exists, it will be loaded and set as an "key" option. See the "file path" section for file locations. (Default: not load)  |
| `MQTT_BASE_TOPIC`   | MQTT topic prefix. (Default:"echonetlite2mqtt/elapi/v2/devices") |



__ECHONET Lite parameters__

| parameter                               | description |
| --------------------------------------  | ----------- |
| `ECHONET_TARGET_NETWORK`                | Specify the network for ECHONET Lite in the format "000.000.000.000/00". (Default: Auto) |
| `ECHONET_DEVICE_IP_LIST`                | Specify the device IPs separated by commas. (Default: none) |
| `ECHONET_COMMAND_TIMEOUT`               | Specify the timeout for ECHONET Lite commands. (Unit: ms) (Default: 3000) |
| `ECHONET_DISABLE_AUTO_DEVICE_DISCOVERY` | Disable automatic device discovery. (default: off) |
| `ECHONET_ALIAS_FILE`                    | The file path for alias option file. See the "file path" section for file locations. (Defalt: (empty)) |
| `ECHONET_LEGACY_MULTI_NIC_MODE`         | Revert to legacy communication mode. (Default: off) |
| `ECHONET_UNKNOWN_AS_ERROR`              | Specifies whether to  treat unknown classes and unknown properties as errors. (Default: off) |


## file path

The parameters that specify the file have different base paths depending on the parameter.
First, to place the file, install the `Samba share` addon and access `\\(Home Assistant IP)`.

Place the files for the following parameters in the `xxxxxxxx_echonetlite2mqtt` folder in `addon_configs` and specify the relative path from `xxxxxxxx_echonetlite2mqtt` folder.

* `MQTT_OPTION_FILE`
* `ECHONET_ALIAS_FILE`

Sample
```
\\(Home Assistant IP)\addon_configs\885b0f86_echonetlite2mqtt\
├─ aliasFile.json
└─ mqtt_option.json
```

For the file placement above, specify as follows.

* `MQTT_OPTION_FILE` : `mqtt_option.json`
* `ECHONET_ALIAS_FILE` : `aliasFile.json`


The files for the following parameters should be placed under the `ssl` folder and the relative path from the ‘ssl‘ folder should be specified.

* `MQTT_CA_FILE`
* `MQTT_CERT_FILE`
* `MQTT_KEY_FILE`


Sample
```
\\(Home Assistant IP)\ssl\
└─ mqtt
    ├─ ca.crt
    ├─ cert.pem
    └─ key.pem
```

For the file placement above, specify as follows.

* `MQTT_CA_FILE` : `ssl/mqtt/ca.crt`
* `MQTT_CERT_FILE` : `ssl/mqtt/cert.pem`
* `MQTT_KEY_FILE` : `ssl/mqtt/key.pem`


# 日本語の説明


__MQTT パラメーター__

| parameter           | description |
| ------------------  | ----------- |
| `MQTT_BROKER`       | MQTTブローカーのURLを指定します。"mqtt://" または "mqtts://"で始まる必要があります。  |
| `MQTT_PORT`         | MQTTブローカーのポートNoを指定します。(デフォルト: 1883) |
| `MQTT_CLIENT_ID`    | MQTTのクライアントIDを指定します。 (Default: (空)) |
| `MQTT_USERNAME`     | MQTTのユーザー名を指定します。 (Default: (空))|
| `MQTT_PASSWORD`     | MQTTのパスワードを指定します。 (Default: (空))|
| `MQTT_OPTION_FILE`  | MQTTのオプションファイルのパスを指定します。ファイルの形式は [MQTT.js](https://github.com/mqttjs/MQTT.js) の Client Options を参照してください。ファイルの配置場所については、"ファイルパス"セクションを参照してください。 (デフォルト: (空))  |
| `MQTT_CA_FILE`      | MQTTの CA ファイルのパスを指定します。パスが指定されればロードして、MQTTのオプションの"ca"に設定されます。ファイルの配置場所については、"ファイルパス"セクションを参照してください。 (デフォルト: ロードしない)  |
| `MQTT_CERT_FILE`    | MQTTの cert ファイルのパスを指定します。パスが指定されればロードして、MQTTのオプションの"cert"に設定されます。ファイルの配置場所については、"ファイルパス"セクションを参照してください。 (デフォルト: ロードしない)  |
| `MQTT_KEY_FILE`     | MQTTの key ファイルのパスを指定します。パスが指定されればロードして、MQTTのオプションの"key"に設定されます。ファイルの配置場所については、"ファイルパス"セクションを参照してください。  (デフォルト: ロードしない)  |
| `MQTT_BASE_TOPIC`   | MQTTトピックのプレフィックスを指定します。(デフォルト:"echonetlite2mqtt/elapi/v2/devices") |

__ECHONET Lite パラメーター__

| parameter                               | description |
| --------------------------------------  | ----------- |
| `ECHONET_TARGET_NETWORK`                | ECHONET Liteのネットワークを"000.000.000.000/00"の形で指定します。 (デフォルト: 自動) |
| `ECHONET_DEVICE_IP_LIST`                | デバイスのIPをカンマ区切りで指定します。(デフォルト:無し) |
| `ECHONET_COMMAND_TIMEOUT`               | ECHONET Liteコマンドの応答待ちの時間を指定します. (単位: ms) (デフォルト: 3000) |
| `ECHONET_DISABLE_AUTO_DEVICE_DISCOVERY` | デバイスの自動探索を無効にします。(デフォルト: off) |
| `ECHONET_ALIAS_FILE`                    | エイリアスオプションファイルを指定します。 (デフォルト: (空)) |
| `ECHONET_LEGACY_MULTI_NIC_MODE`         | 以前の通信モードに戻します。 (デフォルト: off) |
| `ECHONET_UNKNOWN_AS_ERROR`              | 不明なデバイスクラスや不明なプロパティをエラーとして扱います。 (デフォルト: off) |





## ファイルパス

ファイルを指定するパラメーターは、パラメーターによって基準となるパスが異なります。
まず、ファイルを配置するには、 `Samba share` addonをインストールし、 `\\(Home Assistant IP)`にアクセスします。

次のパラメーターのファイルは、 `addon_configs` の中の `xxxxxxxx_echonetlite2mqtt` フォルダ以下に配置し、`xxxxxxxx_echonetlite2mqtt` フォルダからの相対パスを指定してください。 

* `MQTT_OPTION_FILE`
* `ECHONET_ALIAS_FILE`

サンプル
```
\\(Home Assistant IP)\addon_configs\885b0f86_echonetlite2mqtt\
├─ aliasFile.json
└─ mqtt_option.json
```

上記のようなファイル配置の場合、以下のように指定します。

* `MQTT_OPTION_FILE` : `mqtt_option.json`
* `ECHONET_ALIAS_FILE` : `aliasFile.json`


次のパラメーターのファイルは、 `ssl` フォルダ以下に配置し、`ssl` からの相対パスを指定してください。

* `MQTT_CA_FILE`
* `MQTT_CERT_FILE`
* `MQTT_KEY_FILE`


サンプル
```
\\(Home Assistant IP)\ssl\
└─ mqtt
    ├─ ca.crt
    ├─ cert.pem
    └─ key.pem
```

上記のようなファイル配置の場合、以下のように指定します。

* `MQTT_CA_FILE` : `mqtt/ca.crt`
* `MQTT_CERT_FILE` : `mqtt/cert.pem`
* `MQTT_KEY_FILE` : `mqtt/key.pem`
