# DlMirrorSync

[![.NET](https://github.com/dkackman/DlMirrorSync/actions/workflows/dotnet.yml/badge.svg)](https://github.com/dkackman/DlMirrorSync/actions/workflows/dotnet.yml)

This is a utility service that will synchronize the list of chia data layer singletons from [datalayer.storage](https://api.datalayer.storage/mirrors/v1/list_all) to the local chia node. By running this tool, the local node will subscribe to and mirror all of the `datalayer.storage` singletons. This includes a transaction fee for each and devoting 0.0003 XCH per mirror, so be sure you are ready to do this.

Can either be run from code, from built binaries in [the latest release](https://github.com/dkackman/DlMirrorSync/releases/), or as a windows service.

- The `singlefile` versions require [.NET 8](https://dotnet.microsoft.com/en-us/download/dotnet/8.0).
- The `standalone` versions have .net embedded so don't need it installed separately.
- The MSI installs the windows service that will synchronize the singletons once per day. (this installs as autostart and will run immediately)

## Build

- Ensure you have the .NET 8 SDK installed
- Run `./publish.ps1` which will build single file and standalone binaries for windows, linux, and os-x
- Outputs will be placed in the `publish` folder

To build the installer you need wix installed: `dotnet tool install -g dotnet-wix` (Windows only).

To manually install as a windows service run `./install.ps1` from an elevated terminal.

## Run

### Command Line

If you are running the single file or standalone versions you can run the following command to sync the singletons:

```bash
./DlMirrorSync ["optional path to chia config"]
```

### Install As a Service

First build the binaries by running `publish.ps1` [[powershell for linux](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-linux)]
which will build single file and standalone binaries for windows, linux, and os-x. Outputs will be placed in the `publish` folder. Then run the following commands to install the service:

#### Windows

To manually install as a windows service run `./install.ps1` from an elevated terminal.

#### Linux

_work in progress_

To install as a `systemd` service run `sudo bash install.sh`

#### OS-X

TBD
