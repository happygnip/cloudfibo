<p align="center">
  <img src="assets/brand/cloudfibo-logo.svg" alt="CloudFibo" width="280" />
</p>

<h1 align="center">CloudFibo AI Infrastructure Operations Platform</h1>

<p align="center">
  Unify resources, delivery, operations, cost, and AI analysis on a controlled and auditable infrastructure foundation
</p>

<p align="center">
  <a href="README.md">简体中文</a> · <strong>English</strong>
</p>

<p align="center">
  <a href="https://cloudfibo.com">Website</a> ·
  <a href="docs/DEPLOYMENT.md">Deployment</a> ·
  <a href="docs/LICENSE_REQUEST.md">Request a License</a> ·
  <a href="https://github.com/happygnip/cloudfibo/discussions">Community</a>
</p>

CloudFibo is built for public clouds, private clouds, virtualization, Kubernetes, and critical IT infrastructure. Its unified resource model and business-domain context connect resources, relationships, observability, incidents, tasks, and cost data in one platform, while permissions, approval, confirmation, and audit controls protect operational boundaries.

## Platform Architecture

<p align="center">
  <img src="assets/architecture/cloudfibo-platform-architecture-zh.png" alt="CloudFibo platform architecture" width="100%" />
</p>

One resource model supports infrastructure onboarding, asset management, service delivery, observability, automation, FinOps, and AI-assisted operations. OpenAPI, webhooks, events, and adapters connect CloudFibo with existing enterprise systems.

## Core Capabilities

| Pillar | Capabilities | Outcome |
| --- | --- | --- |
| Unified resource foundation | Multi-cloud accounts, continuous discovery, normalized models, relationships, business ownership | A continuously updated and auditable infrastructure source of truth |
| Standardized service delivery | Service catalog, dynamic requests, policy approval, blueprints, automation, result reconciliation | Reusable and traceable infrastructure delivery |
| Intelligent operations loop | Monitoring, alert governance, incidents, logs, jobs, diagnostics, AI-assisted analysis | A shorter path from detection to analysis, remediation, validation, and review |
| Operations and security governance | Multi-cloud billing, allocation, budgets, optimization, scoped access, controlled execution, audit | Clear cost accountability and bounded automation |

## Product Views

<table>
  <tr>
    <td width="50%" align="center">
      <img src="assets/screenshots/multi-cloud-resource-management.png" alt="Multi-cloud resource management" width="100%" /><br />
      <strong>Multi-cloud Resource Management</strong><br />
      <sub>Connect heterogeneous platforms and continuously synchronize resources, status, tags, and relationships.</sub>
    </td>
    <td width="50%" align="center">
      <img src="assets/screenshots/finops-cost-governance.png" alt="FinOps cost governance" width="100%" /><br />
      <strong>FinOps Cost Governance</strong><br />
      <sub>Consolidate billing, allocation, trend analysis, anomaly detection, and continuous optimization.</sub>
    </td>
  </tr>
</table>

<p align="center">
  <img src="assets/screenshots/ai-insight-analysis.png" alt="AI insight and analysis" width="760" /><br />
  <strong>AI Insight and Controlled Response</strong><br />
  <sub>Correlate resources, metrics, alerts, incidents, tasks, and cost evidence into explainable analysis and action guidance.</sub>
</p>

> Screenshots use demonstration data. Available features vary by CloudFibo release and license edition.

## Infrastructure Coverage

- Public cloud: AWS, Azure, Google Cloud, Alibaba Cloud, Huawei Cloud, Tencent Cloud, Baidu AI Cloud, JD Cloud, China Telecom Cloud, China Mobile Cloud, Volcengine, and others.
- Private cloud and virtualization: VMware, Proxmox, ZStack, CloudTower, FusionCompute, Huawei HCS/HCSO, SCP, and others.
- Cloud native: Kubernetes, Rancher, clusters, nodes, workloads, and related resources.

Exact resource and lifecycle-operation coverage depends on the CloudFibo version, provider APIs, and license edition. Refer to each release's compatibility notes.

## Quick Start

CloudFibo provides a Docker Compose deployment package. Release artifacts are published through GitHub Releases and mirrored to Alibaba Cloud OSS.

- [Docker Compose deployment guide](docs/DEPLOYMENT.md) (Chinese)
- [v3.3.5-build.2026070801 offline image archive](https://cloudfibo-release.oss-cn-beijing.aliyuncs.com/compose/3.3.5/v3.3.5-build.2026070801/cloudfibo-compose-v3.3.5-build.2026070801.tar)

```bash
# Download and extract cloudfibo-compose-<version>.tar.gz from a Release or OSS.
cd deploy/docker-compose
chmod +x ./deploy.sh
./deploy.sh --public-origin "https://localhost:8443" --gateway-https-port 8443
```

After deployment, open:

```text
https://<server-ip-or-domain>:8443/
```

## License

The deployment package is free to download and install. CloudFibo product capabilities are enabled by an offline license bound to the installation fingerprint.

- [License request process and email template](docs/LICENSE_REQUEST.md) (Chinese)
- License signatures are verified locally; normal operation does not require a persistent connection to an external licensing service.
- Never post a platform fingerprint, license file, credentials, or customer-sensitive data in a public Issue or Discussion.

## Community and Support

- Questions, practices, and feature ideas: [GitHub Discussions](https://github.com/happygnip/cloudfibo/discussions)
- Reproducible defects: [GitHub Issues](https://github.com/happygnip/cloudfibo/issues)
- Deployment, commercial, and license requests: `postmaster@cloudfibo.com`
- Security reports: follow [SECURITY.md](SECURITY.md) and report privately

See [SUPPORT.md](SUPPORT.md), [CONTRIBUTING.md](CONTRIBUTING.md), and [LEGAL.md](LEGAL.md) for additional guidance.

Copyright © CloudFibo. All rights reserved.
