# Kubeflow

## Introduction
Kubeflow is an open-source platform built on Kubernetes designed to simplify and accelerate the development, deployment, and management of machine learning workflows. It provides a scalable and portable framework for running machine learning pipelines, automating model training and deployment, and facilitating collaboration among data scientists and ML engineers.

This repository serves as a starting point and documentation for using Kubeflow. It provides an overview of the key concepts, components, and steps to get started with Kubeflow.

## Key Features
- **Pipeline Orchestration:** Kubeflow allows you to define and orchestrate end-to-end machine learning pipelines, integrating various stages such as data preprocessing, model training, evaluation, and deployment.

- **Scalable and Distributed Training:** With Kubeflow, you can scale your machine learning workloads using distributed training techniques, harnessing the power of multiple GPUs or even multiple nodes.

- **Reproducibility and Versioning:** Kubeflow promotes reproducibility by providing versioning and tracking capabilities for your machine learning experiments, making it easier to reproduce and compare results.

- **Model Serving and Inference:** Kubeflow simplifies the process of serving and deploying trained models as scalable and robust web services, allowing easy integration into applications and systems.

## Prerequisites
- **minikube Installation:** Setup minikube before hand, you can install it from [https://minikube.sigs.k8s.io/docs/start/] as per your OS. Make sure you add the path for the .exe file to your environment variables.
- **Docker Installation:** Make sure Docker is installed in your system, for futher information on Doker installation visit [https://docs.docker.com/engine/install/].
- **Docker Initialization:** Make sure Docker is up and running.

- **Verify the Installation for minkube:**
   - Open a terminal or command prompt.
   - Run the following command to verify that Minikube is installed correctly:
     ```
     minikube version
     ```
   - If Minikube is installed successfully, you should see the version information displayed in the terminal or command prompt.



## Getting Started
To get started with Kubeflow, follow these steps:

1. **Installation:** Set up a Kubernetes cluster and install Kubeflow using the provided installation guides. Make sure you have the necessary dependencies, such as Docker and kubectl, installed on your machine.
- **Start Minikube:**
   - Open a terminal or command prompt.
   - Run the following command to start Minikube:
     ```
     minikube start
     ```
   - Minikube will start a virtual machine and configure the Kubernetes cluster.
   - This process may take a few minutes. Once the cluster is ready, you will see a success message in the terminal or command prompt.
- ** Interact with cluster using kubectl**
   - You can use the following command to check is the cluster is up and running
     ```
     kubectl get pod -A
     ```
- ** Deploying pipeline**
   - You can use the following command to deploy the pipeline, increase the timeout to 90s if it gives timeout related errors.
     ```
     set PIPELINE_VERSION=1.8.5
     kubectl apply -k "github.com/kubeflow/pipelines/manifests/kustomize/cluster-scoped-resources?ref=$PIPELINE_VERSION"
     kubectl wait --for condition=established --timeout=60s crd/applications.app.k8s.io
     kubectl apply -k "github.com/kubeflow/pipelines/manifests/kustomize/env/platform-agnostic-pns?ref=$PIPELINE_VERSION"
     ```
- ** User Interface**
   - You can use the following command to access Kubeflow UI to check the pipelines. Finally go to http://localhost:8080/ after running the command.
     ```
     kubectl port-forward -n kubeflow svc/ml-pipeline-ui 8080:80
     ```
kubectl port-forward -n kubeflow svc/ml-pipeline-ui 8080:80
2. **Create and Run Pipelines:** Use Kubeflow Pipelines to define and run your machine learning pipelines. Leverage the visual interface or the Python SDK to build complex workflows involving data processing, model training, and serving.


## Contributing
Contributions to Kubeflow are welcome! If you find any issues or have suggestions for improvements, please submit them via the issue tracker. You can also contribute by submitting pull requests to address existing issues or add new features.

Please read the CONTRIBUTING.md file for more details on how to contribute.

## License
This project is licensed under the Apache License 2.0. See the LICENSE file for more information.
