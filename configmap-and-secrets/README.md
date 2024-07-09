


## Generate an `htpasswd` File and Store It as a Secret

Use htpasswd to generate an htpasswd file.

Create a secret called nginx-htpasswd, and store the contents of the htpasswd file in that Secret. Delete the htpasswd file once the Secret is created.





## Create the Nginx Pod

Create a pod with a single container using the nginx:1.19.1 image.

The Nginx configuration is stored in an existing ConfigMap called nginx-config. Mount the ConfigMap to /etc/nginx in your pod.

Mount your htpasswd secret to /etc/nginx/conf within your pod. The htpasswd data should be in a file in the container at /etc/nginx/conf/.htpasswd.

Expose containerPort 80 on the Nginx container so you can communicate with it to test your setup.


## Testing your solution

Remember to create the configmap with the supplied `config-map.yml` and run a busybox container for testing.
 
```
kubectl apply -f busybox.yml
kubectl apply -f config-map.yml
```

Assuming you have alread created the secret and the nginx pod based on the instructions above, you can now test your answer.

```
k exec busybox -- curl <your_nginx_pod_ip_address>

```
You should see 401 error: 401 Authorization Required. 


Next, supply the user name and password when curling.

```
k exec busybox -- curl -u user:<password> <your_nginx_pod_ip_address>
```



You should see the following output: 
```
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>


``` 
