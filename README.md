# ADempiere S3 Connector

A AWS3 Connector to use as File Storage

## Requirements
- [JDK 11 or later](https://adoptium.net/)
- [Gradle 8.0.1 or later](https://gradle.org/install/)

## Model Deploy class
The main deploy is `org.spin.eca62.setup.Deploy`, used to connect this plibrary with a minio instance like is generated [here](https://github.com/adempiere/s3_gateway_rs/blob/main/docker-compose/docker-compose-develop.yml)

## ADempiere Patches
Currently the old implementation for ADempiere not work with the new definition, here a example of new definition `org.spin.util.AttachmentUtil`

## S3 File Structure

The files are store depending of follow parameters:

- Client ID
- Container Type
- Container ID
- Table
- Record ID
- User ID
- Resource Name

### Some Examples

#### Images

- Client ID: `8d4e103d-6add-474f-948d-3d9bcbe7b541`
- Container Type: `resource`
- Container ID: `image`
- Table: No apply
- Record ID: No apply
- User ID: No apply
- Resource Name: `2024-04-01_10-16.png`

The route to store this resource is `<bucket name>/8d4e103d-6add-474f-948d-3d9bcbe7b541/client/resource/image/2024-04-01_10-16.png`

#### Archives

- Client ID: `8d4e103d-6add-474f-948d-3d9bcbe7b541`
- Container Type: `resource`
- Container ID: `archive`
- Table: `AD_AppRegistration`
- Record ID: `1000000`
- User ID: No apply
- Resource Name: `GardenWorld---Application-Registration.pdf`

The route to store this resource is `<bucket name>/8d4e103d-6add-474f-948d-3d9bcbe7b541/client/resource/archive/ad_appregistration/1000000/gardenworld---application-registration.pdf`

#### Attachments

##### File 1
  - Client ID: `8d4e103d-6add-474f-948d-3d9bcbe7b541`
  - Container Type: `attachment`
  - Container ID: No Apply
  - Table: `AD_AppRegistration`
  - Record ID: `1000000`
  - User ID: No apply
  - Resource Name: `-2024-02-10-2119.png`

The route to store this resource is `<bucket name>/8d4e103d-6add-474f-948d-3d9bcbe7b541/client/attachment/ad_appregistration/1000000/-2024-02-10-2119.png`

##### File 2
  - Client ID: `8d4e103d-6add-474f-948d-3d9bcbe7b541`
  - Container Type: `attachment`
  - Container ID: No Apply
  - Table: `AD_AppRegistration`
  - Record ID: `1000000`
  - User ID: No apply
  - Resource Name: `09920_eca62_add_app_support.xml`

The route to store this resource is `<bucket name>/8d4e103d-6add-474f-948d-3d9bcbe7b541/client/attachment/ad_appregistration/1000000/09920_eca62_add_app_support.xml`

##### File 3
  - Client ID: `8d4e103d-6add-474f-948d-3d9bcbe7b541`
  - Container Type: `attachment`
  - Container ID: No Apply
  - Table: `AD_AppRegistration`
  - Record ID: `1000000`
  - User ID: No apply
  - Resource Name: `a.xml`

The route to store this resource is `<bucket name>/8d4e103d-6add-474f-948d-3d9bcbe7b541/client/attachment/ad_appregistration/1000000/a.xml`

## Binary Project

You can get all binaries from github [here](https://central.sonatype.com/artifact/io.github.adempiere/adempiere-s3-connector/1.0.0).

All contruction is from github actions


## Some XML's:

All dictionary changes are writing from XML and all XML's hare `xml/migration`


## How to add this library?

Is very easy.

- Gradle

```Java
implementation 'io.github.adempiere:adempiere-s3-connector:1.0.0'
```

- SBT

```
libraryDependencies += "io.github.adempiere" % "adempiere-s3-connector" % "1.0.0"
```

- Apache Maven

```
<dependency>
    <groupId>io.github.adempiere</groupId>
    <artifactId>adempiere-s3-connector</artifactId>
    <version>1.0.0</version>
</dependency>
```