CloudStack PHP Client
=====================

PHP client library for the CloudStack User API v2.2 (Reference : http://download.cloud.com/releases/2.2.0/api_2.2.8/TOC_User.html)

Generate with the CloudStack client generator [qpleple/cloudstack-client-generator](https://github.com/qpleple/cloudstack-client-generator),
others languages are available. Check out this project to know more about it.

Changes to the original:
	* Uses PHP's curl instead of PECL HttpRequest
	* Replaced each 4 whitespaces by a tabulator


Examples
--------

Initialization

    $cloudstack = new CloudStackClient(API_ENDPOINT, API_KEY, SECRET_KEY);
   
Lists

    $vms = $cloudstack->listVirtualMachines();
    foreach ($vms as $vm) {
        echo("{$vm->id} : {$vm->name} {$vm->state}<br>");
    }
   
Asynchronous tasks

    $job = $cloudstack->deployVirtualMachine(1, 259, 1);
    echo("VM being deployed. Job id = {$job->jobid}<br>");
    
    echo("All jobs :<br>");
    foreach ($cloudstack->listAsyncJobs() as $job) {
        echo("{$job->jobid} : {$job->cmd}, status = {$job->jobstatus}<br>");
    }
