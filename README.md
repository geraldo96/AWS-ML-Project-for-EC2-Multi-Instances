# Operationalizing Machine Learning on SageMaker

Author: **Geraldo Margjini**  
Date: **June 15, 2025**

This project demonstrates how to operationalize a deep learning model using AWS services such as **SageMaker**, **EC2**, **Lambda**, and **Auto Scaling**. The task focuses on training a model to classify dog breeds from images, deploying it, and enabling scalable, serverless inference.

## 🚀 Project Overview

This project covers the full ML operationalization lifecycle:

1. **Training and Deployment on SageMaker**
2. **Training on an EC2 Instance**
3. **Creating an AWS Lambda Function for Inference**
4. **Implementing Lambda Security**
5. **Configuring Concurrency and Auto-Scaling**

---

## 📦 Dataset

The dataset includes **133 dog breeds** and is composed of:

- **6680 training images**
- **835 validation images**
- **836 test images**

It is downloaded into an S3 bucket named `reco-dogs`.

---

## 📍 Step-by-Step Breakdown

### Step 1: Training and Deployment on SageMaker

- **Single Instance Training** using `ml.m5.xlarge` with best-found hyperparameters:
  - `batch_size = 256`
  - `learning_rate = 0.002896533293199136`
- **Multi-instance Training** with `instance_count = 4` for distributed processing.

### Step 2: EC2 Training

- EC2 instance used: `m5.2xlarge` with **Deep Learning AMI Neuron**.
- Model trained locally using a Python script (`solution.py`).
- Comparison with SageMaker highlights the trade-offs in flexibility, scalability, and automation.

### Step 3: Lambda Function

- Created a Lambda function for inference using the trained SageMaker endpoint.
- S3 image URLs are used to trigger predictions.

### Step 4: Lambda Security and Testing

- Applied a restricted IAM policy to ensure the Lambda function can only access the specific inference endpoint.
- Successfully tested inference using an image URL.

### Step 5: Concurrency and Auto-Scaling

- **Provisioned Concurrency**: 3
- **Reserved Concurrency**: 100
- **Endpoint Auto-Scaling**: Up to 4 instances
  - Scale-in cooldown: 30 seconds
  - Scale-out cooldown: 300 seconds

---

## 🧪 Tech Stack

- **AWS SageMaker**
- **AWS EC2**
- **AWS Lambda**
- **AWS S3**
- **PyTorch**
- **Python 3**

---

## 📝 Notes

- This project was developed within the AWS Free Tier constraints where possible.
- Screenshots of each step are provided in the original write-up.

---

## 📂 Repository Structure
