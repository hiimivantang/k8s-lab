Run both `busybox` and `beebox` pods. 

Beebox unfortunately has been crashing repeatedly.

We are tasked to implement a self-healing solution while we perform RCA. 


## Set a Restart Policy to Restart the Container When It Is Down

Find the beebox-shipping-data pod located in the default namespace. Modify this pod so its restartPolicy will restart the container whenever it fails.

  Note: You may need to delete and re-create the pod in order to make this change.


## Create a Liveness Probe to Detect When the Application Has Crashed

Add a liveness probe to the container that checks the container status by making an HTTP request to the container every 5 seconds. The request should check the / (root) path on port 8080.

  Note: You may need to delete and re-create the pod in order to make this change.
