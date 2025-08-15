# MinIO Deployment with Dokploy

This repository contains a MinIO deployment configuration optimized for Dokploy + Traefik + Hetzner.

## Endpoints

- **Web Console**: https://minio.aimamin.com
- **S3 API**: https://api.minio.aimamin.com

## DNS Configuration Required

Add these A records to your DNS:
```
minio.aimamin.com     → YOUR_HETZNER_SERVER_IP
api.minio.aimamin.com → YOUR_HETZNER_SERVER_IP
```

## Environment Variables for Dokploy

Set these in your Dokploy application settings:

```bash
MINIO_BROWSER_REDIRECT_URL=https://minio.aimamin.com
MINIO_SERVER_URL=https://api.minio.aimamin.com
```

## TypeScript/Node.js Integration

```bash
npm install minio @types/minio
```

```typescript
import { Client } from 'minio';

const minioClient = new Client({
  endPoint: 'api.minio.aimamin.com',
  port: 443,
  useSSL: true,
  accessKey: 'your-admin-user',
  secretKey: 'your-secure-password'
});
```

## Features

- ✅ SSL/TLS certificates via Let's Encrypt
- ✅ Traefik integration
- ✅ Docker Swarm compatible
- ✅ Persistent data storage
- ✅ Production-ready configuration