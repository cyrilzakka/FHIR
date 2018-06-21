![alt text](https://github.com/cyrilzakka/FHIR/blob/master/proto_banner.png)

## About
Nowadays, healthcare records are becoming increasingly digitized. As patients move around the healthcare ecosystem, their electronic health records must be made available, discoverable, and understandable. Unfortunately with no common data representation or established standards across vendors, making sense of this data for large scale studies and analysis rapidly becomes a difficult feat.

This repository contains an implementation of a [protocol buffer](https://developers.google.com/protocol-buffers/) for the [Fast Healthcare Interoperability Resources (FHIR)](https://www.hl7.org/fhir/). The FHIR is a solid yet extensible data-model for health records, built on established web standards that seeks to standardize both individual records and bulk-data access, thereby simplifying automated clinical decision support and other machine-based processing.

#### Versioning

|  Format  | Version |
| -------- | --------|
| protobuf |  3.5.1  |
| FHIR     |  3.0.1  |

## Motivation
While HL7 does provide a general implementation of the FHIR architecture in `XML`, `JSON`, as well as links to third-party implementations in various languages, protocol buffers have the advantage of:

- **being backwards compatible**: FHIR is still in development and is likely to evolve the near future as its schemas are improved and optimized. Protocol buffers obviate the need for version checks through its use of numbered fields.
- **being platform independent**: Protocol buffers automatically generate classes for the most common languages making it easy to use the same architecture for different platforms. 
- **being faster and smaller in size**: Protocol buffers are 3 to 10 times smaller and 20 to 100 times faster than `XML` and `JSON` files making them an ideal medium for large data manipulation common to the healthcare industry.

## Requirements
In order to make use of the included `proto` files, you'll have to install the latest version of `protobuf` on your system. Here are some OS-specific options for installing the binary:

#### macOS
If you have `homebrew` installed on your system, run the following commands:

``` sh
brew install protobuf
brew upgrade protobuf
```

Alternatively, use the commands below (changing the version number as needed):

``` sh
PROTOC_ZIP=protoc-3.5.1-osx-x86_64.zip
curl -OL https://github.com/google/protobuf/releases/download/v3.5.1/$PROTOC_ZIP
sudo unzip -o $PROTOC_ZIP -d /usr/local bin/protoc
rm -f $PROTOC_ZIP
```

#### Linux
Type in the following command, (changing the version number as needed):

``` sh
PROTOC_ZIP=protoc-3.5.1-linux-x86_64.zip
curl -OL https://github.com/google/protobuf/releases/download/v3.5.1/$PROTOC_ZIP
sudo unzip -o $PROTOC_ZIP -d /usr/local bin/protoc
rm -f $PROTOC_ZIP
```

## Usage
In order to automatically generate classes from the `proto` files, run the compiler, specifying the source directory (where your application's source code lives – the current directory is used if you don't provide a value), the destination directory (where you want the generated code to go; often the same as $SRC_DIR), and the path to your `.proto`.
For example, to generate `python` classes, use the following:

``` sh
protoc -I=$SRC_DIR --python_out=$DST_DIR $SRC_DIR/$FILENAME.proto
```
For further instructions and details, please refer to the official [Protocol Buffer Documentation](https://developers.google.com/protocol-buffers/docs/tutorials).
