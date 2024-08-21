# redis-k8s-deployment
Step 1: Create a new repository on GitHub.
Step 2: Create a pod.yml file:
apiVersion: v1
kind: Pod
metadata:
  name: redis-pod
  labels:
    app: redis
spec:
  containers:
  - name: redis
    image: redis:latest
    ports:
    - containerPort: 6379

Step 3: Clone the repository: git clone https://github.com/Alreembader/redis-k8s-deployment.git
Step 4: cd redis-k8s-deployment
Step 5: Deploy the Redis pod: kubectl apply -f pod.yml
Step 6: kubectl get pods, to ensure that the stauts is running
Step 7: use this command: minikube start
Step 8: Expose the Redis pod using a NodePort service: kubectl expose pod redis-pod --type=NodePort --name=redis-svc --port=6379
Step 9: Verify the service is created: kubectl get services
Step 10: Get the details of the redis-svc service: kubectl describe service redis-svc
Step 11: use this command: kubectl get nodes -o wide
Step 12: I use this command(redis-cli -h localhost -p 31047), but dose not connect. XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXx
Step 13: using this command: kubectl get endpoints redis-svc , it change the port
Step 14: redis-cli -h localhost -p 6379 // using this command will connect successfully :) !! 



