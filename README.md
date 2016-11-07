# CAN to CSV Parser

## Usage

To parse a CAN dump (in `candump -l` format):

```
./canparser -s my_schema.yaml candump-foo.log
```
Individual .csv files will be created for each message type in the dump. These
will appear in a 'candump-foo' folder where canparser was run.

You will also need a schema file that describes the messsages in the can dump.
To load a schema you can either name it `schema.yaml` and put it in the same
folder as the script or use the `-s` flag to pass the path to the schema file.
The format of the schema file is described below.

## Message Definition Schema

### Example

```
- cob_id: '0x101'
  name: environment_status
  order: little-endian
  contents:
  - {name: Voltage, scale: 0.001, type: uint16}
  - {name: Current, scale: 0.1, type: int16}
  - {name: Pressure, type: uint8}
- cob_id: '0x201'
  name: encoder_input
  order: big-endian
  contents:
  - {name: 'Left Encoder', scale: 0.125, type: int32}
  - {name: 'Right Encoder', scale: 0.125, type: int32}
```
