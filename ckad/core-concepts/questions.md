1. Create a new Pod named nginx running the image nginx:1.17.10. Expose the container port 80. The Pod should live in the namespace named `ckad`.

2. Get the details of the Pod including its IP address.

3. Create a temporary Pod that uses the `busybox` image to execute wget command inside of the container. The `wget` command should access the endpoint exposed by the nginx container. You should see the HTML response rendered in the terminal.

4. Get the logs of the `nginx` container

5. Add the environment variables `DB_URL=postgresql://mydb:5432` and `DB_USERNAME=admin` to the container of the `nginx` Pod.

6. Open a shell for the `nginx` container and inspect the contents of the current directoy `ls -l`.

7. Create a YAML manifest for a Pod named `loop` that runs the busybox image in a container. The container should run the following command: `for i in {1..10}; do echo "Welcome $i times"; done`. Create the Pod from the YAML manifest. Whats the status of the Pod?

8. Edit the Pod named `loop`. Change the command to run in an endless loop. Each iteration should `echo` the current date.

9. Inspect the events and the status of the Pod `loop`.

10. Delete the namespace `ckad` and its Pods.

11. Create a namespace called `mynamespace` and a pod with the image `nginx` called `nginx` on this namespace

12. Create the pod that was just described using YAML

13. Create a busybox pod (using kubectl cimmand) that runs the command `env`. Run it and see the output.

14. Create a busybox pod (using YAML) that runs the command `env`. Run it and see the output.

15. Get the YAML for a new namespace called `myns` without creating it.

16. Get the YAML for a new ResourceQuota called `myrq` with hard limits of 1 CPU, 1G memory and 2 pods without creating it.

17. Get pods on all namespaces

18. Create a pod with image nginx called nginx and expose traffic on port 80

19. Change pod's image to nginx:1.7.1. Observe that the container will be restarted as soon as the image gets pulled.

20. Get nginx pod's IP created in previous step, use a temp busybox image to wget its root path.

21. Get pod's YAML

22. Get information about the pod, including details about potential issues (e.g. pod hasn't started)

23. Get pod logs

24. If pod crashed and restarted, get logs about the prevous instance

25. Execute a simple shell on the nginx pod

26. Create a busybox pod that echoes `hello world` and then exists

27. Do the same, but have the pod deleted automatically when its completed.

28. Create an nginx pod and set an env values as `var1=val1`. Check the env value existence within the pod.

29. Create the namespace `ckad-prep`

30. In the namespace `ckad-prep` create a new Pod named `mypod` with the image `nginx:2.3.5`. Expose the port 80.

31. Identify the issue with creating the container. Write down the root cause of issue in a file named `pod-error.txt`.

32. Change the image of the Pod to `nginx:1.15.12`.

33. List the Pod and ensure that the container is running.

34. Log into the container and run the `ls` command. Write down the output. Log out of the container.

35. Retrieve the IP address of the Pod `mypod`.

36. Run a temporary Pod using the image busybox, shell into it and run a wget command against the nginx Pod using port 80.

37. Render the logs of Pod mypod.
38. Delete the Pod and the namespace.
