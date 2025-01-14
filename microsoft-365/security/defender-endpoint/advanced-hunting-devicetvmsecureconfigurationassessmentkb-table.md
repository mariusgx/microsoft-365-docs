---
title: DeviceTvmSecureConfigurationAssessmentKB table in the advanced hunting schema
description: Learn about the various secure configurations assessed by Threat & Vulnerability Management in the DeviceTvmSecureConfigurationAssessmentKB table of the Advanced hunting schema.
keywords: advanced hunting, threat hunting, cyber threat hunting, mdatp, microsoft defender atp, wdatp search, query, telemetry, schema reference, kusto, table, column, data type, description, threat & vulnerability management, TVM, device management, security configuration, MITRE ATT&CK framework, knowledge base, KB, DeviceTvmSecureConfigurationAssessmentKB
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
---

# DeviceTvmSecureConfigurationAssessmentKB

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Applies to:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)


>Want to experience Defender for Endpoint? [Sign up for a free trial.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

The `DeviceTvmSecureConfigurationAssessmentKB` table in the advanced hunting schema contains information about the various secure configurations — such as whether a device has automatic updates on — checked by [Threat & Vulnerability Management](next-gen-threat-and-vuln-mgt.md). It also includes risk information, related industry benchmarks, and applicable MITRE ATT&CK techniques and tactics. Use this reference to construct queries that return information from the table.

For information on other tables in the advanced hunting schema, see [the advanced hunting reference](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference).

| Column name | Data type | Description |
|-------------|-----------|-------------|
| `ConfigurationId` | string | Unique identifier for a specific configuration |
| `ConfigurationImpact` | string | Rated impact of the configuration to the overall configuration score (1-10) |
| `ConfigurationName` | string | Display name of the configuration |
| `ConfigurationDescription` | string | Description of the configuration |
| `RiskDescription` | string | Description of the associated risk |
| `ConfigurationCategory` | string | Category or grouping to which the configuration belongs: Application, OS, Network, Accounts, Security controls|
| `ConfigurationSubcategory` | string |Subcategory or subgrouping to which the configuration belongs. In many cases, this describes specific capabilities or features. |
| `ConfigurationBenchmarks` | string | List of industry benchmarks recommending the same or similar configuration |
| `RelatedMitreTechniques` | string | List of Mitre ATT&CK framework techniques related to the configuration |
| `RelatedMitreTactics ` | string | List of Mitre ATT&CK framework tactics related to the configuration |

## Related topics

- [Advanced hunting overview](advanced-hunting-overview.md)
- [Learn the query language](advanced-hunting-query-language.md)
- [Understand the schema](advanced-hunting-schema-reference.md)
- [Overview of Threat & Vulnerability Management](next-gen-threat-and-vuln-mgt.md)
