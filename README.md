<!-- This file was automatically generated by the `build-harness`. Make all changes to `README.yaml` and run `make readme` to rebuild this file. -->
[![README Header][readme_header_img]][readme_header_link]

[![Cloud Posse][logo]](https://cpco.io/homepage)

# terraform-aws-cloudformation-stack-set

 [![Build Status](https://g.codefresh.io/api/badges/pipeline/cloudposse/cloudposse%2Fterraform-aws-cloudformation-stack-set%2Flint?type=cf-1)](https://g.codefresh.io/public/accounts/cloudposse/pipelines/cloudposse/terraform-aws-cloudformation-stack-set/lint) [![Latest Release](https://img.shields.io/github/release/cloudposse/terraform-aws-cloudformation-stack-set.svg)](https://github.com/cloudposse/terraform-aws-cloudformation-stack-set/releases/latest) [![Slack Community](https://slack.cloudposse.com/badge.svg)](https://slack.cloudposse.com)


Terraform module to provision Cloudformation Stack Set and Administrator IAM role.


---

This project is part of our comprehensive ["SweetOps"](https://cpco.io/sweetops) approach towards DevOps. 
[<img align="right" title="Share via Email" src="https://docs.cloudposse.com/images/ionicons/ios-email-outline-2.0.1-16x16-999999.svg"/>][share_email]
[<img align="right" title="Share on Google+" src="https://docs.cloudposse.com/images/ionicons/social-googleplus-outline-2.0.1-16x16-999999.svg" />][share_googleplus]
[<img align="right" title="Share on Facebook" src="https://docs.cloudposse.com/images/ionicons/social-facebook-outline-2.0.1-16x16-999999.svg" />][share_facebook]
[<img align="right" title="Share on Reddit" src="https://docs.cloudposse.com/images/ionicons/social-reddit-outline-2.0.1-16x16-999999.svg" />][share_reddit]
[<img align="right" title="Share on LinkedIn" src="https://docs.cloudposse.com/images/ionicons/social-linkedin-outline-2.0.1-16x16-999999.svg" />][share_linkedin]
[<img align="right" title="Share on Twitter" src="https://docs.cloudposse.com/images/ionicons/social-twitter-outline-2.0.1-16x16-999999.svg" />][share_twitter]


[![Terraform Open Source Modules](https://docs.cloudposse.com/images/terraform-open-source-modules.svg)][terraform_modules]



It's 100% Open Source and licensed under the [APACHE2](LICENSE).







We literally have [*hundreds of terraform modules*][terraform_modules] that are Open Source and well-maintained. Check them out! 







## Usage


**IMPORTANT:** The `master` branch is used in `source` just as an example. In your code, do not pin to `master` because there may be breaking changes between releases.
Instead pin to the release tag (e.g. `?ref=tags/x.y.z`) of one of our [latest releases](https://github.com/cloudposse/terraform-aws-cloudformation-stack-set/releases).


This example creates a role with the name `cp-prod-app` with permission to assume `` Chamber with S3 bucket as parameter store,
and gives permission to the entities specified in `assume_role_arns` to assume the role.

```hcl
module "default" {
  source = "git::https://github.com/cloudposse/terraform-aws-cloudformation-stack-set.git?ref=init"

  enabled            = "true"
  namespace          = "cp"
  stage              = "prod"
  name               = "app"
  template_url       = "https://aws-quickstart.s3.amazonaws.com/quickstart-compliance-cis-benchmark/templates/main.template"
  executor_role_name = "cis-executor"

  parameters         = {
    NotificationEmailAddressForCloudWatchAlarms = "notify-me@example.com"
    ConfigureCloudtrail = "Yes"
    ConfigureConfig = "Yes"
    ProfileLevel = "Level 2"
    QSS3BucketName = "aws-quickstart"
    QSS3KeyPrefix = "quickstart-compliance-cis-benchmark/"
  }

  capabilities = ["CAPABILITY_IAM"]
}
```






## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| attributes | Additional attributes (_e.g._ "1") | list | `<list>` | no |
| capabilities | A list of capabilities. Valid values: CAPABILITY_IAM, CAPABILITY_NAMED_IAM, CAPABILITY_AUTO_EXPAND | list | `<list>` | no |
| delimiter | Delimiter between `name`, `namespace`, `stage` and `attributes` | string | `-` | no |
| enabled | Set to false to prevent the module from creating any resources | string | `true` | no |
| executor_role_name | Name of the IAM Role in all target accounts for Stack Set operations | string | `AWSCloudFormationStackSetExecutionRole` | no |
| name | Name | string | `cis` | no |
| namespace | Namespace (e.g. `cp` or `cloudposse`) | string | - | yes |
| parameters | Key-value map of input parameters for the Stack Set template. (_e.g._ map("BusinessUnit","ABC") | map | `<map>` | no |
| stage | Stage (e.g. `prod`, `dev`, `staging`) | string | - | yes |
| tags | Additional tags (_e.g._ map("BusinessUnit","ABC") | map | `<map>` | no |
| template_url | Amazon S3 bucket URL location of a file containing the CloudFormation template body. Maximum file size: 460,800 bytes | string | - | yes |

## Outputs

| Name | Description |
|------|-------------|
| administrator_role_arn | Amazon Resource Number (ARN) of the IAM Role in the administrator account |
| executor_role_name | Name of the IAM Role in all target accounts for Stack Set operations |
| name | Name of the Stack Set |




## Share the Love 

Like this project? Please give it a ★ on [our GitHub](https://github.com/cloudposse/terraform-aws-cloudformation-stack-set)! (it helps us **a lot**) 

Are you using this project or any of our other projects? Consider [leaving a testimonial][testimonial]. =)


## Related Projects

Check out these related projects.




## Help

**Got a question?**

File a GitHub [issue](https://github.com/cloudposse/terraform-aws-cloudformation-stack-set/issues), send us an [email][email] or join our [Slack Community][slack].

[![README Commercial Support][readme_commercial_support_img]][readme_commercial_support_link]

## Commercial Support

Work directly with our team of DevOps experts via email, slack, and video conferencing. 

We provide [*commercial support*][commercial_support] for all of our [Open Source][github] projects. As a *Dedicated Support* customer, you have access to our team of subject matter experts at a fraction of the cost of a full-time engineer. 

[![E-Mail](https://img.shields.io/badge/email-hello@cloudposse.com-blue.svg)][email]

- **Questions.** We'll use a Shared Slack channel between your team and ours.
- **Troubleshooting.** We'll help you triage why things aren't working.
- **Code Reviews.** We'll review your Pull Requests and provide constructive feedback.
- **Bug Fixes.** We'll rapidly work to fix any bugs in our projects.
- **Build New Terraform Modules.** We'll [develop original modules][module_development] to provision infrastructure.
- **Cloud Architecture.** We'll assist with your cloud strategy and design.
- **Implementation.** We'll provide hands-on support to implement our reference architectures. 



## Terraform Module Development

Are you interested in custom Terraform module development? Submit your inquiry using [our form][module_development] today and we'll get back to you ASAP.


## Slack Community

Join our [Open Source Community][slack] on Slack. It's **FREE** for everyone! Our "SweetOps" community is where you get to talk with others who share a similar vision for how to rollout and manage infrastructure. This is the best place to talk shop, ask questions, solicit feedback, and work together as a community to build totally *sweet* infrastructure.

## Newsletter

Signup for [our newsletter][newsletter] that covers everything on our technology radar.  Receive updates on what we're up to on GitHub as well as awesome new projects we discover. 

## Contributing

### Bug Reports & Feature Requests

Please use the [issue tracker](https://github.com/cloudposse/terraform-aws-cloudformation-stack-set/issues) to report any bugs or file feature requests.

### Developing

If you are interested in being a contributor and want to get involved in developing this project or [help out](https://cpco.io/help-out) with our other projects, we would love to hear from you! Shoot us an [email][email].

In general, PRs are welcome. We follow the typical "fork-and-pull" Git workflow.

 1. **Fork** the repo on GitHub
 2. **Clone** the project to your own machine
 3. **Commit** changes to your own branch
 4. **Push** your work back up to your fork
 5. Submit a **Pull Request** so that we can review your changes

**NOTE:** Be sure to merge the latest changes from "upstream" before making a pull request!


## Copyright

Copyright © 2017-2019 [Cloud Posse, LLC](https://cpco.io/copyright)



## License 

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) 

See [LICENSE](LICENSE) for full details.

    Licensed to the Apache Software Foundation (ASF) under one
    or more contributor license agreements.  See the NOTICE file
    distributed with this work for additional information
    regarding copyright ownership.  The ASF licenses this file
    to you under the Apache License, Version 2.0 (the
    "License"); you may not use this file except in compliance
    with the License.  You may obtain a copy of the License at

      https://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing,
    software distributed under the License is distributed on an
    "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
    KIND, either express or implied.  See the License for the
    specific language governing permissions and limitations
    under the License.









## Trademarks

All other trademarks referenced herein are the property of their respective owners.

## About

This project is maintained and funded by [Cloud Posse, LLC][website]. Like it? Please let us know by [leaving a testimonial][testimonial]!

[![Cloud Posse][logo]][website]

We're a [DevOps Professional Services][hire] company based in Los Angeles, CA. We ❤️  [Open Source Software][we_love_open_source].

We offer [paid support][commercial_support] on all of our projects.  

Check out [our other projects][github], [follow us on twitter][twitter], [apply for a job][jobs], or [hire us][hire] to help with your cloud strategy and implementation.



### Contributors

|  [![Igor Rodionov][goruha_avatar]][goruha_homepage]<br/>[Igor Rodionov][goruha_homepage] |
|---|

  [goruha_homepage]: https://github.com/goruha
  [goruha_avatar]: https://github.com/goruha.png?size=150



[![README Footer][readme_footer_img]][readme_footer_link]
[![Beacon][beacon]][website]

  [logo]: https://cloudposse.com/logo-300x69.svg
  [docs]: https://cpco.io/docs
  [website]: https://cpco.io/homepage
  [github]: https://cpco.io/github
  [jobs]: https://cpco.io/jobs
  [hire]: https://cpco.io/hire
  [slack]: https://cpco.io/slack
  [linkedin]: https://cpco.io/linkedin
  [twitter]: https://cpco.io/twitter
  [testimonial]: https://cpco.io/leave-testimonial
  [newsletter]: https://cpco.io/newsletter
  [email]: https://cpco.io/email
  [commercial_support]: https://cpco.io/commercial-support
  [we_love_open_source]: https://cpco.io/we-love-open-source
  [module_development]: https://cpco.io/module-development
  [terraform_modules]: https://cpco.io/terraform-modules
  [readme_header_img]: https://cloudposse.com/readme/header/img?repo=cloudposse/terraform-aws-cloudformation-stack-set
  [readme_header_link]: https://cloudposse.com/readme/header/link?repo=cloudposse/terraform-aws-cloudformation-stack-set
  [readme_footer_img]: https://cloudposse.com/readme/footer/img?repo=cloudposse/terraform-aws-cloudformation-stack-set
  [readme_footer_link]: https://cloudposse.com/readme/footer/link?repo=cloudposse/terraform-aws-cloudformation-stack-set
  [readme_commercial_support_img]: https://cloudposse.com/readme/commercial-support/img?repo=cloudposse/terraform-aws-cloudformation-stack-set
  [readme_commercial_support_link]: https://cloudposse.com/readme/commercial-support/link?repo=cloudposse/terraform-aws-cloudformation-stack-set
  [share_twitter]: https://twitter.com/intent/tweet/?text=terraform-aws-cloudformation-stack-set&url=https://github.com/cloudposse/terraform-aws-cloudformation-stack-set
  [share_linkedin]: https://www.linkedin.com/shareArticle?mini=true&title=terraform-aws-cloudformation-stack-set&url=https://github.com/cloudposse/terraform-aws-cloudformation-stack-set
  [share_reddit]: https://reddit.com/submit/?url=https://github.com/cloudposse/terraform-aws-cloudformation-stack-set
  [share_facebook]: https://facebook.com/sharer/sharer.php?u=https://github.com/cloudposse/terraform-aws-cloudformation-stack-set
  [share_googleplus]: https://plus.google.com/share?url=https://github.com/cloudposse/terraform-aws-cloudformation-stack-set
  [share_email]: mailto:?subject=terraform-aws-cloudformation-stack-set&body=https://github.com/cloudposse/terraform-aws-cloudformation-stack-set
  [beacon]: https://ga-beacon.cloudposse.com/UA-76589703-4/cloudposse/terraform-aws-cloudformation-stack-set?pixel&cs=github&cm=readme&an=terraform-aws-cloudformation-stack-set
