## Reflection on Hello Minikube
1. Compare the application logs before and after you exposed it as a Service.
   Before exposing, I only saw the two “Started …” messages. After exposing, each page load adds a “GET /” line. Every time I open or refresh, the logs grow by one.
![image](https://github.com/user-attachments/assets/5be0aa96-2ab6-46d2-96ba-f044202fda40)
![image](https://github.com/user-attachments/assets/0628f4e5-37bd-4fbc-80dd-a4b9186a6393)

3.  Notice that there are two versions of `kubectl get` invocation during this tutorial section. The first does not have any option, while the latter has `-n` option with value set to
`kube-system`. What is the purpose of the `-n` option and why did the output not list the pods/services that you
explicitly created? The -n flag tells kubectl which namespace to look in. By default it shows only the default namespace. So when I ran kubectl get … -n kube-system it didn’t list my app’s pods/services because those live in the default namespace.
![image](https://github.com/user-attachments/assets/7ec19aa6-d107-49a3-8209-21f62a412385)
