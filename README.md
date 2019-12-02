## AWS Certified Developer Associate
My personal notes.

## Author
Aditya Hajare [Linkedin Profile](https://in.linkedin.com/in/aditya-hajare).

## Current Status
WIP (Work In Progess).

## License
Open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT).

**************

## Table of Contents
- AWS Basics (IAM & EC2)
    - [AWS Regions](#aws-regions)
    - [IAM (Identity And Access Management)](#iam-basics)

---

#### AWS Regions
Each availability zone is a physical data center in the region, but separated from the other ones (so that they're isolated from disasters).

#### IAM (Identity And Access Management)
- Whole AWS security is there:
    * Users
    * Groups
    * Roles
- Root account should never be used (and shared) since it has the most control over entire AWS account.
- Users must be created with proper permissions.
- IAM is at the center of AWS.
- Policies are written in JSON.
- Roles: Internal usage within AWS resources.