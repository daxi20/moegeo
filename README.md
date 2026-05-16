# Moegeo Geofeed Community Repository

由 MoeDove LLC 维护的社区驱动型 Geofeed 聚合仓库。

A community-driven Geofeed aggregation repository maintained by MoeDove LLC.

---

本仓库旨在为网络运营商提供一个集中展示和聚合 [RFC 8805](https://datatracker.ietf.org/doc/html/rfc8805) 格式 Geofeed 文件的平台。通过聚合各家的 Geofeed，第三方定位服务商可以更便捷地获取和更新 IP 地理位置信息。

This repository provides a centralized platform for network operators to publish and aggregate [RFC 8805](https://datatracker.ietf.org/doc/html/rfc8805) compliant Geofeed files. By aggregating geofeeds from multiple sources, third-party geolocation providers can more easily access and update IP geolocation data.

## 🚀 如何提交您的 Geofeed？/ How to Submit Your Geofeed

我们**不**在仓库中直接存储您的 IP 数据，而是让您提交您自己托管的 `geofeed.csv` 的 URL。

We do **not** store your IP data directly in this repository. Instead, you submit the URL of your self-hosted `geofeed.csv`.

1. **Fork 本仓库。** / **Fork this repository.**
2. 复制 `feeds/example.yml` 并以您的 ASN 命名（例如：`AS12345.yml`），放入 `feeds/` 目录。/ Copy `feeds/example.yml`, rename it to your ASN (e.g., `AS12345.yml`), and place it in the `feeds/` directory.
3. 在 YAML 文件中填入您的网络信息和 Geofeed URL。/ Fill in your network information and Geofeed URLs in the YAML file.
4. **提交 Pull Request (PR)。** / **Submit a Pull Request (PR).**

我们的 GitHub Actions 将自动验证您提供的文件格式及 URL 的可达性和有效性。

Our GitHub Actions will automatically validate your file format and check the accessibility and validity of your URLs.

## 🛡️ 归属权验证 / Ownership Verification

如果您在提交 PR 时的 Commit 进行了 [GPG 签名验证](https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification)，并且该 Commit 邮箱与您 ASN 在 RIR (WHOIS/RDAP) 中注册的邮箱一致，系统将自动通过归属权验证，加快合并速度。否则，管理员将进行人工审核。

If your PR commit is [GPG-signed](https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification) and the signing email matches the email registered for your ASN in the RIR (WHOIS/RDAP) database, ownership verification will pass automatically, speeding up the merge process. Otherwise, a maintainer will perform a manual review.

## 🚫 受限国家代码 / Restricted Country Codes

包含以下国家代码的 Geofeed 条目将不会被汇总到聚合输出中：`KP`、`AQ`、`IR`。

Geofeed entries containing the following country codes will be excluded from the aggregated output: `KP`, `AQ`, `IR`.

## 💡 为什么使用 URL 提交？/ Why URL-based Submissions?

- 客户只需在自己的基础设施上维护原始的 Geofeed 文件，随时更新无需反复提交 PR。/ You maintain your Geofeed file on your own infrastructure and can update it at any time without submitting another PR.
- 我们的聚合脚本每天会自动拉取最新的数据。/ Our aggregation script automatically fetches the latest data daily.

更多详情，请查看 [CONTRIBUTING.md](./CONTRIBUTING.md)。/ For more details, see [CONTRIBUTING.md](./CONTRIBUTING.md).
