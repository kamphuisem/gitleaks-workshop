# Integrate gitleaks in an Azure DevOps pipeline

So far, all effort we've put into the solution is client-side. This means that anybody with access to the git repo, still will be able to `SKIP` or commit secrets in other ways, without the pre-commit preventing the commit.

Once secrets get pushed to the git remote, it will be a lot harder to recover from. Once secrets get to the remote, you should consider them as 'leaked' and you need to take corrective measures like change passwords, rotate keys, etc. However, how to we know when secrets get pushed into our remote repo?

Fortunately for us, gitleaks secret detection is fairly easy to implement into a CI/CD pipeline. In this lab, we are going to use Azure DevOps to create a pipeline to do just that.

## Pre-assignment
If you have contributor access to an Azure DevOps project, you can use your own repo. If not, please let the instructor know your emailaddress, where you will be invited to a project. Create a branch from the repo, naming it something like 'workshop-YOURNAMEHERE'.

## Assignment
In your browser, add a file azure_pipeline.yaml via `Repos > Files > ... > New > File` and create a simple pipeline definition you can trigger manually. If you need hints on how to accomplish this, look in the 'hints' folder. Don't spend too much time trying to figure it out if you're having difficulties. Instead, try the 'hints/azure_pipelines.yaml' file and try to make sense of the command the pipeline is executing.

In Azure DevOps Pipelines, create a new pipeline from the YAML definition in your repo (choose a unique name, like you did with the new branch) and run it. 

What does the log say?