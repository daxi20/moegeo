# 贡献指南 / Contributing Guidelines

感谢您向 Moegeo 提供 Geofeed 数据！请遵循以下指南以确保您的提交能够被快速处理。

Thank you for contributing Geofeed data to Moegeo! Please follow these guidelines to ensure your submission is processed quickly.

## 提交格式 / Submission Format

请在 `feeds/` 目录下创建一个 YAML 文件，文件名为您的自治系统号（例如：`AS12345.yml`）。文件内容如下：

Create a YAML file in the `feeds/` directory named after your Autonomous System Number (e.g., `AS12345.yml`). The file should contain the following:

```yaml
name: "Your Organization Name / 您的组织或公司名称"
asn: "AS12345"
contact: "noc@example.com"
geofeed_urls:
  - "https://example.com/geofeed.csv"
  - "https://example.com/geofeed-v6.csv"
```

### 必填字段说明 / Required Fields

| 字段 / Field | 说明 / Description |
|---|---|
| `name` | 您的网络或组织全称。/ Full name of your network or organization. |
| `asn` | 您的自治系统号，必须以大写 `AS` 开头。/ Your ASN, must start with uppercase `AS`. |
| `contact` | 您的技术联系人邮箱。/ Your technical contact email. |
| `geofeed_urls` | 一个包含 Geofeed URL 的列表，至少包含一个 URL。/ A list of Geofeed URLs, at least one required. |

## Geofeed URL 规范 / Geofeed URL Requirements

您提供的 URL 必须 / Your URLs must:

1. 是 HTTP 或 HTTPS 协议。/ Use the HTTP or HTTPS protocol.
2. 可公开访问且返回 `200 OK` 状态。/ Be publicly accessible and return a `200 OK` status.
3. 内容严格符合 [RFC 8805](https://datatracker.ietf.org/doc/html/rfc8805) 的 CSV 格式。/ Strictly comply with the [RFC 8805](https://datatracker.ietf.org/doc/html/rfc8805) CSV format.

   示例格式 / Example format:
   ```csv
   192.0.2.0/24,US,US-WA,Seattle,
   2001:db8::/32,CN,CN-BJ,Beijing,
   ```

## 受限国家代码 / Restricted Country Codes

包含以下国家代码的条目将**不会**被汇总到聚合输出中。提交 PR 时，CI 会发出警告提醒您。

Entries with the following country codes will **NOT** be included in the aggregated output. The CI will issue a warning when you submit a PR.

| 国家代码 / Code | 国家 / Country |
|---|---|
| `KP` | 朝鲜 / North Korea |
| `AQ` | 南极洲 / Antarctica |
| `IR` | 伊朗 / Iran |

## 自动化检查与归属权验证 / Automated Checks & Ownership Verification

当您发起 Pull Request 时，GitHub Actions 会自动运行检查：

When you open a Pull Request, GitHub Actions will automatically run the following checks:

- 您的 YAML 文件格式是否正确。/ Whether your YAML file format is valid.
- 您提供的 URL 是否可以访问。/ Whether your URLs are reachable.
- URL 下载的 CSV 是否包含合法 IP 前缀。/ Whether the downloaded CSV contains valid IP prefixes.

**✅ 加速合并：GPG 签名验证 / Fast-track Merge: GPG Signature Verification**

为了防止恶意冒充，我们使用自动化归属权验证。如果满足以下两个条件，您的 PR 将被标记为"归属权已验证"，管理员可以快速合并：

To prevent impersonation, we use automated ownership verification. If both conditions below are met, your PR will be marked as "ownership verified" and can be merged quickly by maintainers:

1. 您的 Commit 已通过 GitHub 的 GPG 签名验证。/ Your commit is GPG-signed and verified by GitHub.
2. 您的签名邮箱与 RIR（RIPE/ARIN/APNIC 等）数据库中该 ASN 的 WHOIS/RDAP 记录邮箱一致。/ Your signing email matches the WHOIS/RDAP email on record for the ASN at the relevant RIR (RIPE/ARIN/APNIC, etc.).

如果未满足以上条件，您的 PR 将进入人工审核流程，管理员可能会通过您填写的邮箱与您联系确认。

If the above conditions are not met, your PR will go through manual review, and a maintainer may contact you via the email provided in your submission.
