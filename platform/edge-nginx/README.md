# Edge Gateway (Host NGINX)

This directory contains the host-level NGINX configuration used as the on-prem
edge gateway for the Online Shop platform.

This component is the on-prem equivalent of a cloud-managed edge load balancer.

Cloud equivalents:
- Azure: Front Door / Application Gateway
- AWS: Application Load Balancer (ALB)
- GCP: External HTTPS Load Balancer

## Purpose

- Bind real host ports 80 and 443 on the laptop
- Terminate HTTPS using mkcert-generated certificates
- Forward traffic to the Kubernetes Ingress Controller via NodePort

## Traffic Flow

Browser
→ https://shop.lab (443)
→ Host NGINX (Ubuntu)
→ Kubernetes Ingress NodePort (31251)
→ Ingress Controller
→ Service
→ Pod

## Files

- shop.lab.nginx.conf  
  The NGINX virtual host configuration used on the host.

## Notes

- TLS private keys are NOT stored in Git.
- Certificates are expected at:
  /etc/nginx/certs/shop.lab.pem
  /etc/nginx/certs/shop.lab-key.pem
- This config is meant for on-prem / lab / datacenter setups.
