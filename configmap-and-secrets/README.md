


## Generate an `htpasswd` File and Store It as a Secret

Use htpasswd to generate an htpasswd file.

Create a secret called nginx-htpasswd, and store the contents of the htpasswd file in that Secret. Delete the htpasswd file once the Secret is created.





## Create the Nginx Pod

Create a pod with a single container using the nginx:1.19.1 image.

The Nginx configuration is stored in an existing ConfigMap called nginx-config. Mount the ConfigMap to /etc/nginx in your pod.

Mount your htpasswd secret to /etc/nginx/conf within your pod. The htpasswd data should be in a file in the container at /etc/nginx/conf/.htpasswd.

Expose containerPort 80 on the Nginx container so you can communicate with it to test your setup.
