k8s-vpa-demo
This repository demonstrates how to deploy a sample Flask application on Kubernetes, generate CPU load, and use a Vertical Pod Autoscaler (VPA) to automatically monitor and adjust CPU resource requests for pods.

Contents

vpa-cpu-testing.yml – Deployment + Service of a sample Flask application exposed via NodePort (30080).

vpa-cpu.yml – Vertical Pod Autoscaler configuration that observes the Deployment and adjusts CPU requests (min: 100m, max: 1000m).

load.sh – Bash script that continuously sends requests to the service, generating artificial CPU load for testing autoscaling behavior.

Demo Flow

Deploy the Flask app and its Service.

Apply the Vertical Pod Autoscaler manifest.

Run ./load.sh to simulate traffic and stress CPU.

Observe VPA recommendations and automatic adjustments to pod CPU requests/limits.

This setup helps visualize how Kubernetes VPA reacts to increased workload by dynamically optimizing resource allocation for running pods.
