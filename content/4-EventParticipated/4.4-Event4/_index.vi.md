---
title: "Event 4"
date: 2025-10-16
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---


# Bài Thu Hoạch: AWS Cloud Mastery Series #3 — AWS Well-Architected Security Pillar

## 1. Mục đích sự kiện
- Giới thiệu vai trò của Security Pillar trong AWS Well-Architected Framework.
- Trình bày 5 trụ cột bảo mật: IAM, Detection, Infrastructure Protection, Data Protection, Incident Response.
- Cung cấp best practices và các kịch bản thực tế để bảo vệ ứng dụng trên môi trường Cloud.

## 2. Nội dung chính

### Pillar 1 — Identity & Access Management (IAM)
- Nguyên tắc: Least Privilege, Zero Trust, Defense in Depth.
- IAM hiện đại: tránh long-term credentials, ưu tiên IAM Roles và managed policies.
- IAM Identity Center: SSO, Permission Sets, quản lý truy cập tập trung.
- Bảo mật multi-account: Service Control Policies và Permission Boundaries.
- Mini demo: kiểm tra IAM policy và mô phỏng hành vi truy cập.

### Pillar 2 — Detection
- Giám sát liên tục với CloudTrail (org-level), GuardDuty, Security Hub.
- Logging đa tầng: VPC Flow Logs, ALB logs, S3 access logs.
- Tự động hóa cảnh báo qua Amazon EventBridge.

### Pillar 3 — Infrastructure Protection
- Bảo mật mạng: tách lớp network (public/private VPC).
- Cơ chế phòng thủ: Security Groups vs NACLs, AWS WAF, Shield, Network Firewall.
- Bảo mật workload: EC2, ECS/EKS ở mức cơ bản.

### Pillar 4 — Data Protection
- Mã hóa dữ liệu at-rest và in-transit (S3, EBS, RDS, DynamoDB).
- KMS cho quản lý khóa; Secrets Manager và Parameter Store cho quản lý secrets.
- Phân loại dữ liệu và thiết lập guardrails truy cập.

### Pillar 5 — Incident Response
- Vòng đời Incident Response theo AWS.
- Xây dựng IR playbook và tự động hóa với Lambda/Step Functions.
- Kịch bản mẫu: lộ IAM keys, S3 public exposure, phát hiện malware trên EC2.

## 3. Kiến thức rút ra
- Hiểu rõ 5 trụ cột của Security Pillar và Shared Responsibility Model.
- Áp dụng IAM nâng cao: Identity Center, SCPs, tránh sử dụng long-term credentials.
- Nắm tầm quan trọng của Data Security: KMS, secrets management.
- Biết cách xây dựng và tự động hóa Incident Response thông qua serverless workflows.

## 4. Trải nghiệm sự kiện
- Workshop mang tính tổng kết chuỗi học, tăng cường nền tảng bảo mật trước khi hoàn thiện dự án.
- Phần IAM Identity Center và Secrets Manager giải quyết trực tiếp bài toán xác thực và quản lý khóa API của nhóm.
- Các kịch bản IR (như S3 public exposure) giúp củng cố chính sách bảo mật của dự án.
- Buổi Q&A định hướng thêm về lộ trình chứng chỉ AWS Security Specialty.
