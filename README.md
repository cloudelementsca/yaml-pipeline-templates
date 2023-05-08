# Introduction 
This repo contains reusable templates for Azure Pipelines. 

# Reference the template in your Azure YAML Pipeline
In your Azure Pipelines YAML pipeline stage, job or steps, use the template key to provide reference to the file and template resource name. Use parameters to provide the required input for the template.

```
resources:
  repositories:
  - repository: templates
    type: github
    name: cloudelementsca/yaml-pipeline-templates
    ref: refs/heads/main

stages:
- stage: tfPlanStage
  jobs:
  - job: tfPlanJob
    steps:
    - template: terraform/tf-plan-tasks.yaml@tf-apply-template
      parameters:
        workingDirectory: ${{ parameters.workingDirectory }}
```
