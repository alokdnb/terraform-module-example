# Terraform Module: AWS S3 Bucket

A reusable Terraform module for creating and managing AWS S3 buckets with security best practices.

## Features

- Create S3 buckets with customizable configuration
- Optional versioning support
- Server-side encryption enabled by default
- Public access blocking for enhanced security
- Support for custom tags
- Input validation for bucket naming

## Requirements

- Terraform >= 1.0
- AWS Provider >= 5.0

## Usage

```hcl
module "s3_bucket" {
  source = "github.com/alokdnb/terraform-module-example"

  bucket_name        = "my-company-data-bucket"
  enable_versioning  = true
  block_public_access = true

  common_tags = {
    Environment = "production"
    Project     = "data-pipeline"
    Terraform   = "true"
  }
}
```

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| `bucket_name` | Name of the S3 bucket | `string` | — | yes |
| `enable_versioning` | Enable versioning for the S3 bucket | `bool` | `true` | no |
| `block_public_access` | Block public access to the S3 bucket | `bool` | `true` | no |
| `common_tags` | Common tags to apply to all resources | `map(string)` | `{}` | no |

## Outputs

| Name | Description |
|------|-------------|
| `bucket_id` | The name of the S3 bucket |
| `bucket_arn` | The ARN of the S3 bucket |
| `bucket_region` | The AWS region of the S3 bucket |
| `bucket_domain_name` | The bucket regional domain name |

## Example Configuration

See `terraform.tfvars.example` for a sample configuration file.

## Security

This module implements the following security best practices:

- **Server-side encryption**: All objects are encrypted with AES256 by default
- **Public access blocking**: Prevents accidental public exposure of bucket contents
- **Versioning**: Optional object versioning for data protection and recovery
- **Input validation**: Bucket names are validated to follow AWS naming conventions

## License

Apache 2.0
