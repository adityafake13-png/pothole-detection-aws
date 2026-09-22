# pothole-detection-aws
# 🚧 AI-Based Pothole Detection and Road Monitoring System

An IoT and cloud-based road monitoring system designed to detect potholes, measure their dimensions, capture pothole images, record location data, calculate severity and estimated repair material requirements, and display the collected information through a web dashboard.

The system combines Raspberry Pi, sensors, camera, AWS cloud services, and a web-based dashboard to create a prototype for automated road-condition monitoring.

---

## 📌 Project Overview

Potholes can cause vehicle damage, accidents, traffic disruption, and increased road maintenance costs.

This project aims to develop a compact prototype vehicle that travels over a road model and detects potholes using sensors.

When a pothole is detected, the system can collect:

- Pothole dimensions
- Pothole depth
- Pothole image
- Location information
- Route information
- Pothole severity
- Estimated material requirement
- Estimated repair cost

The collected information is sent to AWS, where it is stored and processed. A web dashboard is used to visualize the collected pothole information.

---

## 🎯 Objectives

The main objectives of this project are:

1. Detect potholes automatically using sensors.
2. Measure pothole dimensions and depth.
3. Capture an image of the detected pothole.
4. Record location information.
5. Send pothole information to the AWS cloud.
6. Store images using Amazon S3.
7. Store structured pothole data using Amazon DynamoDB.
8. Process pothole measurements using AWS Lambda.
9. Provide a web dashboard for monitoring potholes.
10. Calculate estimated repair material requirements and cost.

---

## 🏗️ System Architecture

```text
                ┌───────────────────────┐
                │      Road / Track     │
                │   With Potholes      │
                └───────────┬───────────┘
                            │
                            ▼
                ┌───────────────────────┐
                │     Sensors           │
                │ Depth / Distance      │
                └───────────┬───────────┘
                            │
                            ▼
                ┌───────────────────────┐
                │     Raspberry Pi      │
                │  Main Controller      │
                └───────┬───────┬───────┘
                        │       │
              ┌─────────┘       └─────────┐
              ▼                           ▼
       ┌─────────────┐             ┌─────────────┐
       │   Camera    │             │  Location   │
       │ Pothole     │             │   Data      │
       │   Image     │             └──────┬──────┘
       └──────┬──────┘                    │
              │                           │
              └────────────┬──────────────┘
                           ▼
                   ┌───────────────┐
                   │   AWS API     │
                   │ API Gateway   │
                   └───────┬───────┘
                           │
                           ▼
                   ┌───────────────┐
                   │ AWS Lambda    │
                   │ Calculation   │
                   └───────┬───────┘
                           │
                 ┌─────────┴─────────┐
                 ▼                   ▼
          ┌─────────────┐     ┌─────────────┐
          │ DynamoDB    │     │     S3      │
          │ Pothole     │     │   Images    │
          │ Data        │     │             │
          └──────┬──────┘     └─────────────┘
                 │
                 ▼
          ┌────────────────┐
          │ Web Dashboard  │
          │ Routes /       │
          │ Potholes /     │
          │ Severity /     │
          │ Material      │
          └────────────────┘
