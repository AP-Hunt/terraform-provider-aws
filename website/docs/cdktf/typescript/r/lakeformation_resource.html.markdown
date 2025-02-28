---
subcategory: "Lake Formation"
layout: "aws"
page_title: "AWS: aws_lakeformation_resource"
description: |-
  Registers a Lake Formation resource as managed by the Data Catalog.
---


<!-- Please do not edit this file, it is generated. -->
# Resource: aws_lakeformation_resource

Registers a Lake Formation resource (e.g., S3 bucket) as managed by the Data Catalog. In other words, the S3 path is added to the data lake.

Choose a role that has read/write access to the chosen Amazon S3 path or use the service-linked role.
When you register the S3 path, the service-linked role and a new inline policy are created on your behalf.
Lake Formation adds the first path to the inline policy and attaches it to the service-linked role.
When you register subsequent paths, Lake Formation adds the path to the existing policy.

## Example Usage

```typescript
// DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
import { Construct } from "constructs";
import { Token, TerraformStack } from "cdktf";
/*
 * Provider bindings are generated by running `cdktf get`.
 * See https://cdk.tf/provider-generation for more details.
 */
import { DataAwsS3Bucket } from "./.gen/providers/aws/data-aws-s3-bucket";
import { LakeformationResource } from "./.gen/providers/aws/lakeformation-resource";
class MyConvertedCode extends TerraformStack {
  constructor(scope: Construct, name: string) {
    super(scope, name);
    const example = new DataAwsS3Bucket(this, "example", {
      bucket: "an-example-bucket",
    });
    const awsLakeformationResourceExample = new LakeformationResource(
      this,
      "example_1",
      {
        arn: Token.asString(example.arn),
      }
    );
    /*This allows the Terraform resource name to match the original name. You can remove the call if you don't need them to match.*/
    awsLakeformationResourceExample.overrideLogicalId("example");
  }
}

```

## Argument Reference

The following arguments are required:

* `arn` – (Required) Amazon Resource Name (ARN) of the resource.

The following arguments are optional:

* `roleArn` – (Optional) Role that has read/write access to the resource.
* `useServiceLinkedRole` - (Optional) Designates an AWS Identity and Access Management (IAM) service-linked role by registering this role with the Data Catalog.
* `hybridAccessEnabled` - (Optional) Flag to enable AWS LakeFormation hybrid access permission mode.

~> **NOTE:** AWS does not support registering an S3 location with an IAM role and subsequently updating the S3 location registration to a service-linked role.

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

* `lastModified` - Date and time the resource was last modified in [RFC 3339 format](https://tools.ietf.org/html/rfc3339#section-5.8).

<!-- cache-key: cdktf-0.20.8 input-5970095587554c3a95bb54c03adea93f4524b57f2455f2dcc9fb934b4090d05b -->