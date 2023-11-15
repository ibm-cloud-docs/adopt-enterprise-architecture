---

copyright:
  years: 2023
lastupdated: "2023-11-15"

subcollection: adopt-enterprise-architecture

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Identifying risks and barriers
{: #risks}

A solid risk management plan, including identification of potential barriers, is essential to a successful transition.
{: shortdesc}

1. Per project, after a strategy is determined, identify workload-specific risks or barriers.
   - Technical challenges might include availability concerns, data sync issues, encryption, application technical limitations, and so on.
   - Nontechnical challenges might include data protection or compliance concerns (for example, GDPR), cost, timing (avoid peak loads), training, org impacts, resourcing, and so on.
1. Develop risk mitigation strategies.
   - For example, ensure that migrated data remains encrypted, don’t touch live workloads during sync, plan any reorganizations, providing training, and so on.
1. Ensure the plan, including the risk mitigation, is documented for each transition project.

## Common challenges
{: #challenges}

- Live data is not easy to migrate.
   - Data in active applications is changing rapidly and thus cannot be easily migrated through backup and restore.
- Applications and infrastructure deployment is not automated.
   - Automation to redeploy is not available or not suitable.
- Applications contain hardcoded references.
   - Applications refer to specific IP or DNS or other addresses that make setting up a parallel deployment difficult.
   - Applications refer to specific service or user identities that are account-specific make moving to a new account difficult.
- Joining multiple VPCs with transit gateways can be complicated by problems with overlapping address spaces and poor network ACLs.
