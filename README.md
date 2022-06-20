# BLST-CherryBomb


<img src="https://user-images.githubusercontent.com/58718316/174298977-563a96a2-4e4f-470a-88f3-cd71dcb44ade.png">

# 🐾 Get Started
## Installation
#### Using cURL
##### Linux/MacOS:
```
curl https://cherrybomb.blstsecurity.com/install	| /bin/bash
```
The script requires sudo permissions to move the cherrybomb bin into <b>/usr/local/bin/</b>.</br>
(If you want to view the shell script(or even help to improving it - [/scripts/install.sh](/scripts/install.sh))
#### Direct download
You can also download the binary file directly from [our website](https://www.blstsecurity.com/cherrybomb).
<br />
This is a binary file and you DO NOT have to install Rust.
If you use this method you should run this command:
```
mkdir ~/.cherrybomb
```
To create a .cherrybomb dir in the home directory.

## Usage
After installing the CLI, verify it's working by running
```
cherrybomb --version
```

### OpenAPI specification scan
```
cherrybomb oas --file <PATH> --config <PATH> --verbosity <0/1/2> --format <cli/txt/json> --output <PATH>
```
#### Output example for verbosity level 1:
![checks_table](/images/checks_table.png)
#### Output example for verbosity level 0:
![alerts_table](/images/checks_table.png)

### Generate Parameter Table
```
cherrybomb param-table --file <PATH> --name <SINGLE PARAM NAME(OPTIONAL)>
```
#### Table output example:
![param_table](/images/param_table.png)

### Generate Endpoint Table
```
cherrybomb ep-table --file <PATH> --name <SINGLE PARAM NAME(OPTIONAL)>
```
#### Table output example:
![ep_table](/images/ep_table.png)

### Configuration options:
You can configure the OAS scan using the config.json file in your .cherrybomb director that we create by default in your home path(after one scan at least or downloading using the install script).
#### Go through only part of the checks
Full scan:
```
{
  "scan_type":"Full",
	...
}
```
Only run the server url and the default response checks: 
```
{
  "scan_type":["SERRVER URL","DEFAULT RESPONSE"],
	...
}
```
#### Fail or not when the highest alert level is info
```
{
  "fail_on_info":true,
	...
}
```
### More features
First, we have a mapping module that relies on HTTP logs and builds a map of the API.
<br />
Start mapping your logs by running
```
cherrybomb map --file <LOGS_FILE_PATH> --output <OUTPUT_FILE_NAME> --hint <OAS FILE NAME>
```

If you don't have an HTTP log file, but you have Burp suite logs, you are in luck, go to the scripts folder, there is a convertor script over there.
<br />
If there are any other formats you need conversion scripts to, message us on the [discord server](https://discord.gg/WdHhv4DqwU).
<br />
For futher insights, you can view your map visually in our web based visualizer: [https://www.blstsecurity.com/cherrybomb/Visualizer](https://www.blstsecurity.com/cherrybomb/Visualizer).

In the future, if you want to load new logs to an existing map file, run
```
cherrybomb load --file <LOGS_FILE_PATH> --map <MAPPED_FILE_PATH>
```
