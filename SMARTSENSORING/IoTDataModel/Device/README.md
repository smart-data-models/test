# Device

## Description

An apparatus (hardware + software + firmware) intended to accomplish a
particular task (sensing the environment, actuating, etc.). A Device is a
tangible object which contains some logic and is producer and/or consumer of
data. A Device is always assumed to be capable of communicating electronically
via a network.

This data model has been partially developed in cooperation with mobile
operators and the [GSMA](https://www.gsma.com/iot/iot-big-data/).

This data model reuses concepts coming from the
[SAREF Ontology](http://www.etsi.org/deliver/etsi_ts/103200_103299/103264/01.01.01_60/ts_103264v010101p.pdf)
part of [ETSI](http://www.etsi.org) standards.

## Data Model

The data model is defined as shown below:

-   `id` : Unique identifier.

-   `type` : Entity type. It must be equal to `Device`.

-   `source` : A sequence of characters giving the source of the entity data.

    -   Attribute type: Property. [Text](https://schema.org/Text) or [URL](https://schema.org/URL)
    -   Optional

-   `dataProvider` : Specifies the URL to information about the provider of this
    information

    -   Attribute type: Property. [URL](https://schema.org/URL)
    -   Optional

-   `category` : See attribute `category` from
    [DeviceModel](../../DeviceModel/doc/spec.md). Optional but recommended to
    optimize queries.

-   `controlledProperty` : See attribute `controlledProperty` from
    [DeviceModel](../../DeviceModel/doc/spec.md). Optional but recommended to
    optimize queries.

-   `controlledAsset` : The asset(s) (building, object, etc.) controlled by the
    device.

    -   Attribute type: Property. List of [Text](https://schema.org) or Reference(s) to
        another entity.
    -   Optional

-   `mnc` : This property identifies the Mobile Network Code (MNC) of the
    network the device is attached to. The MNC is used in combination with a
    Mobile Country Code (MCC) (also known as a "MCC / MNC tuple") to uniquely
    identify a mobile phone operator/carrier using the GSM, CDMA, iDEN, TETRA
    and 3G / 4G public land mobile networks and some satellite mobile networks.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   Optional

-   `mcc` : Mobile Country Code - This property identifies univoquely the
    country of the mobile network the device is attached to.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   Optional

-   `macAddress` : The MAC address of the device.

    -   Attribute type: Property. List of [Text](https://schema.org/Text)
    -   Optional

-   `ipAddress` : The IP address of the device. It can be a comma separated list
    of values if the device has more than one IP address.

    -   Attribute type: Property. List of [Text](https://schema.org/Text)
    -   Optional

-   `supportedProtocol` : See attribute `supportedProtocol` from
    [DeviceModel](../../DeviceModel/doc/spec.md). Needed if due to a software
    update new protocols are supported. Otherwise it is better to convey it at
    `DeviceModel` level.

-   `configuration` : Device's technical configuration. This attribute is
    intended to be a dictionary of properties which capture parameters which
    have to do with the configuration of a device (timeouts, reporting periods,
    etc.) and which are not currently covered by the standard attributes defined
    by this model.

    -   Attribute type: Property. [StructuredValue](https://schema.org/StructuredValue)
    -   Attribute metadata:
        -   `dateModified` : Last update timestamp of this attribute.
            -   Metadata type: [DateTime](https://schema.org/DateTime)
            -   Read-Only. Automatically generated.
    -   Optional

-   `location` : Location of this device represented by a GeoJSON geometry of
    type point.

    -   Attribute type: GeoProperty. `geo:json`.
    -   Normative References:
        [https://tools.ietf.org/html/rfc7946](https://tools.ietf.org/html/rfc7946)
    -   Optional.

-   `name` : A mnemonic name given to the device.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   Normative References:
        `https://uri.etsi.org/ngsi-ld/name` equivalent to [name](https://schema.org/name)
    -   Optional

-   `description` : Device's description.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   Normative References:
        `https://uri.etsi.org/ngsi-ld/description` equivalent to [description](https://schema.org/description)
    -   Optional

-   `dateInstalled` : A timestamp which denotes when the device was installed
    (if it requires installation).

    -   Attribute type: Property. [DateTime](https://schema.org/DateTime)
    -   Optional

-   `dateFirstUsed` : A timestamp which denotes when the device was first used.

    -   Attribute type: Property. [DateTime](https://schema.org/DateTime)
    -   Optional

-   `dateManufactured` : A timestamp which denotes when the device was
    manufactured.

    -   Attribute type: Property. [DateTime](https://schema.org/DateTime)
    -   Optional

-   `hardwareVersion` : The hardware version of this device.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   Optional

-   `softwareVersion` : The software version of this device.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   Optional

-   `firmwareVersion` : The firmware version of this device.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   Optional

-   `osVersion` : The version of the host operating system device.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   Optional

-   `dateLastCalibration` : A timestamp which denotes when the last calibration
    of the device happened.

    -   Attribute type: Property. [DateTime](https://schema.org/DateTime)
    -   Optional

-   `serialNumber` : The serial number assigned by the manufacturer.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   Normative References:
        [https://schema.org/serialNumber](https://schema.org/serialNumber)
    -   Optional

-   `provider` : The provider of the device.

    -   Attribute Type: Property. [Provider](http://schema.org/provider)
    -   Normative References:
        [https://schema.org/provider](https://schema.org/provider)
    -   Optional

-   `refDeviceModel` : The device's model.

    -   Attribute type: Property. Reference to an entity of type
        [DeviceModel](../../DeviceModel/doc/spec.md).
    -   Optional

-   `batteryLevel` : Device's battery level. It must be equal to `1.0` when
    battery is full. `0.0` when battery ìs empty. `-1` when transiently cannot
    be determined.

    -   Type: [Number](https://schema.org/Number)
    -   Allowed values: Interval \[0,1\] or -1
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened. This value can also appear as a FIWARE
            [TimeInstant](https://github.com/telefonicaid/iotagent-node-lib#TimeInstant)
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional

-   `rssi` : Received signal strength indicator for a wireless enabled device.
    It must be equal to `1.0` when the signal strength is maximum. `0.0` when
    signal is missing. `-1.0` when it cannot be determined.

    -   Type: [Number](https://schema.org/Number)
    -   Allowed values: Interval \[0,1\] and -1
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened. This value can also appear as a FIWARE
            [TimeInstant](https://github.com/telefonicaid/iotagent-node-lib#TimeInstant)
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional

-   `deviceState` : State of this device from an operational point of view. Its
    value can be vendor dependent.

    -   Type: [Text](https://schema.org/Text)
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened. This value can also appear as a FIWARE
            [TimeInstant](https://github.com/telefonicaid/iotagent-node-lib#TimeInstant)
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional

-   `dateLastValueReported` : A timestamp which denotes the last time when the
    device successfully reported data to the cloud.

    -   Attribute type: Property. [DateTime](https://schema.org/DateTime)
    -   Optional

-   `value` : A observed or reported value. For actuator devices, it is an
    attribute that allows a controlling application to change the actuation
    setting. For instance, a switch device which is currently _on_ can report a
    value `"on"`of type `Text`. Obviously, in order to toggle the referred
    switch, this attribute value will have to be changed to `"off"`.

    -   Attribute type: Property. Any type, depending on the device. Usually
        [Text](https://schema.org/Text) or
        [QuantitativeValue](https://schema.org/QuantitativeValue).
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened. This value can also appear as a FIWARE
            [TimeInstant](https://github.com/telefonicaid/iotagent-node-lib#TimeInstant)
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional

-   `dateModified` : Last update timestamp of this entity.

    -   Attribute type: Property. [DateTime](https://schema.org/DateTime)
    -   Read-Only. Automatically generated.

-   `dateCreated` : Entity's creation timestamp.

    -   Attribute type: Property. [DateTime](https://schema.org/DateTime)
    -   Read-Only. Automatically generated.

-   `owner` : The owners of a Device.
    -   Attribute type: Property. List of references to [Person](http://schema.org/Person)
        or [Organization](https://schema.org/Organization) or List of URIs.
    -   Optional
    
 ## From DeviceModel
 -   `function` : The functionality necessary to accomplish the task for which a
    Device is designed. A device can be designed to perform more than one
    function. Defined by [SAREF](https://w3id.org/saref#Function).

    -   Attribute type: Property. List of [Text](https://schema.org/Text)
    -   Allowed values: (`levelControl`, `sensing`, `onOff`, `openClose`,
        `metering`, `eventNotification`), from SAREF.
    -   Optional

-   `supportedProtocol` : Supported protocol(s) or networks.

    -   Attribute type: Property. List of [Text](https://schema.org/Text).
    -   Allowed values: (`ul20`, `mqtt`, `lwm2m`, `http`, `websocket`, `onem2m`,
        `sigfox`, `lora`, `nb-iot`, `ec-gsm-iot`, `lte-m`, `cat-m`, `3g`,
        `grps`) or any other value meaningful for an application.
    -   Optional

-   `supportedUnits` : Units of measurement supported by the device.

    -   Attribute type: Property. List of [Text](https://schema.org/Text).
    -   Allowed values: The unit code (text) of measurement given using the
        [UN/CEFACT Common Code](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes)
        (max. 3 characters).
    -   Optional

-   `energyLimitationClass` : Device's class of energy limitation as per
    RFC 7228.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   Normative References:
        [RFC7228](https://tools.ietf.org/html/rfc7228#page-11)
    -   Allowed values: (`E0`, `E1`, `E2`, `E9`)
    -   Optional

-   `brandName` : Device's brand name.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   See also: [https://schema.org/brand](https://schema.org/brand)
    -   Mandatory

-   `modelName` : Device's model name.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   See also: [https://schema.org/model](https://schema.org/model)
    -   Mandatory

-   `manufacturerName` : Device's manufacturer name.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   See also: [https://schema.org/model](https://schema.org/model)
    -   Mandatory

-   `name` : Name given to this device model.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   Normative References:
        `https://uri.etsi.org/ngsi-ld/name` equivalent to [name](https://schema.org/name)
    -   Mandatory

-   `description` : Device's description

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   Normative References:
        `https://uri.etsi.org/ngsi-ld/description` equivalent to [description](https://schema.org/description)
    -   Optional

-   `documentation` : A link to device's documentation.

    -   Attribute type: Property. [URL](https://schema.org/URL)
    -   Optional

-   `image` : A link to an image depicting the concerned device.

    -   Normative References:
        [https://schema.org/image](https://schema.org/image)
    -   Optional

 

**Note**: JSON Schemas are intended to capture the data type and associated
constraints of the different Attributes, regardless their final representation
format in NGSI(v2, LD).

## Examples

### Normalized Example

Normalized NGSI response

```json
{
    "id": "device-9845A",
    "type": "Device",
    "category": {
        "value": ["sensor"]
    },
    "batteryLevel": {
        "value": 0.75
    },
    "dateFirstUsed": {
        "type": "DateTime",
        "value": "2014-09-11T11:00:00Z"
    },
    "controlledAsset": {
        "value": ["wastecontainer-Osuna-100"]
    },
    "serialNumber": {
        "value": "9845A"
    },
    "mcc": {
        "value": "214"
    },
    "value": {
        "value": "l%3D0.22%3Bt%3D21.2"
    },
    "refDeviceModel": {
        "type": "Relationship",
        "value": "myDevice-wastecontainer-sensor-345"
    },
    "rssi": {
        "value": 0.86
    },
    "controlledProperty": {
        "value": ["fillingLevel", "temperature"]
    },
    "owner": {
        "value": ["http://person.org/leon"]
    },
    "mnc": {
        "value": "07"
    },
    "ipAddress": {
        "value": ["192.14.56.78"]
    },
    "deviceState": {
        "value": "ok"
    }
}
```

### key-value pairs Example

Sample uses simplified representation for data consumers `?options=keyValues`

```json
    {
        "id": "device-9845A",
        "type": "Device",
        "category": ["sensor"],
        "controlledProperty": ["fillingLevel""temperature"],
        "controlledAsset":["wastecontainer-Osuna-100"],
        "ipAddress": ["192.14.56.78"],
        "mcc": "214",
        "mnc": "07",
        "batteryLevel": 0.75,
        "serialNumber": "9845A",
        "refDeviceModel":"myDevice-wastecontainer-sensor-345",
        "rssi": 0.86,
        "value": "l=0.22;t=21.2",
        "deviceState": "ok",
        "dateFirstUsed": "2014-09-11T11:00:00Z",
        "owner": ["http://person.org/leon"]
    }
```

### LD Example

Sample uses the NGSI-LD representation

```json
{
    "id": "urn:ngsi-ld:Device:device-9845A",
    "type": "Device",
    "category": {
        "type": "Property",
        "value": ["sensor"]
    },
    "batteryLevel": {
        "type": "Property",
        "value": 0.75
    },
    "dateFirstUsed": {
        "type": "Property",
        "value": {
            "@type": "DateTime",
            "@value": "2014-09-11T11:00:00Z"
        }
    },
    "controlledAsset": {
        "type": "Relationship",
        "object": ["urn:ngsi-ld::wastecontainer-Osuna-100"]
    },
    "serialNumber": {
        "type": "Property",
        "value": "9845A"
    },
    "mcc": {
        "type": "Property",
        "value": "214"
    },
    "value": {
        "type": "Property",
        "value": "l%3D0.22%3Bt%3D21.2"
    },
    "refDeviceModel": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:DeviceModel:myDevice-wastecontainer-sensor-345"
    },
    "rssi": {
        "type": "Property",
        "value": 0.86
    },
    "controlledProperty": {
        "type": "Property",
        "value": ["fillingLevel", "temperature"]
    },
    "owner": {
        "type": "Property",
        "value": ["http://person.org/leon"]
    },
    "mnc": {
        "type": "Property",
        "value": "07"
    },
    "ipAddress": {
        "type": "Property",
        "value": ["192.14.56.78"]
    },
    "deviceState": {
        "type": "Property",
        "value": "ok"
    },
    "@context": [
        "https://schema.lab.fiware.org/ld/context",
        "https://uri.etsi.org/ngsi-ld/v1/ngsi-ld-core-notes_context.jsonld"
    ]
}
```

**N.B.:** This example to work in Orion Context Broker implementation of NGSI
v2, requires that value attribute is URL Encoded. As documented
[here](https://fiware-orion.readthedocs.io/en/master/user/forbidden_characters/index.html)
`=` is a forbidden character.

## Test it with a real service

T.B.D.

## Issues

-   Is `function` really needed?
-   Do we need a `state` attribute as it happens in SAREF?
-   Check consistency with oneM2M and SAREF ontologies.
