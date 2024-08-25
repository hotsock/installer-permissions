# Hotsock Installer Permissions

This repository contains the permissions CloudFormation template used [during Hotsock installation](https://www.hotsock.io/docs/installation/initial-setup/#installer-permissions-stack).

It is provided here for easy auditability and change history.

## Included Resources

When creating a stack with the [installer-permissions.yml](./installer-permissions.yml) template, the following resources will be created in your AWS account.

- **`HotsockInstallerRole`**: IAM role that allows CloudFormation to manage Hotsock installations with appropriate permissions. It grants IAM role and policy management permissions within the `/hotsock/` IAM path and grants permissions in the `HotsockMaximumPermissions` managed policy described below.
- **`HotsockSupportRole`**: IAM role that can allow Hotsock support staff to access your account to triage issues upon your request. **Access is denied by default** with an expired date condition in the assume role trust relationship, which must be set to a date in the future to grant access.
- **`HotsockLicensingRole`**: IAM role that allows Hotsock to perform licensing operations and collect usage data for installation metering.
- **`HotsockMaximumPermissions`**: IAM managed policy that specifies the maximum permissions needed for Hotsock, used to grant permissions to `HotsockInstallerRole` and `HotsockSupportRole` and used as the mandatory [Permissions Boundary](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_boundaries.html) for all roles created by `HotsockInstallerRole`.
