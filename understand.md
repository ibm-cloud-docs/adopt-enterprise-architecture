---

copyright:
  years: 2023
lastupdated: "2023-11-15"

subcollection: adopt-enterprise-architecture

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Adopting the Enterprise Architecture
{: #intro}

The [enterprise architecture](/docs/enterprise-account-architecture) is a holistic architecture for large enterprises to use {{site.data.keyword.cloud}} at scale while staying within {{site.data.keyword.cloud_notm}} limits.
{: shortdesc}

The enterprise architecture follows [best practices and principles](/docs/enterprise-account-architecture?topic=enterprise-account-architecture-principles) across networking, resource organization, security, Infrastructure as Code (IaC), and other domains. The impact of this holistic approach is a dramatic reduction in application team overhead, leading to increased productivity, security, and compliance. It is necessary to understand the enterprise architecture before reading this paper.

While each enterprise has a unique starting point, some form of transition is typically required for an enterprise to use these recommendations. By adopting the recommendations, your enterprise gains the benefits of the architecture such as high scale, reduced cost, and improved compliance and security posture.

This paper discusses strategies that can be used to adopt the enterprise architecture from almost any starting point.

## Adoption framework
{: #adoption_framework}

Adoption of the enterprise architecture can be framed as a set of steps and decision points. This framework provides a methodical process to transition workloads to the enterprise architecture by using the following steps:

1. [Understand the benefits and objectives](#objectives)
2. [Assess existing workloads](/docs/adopt-enterprise-architecture?topic=adopt-enterprise-architecture-assess)
3. [Determine the best transition strategy](/docs/adopt-enterprise-architecture?topic=adopt-enterprise-architecture-migration-strategy)
4. [Identify risks and barriers](/docs/adopt-enterprise-architecture?topic=adopt-enterprise-architecture-risks)
5. [Prepare](/docs/adopt-enterprise-architecture?topic=adopt-enterprise-architecture-prep)
6. [Apply transition strategies](/docs/adopt-enterprise-architecture?topic=adopt-enterprise-architecture-migrate)
7. [Evaluate success and clean up](/docs/adopt-enterprise-architecture?topic=adopt-enterprise-architecture-evaluate)


## Understanding benefits and objectives
{: #objectives}

The enterprise architecture uses best practices to achieve compliance, scale, efficiency, security, and effective FinOps. This architecture is aligned with {{site.data.keyword.IBM_notm}} internal use and benefits from high levels of {{site.data.keyword.IBM_notm}} support. For more details, see the [Enterprise architecture](/docs/enterprise-account-architecture) white paper.

Depending on your organization's starting point and objectives, it might be desirable to adopt only a subset of the recommendations. For this reason, it is important to define your objectives for transitioning a particular workload.

To plan for your adoption of the enterprise architecture, ask yourself:

* What is the scope of adoption? Should certain workloads be excluded?
* What is the end state that you want for particular workloads?
* What is the timeline?
* Does adoption pose more risk for certain elements?

### Justifying a change
{: #justifying}

Key motivations for adopting the enterprise architecture include:
* Cost savings. Shared infrastructure efficiencies, reduced operations overhead, and better FinOps practices reduce cost.
* Increased compliance and security. Deployable architectures start secure and compliant and can be centrally maintained. Infrastructure audits are handled centrally and with fewer resources.
* Easier operations. A central team manages infrastructure, which requires fewer operations resources and maximizes resources with scarce expertise.
* Reduced need for expensive skill sets that are outside the focus of the business. Networking, security, and compliance expertise can be centralized into one team for greater effect.
* Increased scale. Scaling limitations for applications and organizations are avoided.
* Increased governance. The architecture reduces the opportunity for errors, allows rollbacks, and eliminates the possibility for bad actors to undermine security controls.
* Dramatically improve application developer productivity. Application developers don't need to concern themselves with infrastructure, high availability, BCDR, compliance, or security.
