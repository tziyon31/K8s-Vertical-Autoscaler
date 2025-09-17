# 🚀 k8s-vpa-demo  

This repository demonstrates how to deploy a sample **Flask application** on **Kubernetes**, generate CPU load, and use a **Vertical Pod Autoscaler (VPA)** to automatically monitor and adjust CPU resource requests for pods.  

---

## 📂 Repository Contents  

- **`vpa-cpu-testing.yml`**  
  Deployment + Service of a sample Flask application exposed via **NodePort (30080)**.  

- **`vpa-cpu.yml`**  
  Vertical Pod Autoscaler configuration that observes the Deployment and adjusts CPU requests  
  *(min: `100m`, max: `1000m`)*.  

- **`load.sh`**  
  Bash script that continuously sends requests to the service, generating **artificial CPU load** for testing autoscaling behavior.  

---

## 🧪 Demo Flow  

1. **Deploy the Flask app and Service**  
   ```bash
   kubectl apply -f vpa-cpu-testing.yml
2.**Apply the VPA manifest**

kubectl apply -f vpa-cpu.yml


3.**Run load generator (in background)**

./load.sh


4.**Observe VPA recommendations**

kubectl describe vpa flask-app


5.**Check updated pod resources**

kubectl get pods -o wide
kubectl describe pod <pod-name>

🎯 What You’ll Learn

How VPA monitors pod CPU usage.

How to stress-test a deployment with artificial load.

How VPA recommends and applies CPU request adjustments automatically.

This setup helps visualize how Kubernetes VPA reacts to increased workload by dynamically optimizing resource allocation for running pods.

📊 Visual Overview
+-------------+       +------------------+       +----------------------+
|  Load Gen   | --->  |  Flask App Pods  | --->  |  VerticalPodAutoscaler |
+-------------+       +------------------+       +----------------------+
        (./load.sh)        (Deployment)                 (VPA Controller)
