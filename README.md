# Selfhosting github actions runner with actions-runner-controller

### Why selfhosting
Having self-hosted runners means having more control over them. Github runners are limited to a certain amount of resources to execute a workflow. By hosting these runners on our servers, we can allocate the desired amount of resources to the runners. This also allows us to have better visibility into workflow execution. By connecting the runners to Prometheus, we can easily obtain accurate information about them.

### Why actions-runner-controller
ARC provides dynamic runner management through a Kubernetes cluster. It easily connects to the desired code repositories to create runners on-demand when executing workflows. ARC offers two methods for scaling runners on-demand: polling and webhooks. The webhook method is prioritized in this example as it allows for a much quicker response to scale runners. A minimum number of runners is configured to be ready to quickly execute the initial workflows. For each additional workflow execution request, a new runner is created and started until the maximum number of configured runners is reached. Once the workflows are excecuted, unused pods running are terminated back to the minimum number configured. 

### Steps
1. Install cert-manager
2. Configure PAT or Github App
3. Install ARC
4. Deploy the runners
