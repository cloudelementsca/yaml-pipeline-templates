# Introduction 
Create YAML templates by extracting commonly used tasks into templates that can be used by other YAML pipelines to provide consistent and re-usable jobs/stages.

# Getting Started
## 1.	Using the YAML templates

In the YAML template, you will need to create a resource reference to the YAML template repository.

In the example below, repository *templates* is the resource name that can be referenced later. The name attribute has the specific inforamtion of the repository. To use the template from a specific branch or tag, the *ref* attribute can be used.

```
resources:
  repositories:
  - repository: templates
    type: github
    name: cloudelementsca/yaml-pipeline-templates
    ref: refs/heads/<branch name>
```

## 2.	Reference the template in your YAML pipeline
In you YAML stage, job or steps, use the template key to provide reference to the file and template resource name. Use parameters to provide the required parameters for the template.

In the example below, *terraform/tf-plan-tasks.yaml* refers to the path and file name of the resource *templates*. 

```
steps:
- template: terraform/tf-plan-tasks.yaml@templates
  parameters:
    workingDirectory: terraform/mymodule
    tfbackend: dev.config.tfbackend
```
