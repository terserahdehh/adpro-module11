## Reflection on Hello Minikube

1. Compare the application logs before and after you exposed it as a Service.
   Before exposing, I only saw the two “Started …” messages. After exposing, each page load adds a “GET /” line. Every time I open or refresh, the logs grow by one.
![image](https://github.com/user-attachments/assets/5be0aa96-2ab6-46d2-96ba-f044202fda40)
![image](https://github.com/user-attachments/assets/0628f4e5-37bd-4fbc-80dd-a4b9186a6393)
2.  Notice that there are two versions of `kubectl get` invocation during this tutorial section. The first does not have any option, while the latter has `-n` option with value set to
`kube-system`. What is the purpose of the `-n` option and why did the output not list the pods/services that you
explicitly created? The -n flag tells kubectl which namespace to look in. By default it shows only the default namespace. So when I ran kubectl get … -n kube-system it didn’t list my app’s pods/services because those live in the default namespace.
![image](https://github.com/user-attachments/assets/7ec19aa6-d107-49a3-8209-21f62a412385)

## Reflection on Rolling Update & Kubernetes Manifest File

1. What is the difference between Rolling Update and Recreate deployment strategy?
Rolling Update replaces pods one by one, keeping the app available. Recreate stops all old pods before starting new ones, causing downtime. Rolling Update suits zero‐downtime updates, while Recreate suits a full restart.
3. Try deploying the Spring Petclinic REST using Recreate deployment strategy and document your attempt.
I changed the deployment strategy to Recreate and removed the rollingUpdate settings. I ran kubectl apply -f deployment-recreate.yaml to deploy. Kubernetes terminated all old pods before starting the new ones.
5. Prepare different manifest files for executing Recreate deployment strategy.
6. What do you think are the benefits of using Kubernetes manifest files? Recall your experience in deploying the app manually and compare it to your experience when deploying the same app by applying the manifest files (i.e., invoking `kubectl apply -f` command) to the cluster.
I can save and version my YAML files so I don’t have to remember all the commands each time. Applying kubectl apply -f is faster and less error-prone than typing everything by hand. Manifests make it easy to share and reproduce the exact same setup on any cluster.






