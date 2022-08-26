---
title: "chaosctl"
---

# ChaosCTL

[ChaosCTL](https://github.com/mental12345/chaosctl) is an open-source, chaos engineering as code, software that enables users to implement chaos engineering in the cloud infrastructure. 

![Screenshot](../static/screenshots/screenshot_hugo_help.png)

## Main Features
* Reads chaos engineering experiments in HCL format. 
* Limit blast radius with the help of tags.
* Both data deletion and server-shutdown perturbation models. 
* AWS compute and k8s services. 

## Starting your chaos experiments
chaosctl has a really simple worflow.
- write
- validate
- destroy

Start by creating a directory
```bash
mkdir chaosExperiment && cd chaosExperiment
```
Create a simple chaos config file and name it `experiment.hcl`

```hcl
app = "ProdApp"
description = "this is a chaos engineering experiment" 

job "aws" "ec2" {
    region = "us-east-1"
    config {
        tag = "Name:prod-web-server"
        chaos = "terminate"
        count = 6
    }
}
```

Execute the experiment:
```bash
chaosctl d experiment.hcl
```

This last experiment will terminate 6 EC2 instances with the tag *Name:prod-web-server* in region *us-east-1*

## Contribute
***chaosctl*** is written in Go, more features (and bugfixes) are in development, if you want a feature or contribute with code, please send and email or make a MR.

