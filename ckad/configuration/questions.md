1. Create a directory with the name config. Within the directory, create two files. The first file should be named db.txt and contain the key-value pair password=mypwd. The second file is named ext-service.txt and should define the key-value pair api_key=LmLHbYhsgWZwNifiqaRorH8T.

2. Create a Secret named ext-service-secret that uses the directory as data source and inspect the YAML representation of the object.

3. Create a Pod named consumer with the image nginx and mount the Secret as a Volume with the mount path /var/app. Open an interactive shell and inspect the values of the Secret.

4. Use the declarative approach to create a ConfigMap named ext-service-configmap. Feed in the key-value pairs api_endpoint=https://myapp.com/api and username=bot as literals.

5. Inject the ConfigMap values into the existing Pod as environment variables. Ensure that the keys conform to typical naming conventions of environment variables.

6. Open an interactive shell and inspect the values of the ConfigMap.

7. Define a security context on the container level of a new Pod named security-context-demo that uses the image alpine. The security context adds the Linux capability CAP_SYS_TIME to the container. Explain if the value of this security context can be redefined in a Pod-level security context.

8. Define a ResourceQuota for the namespace project-firebird. The rules should constrain the count of Secret objects within the namespace to 1.

9. Create as many Secret objects within the namespace until the maximum number enforced by the ResourceQuota has been reached.

10. Create a new Service Account named monitoring and assign it to a new Pod with an image of your choosing. Open an interactive shell and locate the authentication token of the assigned Service Account.

11. Create a new file named config.txt with the following environment variables as key/value pairs on each line.
    DB_URL equates to localhost:3306
    DB_USERNAME equates to postgres

12. Create a new ConfigMap named db-config from that file.

13. Create a Pod named backend that uses the environment variables from the ConfigMap and runs the container with the image nginx.

14. Shell into the Pod and print out the created environment variables. You should find DB_URL and DB_USERNAME with their appropriate values.

15. Create a new Secret named db-credentials with the key/value pair db-password=passwd.

16. Create a Pod named backend that defines uses the Secret as environment variable named DB_PASSWORD and runs the container with the image nginx.

17. Shell into the Pod and print out the created environment variables. You should find DB_PASSWORD variable.

18. Create a Pod named secured that uses the image nginx for a single container. Mount an emptyDir volume to the directory /data/app.

19. Files created on the volume should use the filesystem group ID 3000.

20. Get a shell to the running container and create a new file named logs.txt in the directory /data/app. List the contents of the directory and write them down.

21. Create a resource quota named apps under the namespace rq-demo using the following YAML definition in the file rq.yaml.

```yaml
apiVersion: v1
kind: ResourceQuota
metadata:
  name: app
spec:
  hard:
    pods: "2"
    requests.cpu: "2"
    requests.memory: 500m
```

22. Create a new Pod that exceeds the limits of the resource quota requirements. Write down the error message.

23. Change the request limits to fulfill the requirements to ensure that the Pod could be created successfully. Write down the output of the command that renders the used amount of resources for the namespace.

24. Create a new service account named backend-team.

25. Print out the token for the service account in YAML format.

26. Create a Pod named backend that uses the image nginx and the identity backend-team for running processes.

27. Get a shell to the running container and print out the token of the service account.

28. Create a configmap named config with values foo=lala,foo2=lolo

29. Display its values

30. Create and display a configmap from a file
    echo -e "foo3=lili\nfoo4=lele" > config.txt

31. Create and display a configmap from a .env file
    echo -e "var1=val1\n# this is a comment\n\nvar2=val2\n#anothercomment" > config.env

32. Create and display a configmap from a file, giving the key 'special'
    Create the file with

echo -e "var3=val3\nvar4=val4" > config4.txt

33. Create a configMap called 'options' with the value var5=val5. Create a new nginx pod that loads the value from variable 'var5' in an env variable called 'option'

34. Create a configMap 'anotherone' with values 'var6=val6', 'var7=val7'. Load this configMap as env variables into a new nginx pod

35. Create a configMap 'cmvolume' with values 'var8=val8', 'var9=val9'. Load this as a volume inside an nginx pod on path '/etc/lala'. Create the pod and 'ls' into the '/etc/lala' directory.

36. Create the YAML for an nginx pod that runs with the user ID 101. No need to create the pod

37. Create the YAML for an nginx pod that has the capabilities "NET_ADMIN", "SYS_TIME" added on its single container

38. Create an nginx pod with requests cpu=100m,memory=256Mi and limits cpu=200m,memory=512Mi

39. Create a secret called mysecret with the values password=mypass

40. Create a secret called mysecret2 that gets key/value from a file
    Create a file called username with the value admin:

echo -n admin > username

41. Get the value of mysecret2

42. Create an nginx pod that mounts the secret mysecret2 in a volume on path /etc/foo

43. Delete the pod you just created and mount the variable 'username' from secret mysecret2 onto a new nginx pod in env variable called 'USERNAME'

44. See all the service accounts of the cluster in all namespaces

45. Create a new serviceaccount called 'myuser'

46. Create an nginx pod that uses 'myuser' as a service account
