---

copyright:
  years: 2023
lastupdated: "2023-11-03"

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

## Assessing existing resources and workloads
{: #assess}

Before you determine an adoption strategy, build an inventory of existing resources and workloads.

This inventory might include catalog resources like clusters, databases, and other services, but also include things like access policies and account settings. Then, assess the inventory to determine how the existing resources and workloads would fit into the [recommended account structure](/docs/enterprise-account-architecture?topic=enterprise-account-architecture-account-structure).

![account structure diagram](./images/account-structure.svg){: caption="Recommended account structure" caption-side="bottom"}

1. Locate accounts and workloads that need to be moved. Make sure that all resources are allocated, as missed resources cause problems later on. Use billing records to locate all {{site.data.keyword.cloud_notm}} accounts that potentially contain resources. Use [global search](/docs/account?topic=account-ibmcloud_commands_resource&interface=ui#ibmcloud_resource_search) to locate resources within accounts and record them.
1. Logically partition the existing resources into groups by architecture, sensitivity, automation, and so on. Then, subgroup these resources based on where they fall in the [enterprise architecture account structure](/docs/enterprise-account-architecture?topic=enterprise-account-architecture-account-structure). Be sure to include groups for network infrastructure, common services, backups, nonproduction and production workloads, and so on, as including these groups eases reasoning about the transition.
1. Take note of key factors that influence adoption strategies. Some key factors include types of data storage (and resulting data migration capabilities), availability requirements for applications (and possibility for scheduled downtime), business criticality of applications, scale, and complexity.
1. Delete unneeded resources or mark them as unneeded by using tags. Don't waste effort on unneeded resources or workloads. The Resource Explorer can help you find unused catalog resources and Identity and Access Management can help you find unused security resources.

## Determining your adoption strategy
{: #migration-strategy}

Adopting the enterprise architecture might include both organizational and technical transformation to achieve all the benefits.

To determine your adoption strategy:

1. Evaluate the delta between the existing architecture and the [target architecture](/docs/enterprise-account-architecture?topic=enterprise-account-architecture-account-structure) for each group of resources. Consider your account, security posture, and level of automation.
1. Pick a strategy appropriate for the workload or related group of workloads. Use the [decision tree](#decision-tree) to help with strategy selection.
1. Consider how these changes will affect users. Reorganizing operations, security, network, and compliance expertise might be needed. Also, new cloud access procedures and operational processes might be required.


### Technical strategies
{: #technical}

On the technical side, several strategies can be considered:

* [App by App migration](./migrate/#app-by-app-migration). Migrate one workload or a group of workloads at a time into newly created workload accounts. Deploy a new set of accounts that follow the enterprise architecture recommendations. Then dual deploy workloads to both old and new infrastructure until data migration and testing is complete.
* [Piecemeal migration](./migrate/#piecemeal-migration-identity-and-access-management). Migrate individual aspects only. For example, move dev to a new structure, or adopt the IAM recommendations, or move to the recommended network architecture only. Details depend on what aspect is being migrated.
* [New applications only](./migrate-enterprise-account-architecture?topic=migrate-enterprise-account-architecture-migrate#new). Leave existing workloads alone, only new work is deployed into the new structure.
* [Transform in place](./migrate-enterprise-account-architecture?topic=migrate-enterprise-account-architecture-migrate#transform-in-place). Implement the architecture by gradually transforming existing deployments rather than migrating to a parallel set of infrastructure.
* [Hybrid](./migrate-enterprise-account-architecture?topic=migrate-enterprise-account-architecture-migrate#hybrid). For example, transform databases in place and then use an app by app approach to move workloads to a parallel infrastructure.

Each strategy has more details, including pros and cons.


### Technical strategy decision tree
{: #decision-tree}

To help with selecting technical strategies, the following decision tree can be used as a guide:

![decision tree](./images/decision-tree.svg){: caption="Technical strategy decision tree" caption-side="bottom"}

Keep in mind that any decision tree incorporates only a few key criteria, so be sure to read up on the details of each strategy before adopting.

### Nontechnical aspects of adoption
{: #organizational }

In addition to the technical aspects of adopting the enterprise architecture recommendations, there might be impacts to individual users, procedures, and organizations that should be considered.

* DevOps users might need training on the use of [Infrastructure as Code](https://www.ibm.com/topics/infrastructure-as-code) as they transition from directly manipulating cloud resources to adopting Infrastructure as Code.
* All users might need to login to different cloud accounts and potentially learn how and when to use trusted profiles as the centralized administration model is adopted.
* DevOps procedures and runbooks might need to be updated to align with new network models, centralized administration, IaC, and so on.
* Development and DevOps teams might benefit from reorganization so that experts in core functions such as infrastructure as code, security, networking, and compliance are located in centralized teams that are responsible for developing and maintaining the deployable architectures for shared infrastructure.
* Operations teams might benefit from reorganization so that operations experts are located in centralized teams that operate the shared infrastructure.

## Identifying risks and barriers
{: #risks}

A solid risk management plan, including identification of potential barriers, is essential to a successful transition.

1. Per project, after a strategy is determined, identify workload-specific risks or barriers.
   - Technical challenges might include availability concerns, data sync issues, encryption, application technical limitations, and so on.
   - Nontechnical challenges might include data protection or compliance concerns (for example, GDPR), cost, timing (avoid peak loads), training, org impacts, resourcing, and so on.
1. Develop risk mitigation strategies.
   - For example, ensure that migrated data remains encrypted, don’t touch live workloads during sync, plan any reorganizations, providing training, and so on.
1. Ensure the plan, including the risk mitigation, is documented for each transition project.

### Common challenges
{: #challenges}

- Live data is not easy to migrate.
   - Data in active applications is changing rapidly and thus cannot be easily migrated through backup and restore.
- Applications and infrastructure deployment is not automated.
   - Automation to redeploy is not available or not suitable.
- Applications contain hardcoded references.
   - Applications refer to specific IP or DNS or other addresses that make setting up a parallel deployment difficult.
   - Applications refer to specific service or user identities that are account-specific make moving to a new account difficult.
- Joining multiple VPCs with transit gateways can be complicated by problems with overlapping address spaces and poor network ACLs.

## Preparing for adoption
{: #prep}

After you select a strategy, check if any of the following prerequisite steps are required and completed.

- [ ] Construct a target enterprise account framework
- [ ] Build or customize any needed deployable architectures in preparation for hosting workloads
- [ ] Add existing workloads to {{site.data.keyword.cloud_notm}} projects for tracking
- [ ] Lay down common infrastructure
- [ ] Determine overall project schedule
- [ ] Ensure that backups for live systems are working and current

### Relevant capabilities
{: #capabilities}

Before you apply one of the technical strategies, it can be useful to become familiar with some of the relevant tools and capabilities in {{site.data.keyword.cloud_notm}}.

* [Import existing accounts into an enterprise](/docs/secure-enterprise?topic=secure-enterprise-enterprise-add&interface=ui#add-accounts).
* [Move accounts into different account groups](/docs/secure-enterprise?topic=secure-enterprise-enterprise-organize&interface=ui#move-accounts)
* [Database back up and restore to a different account to move databases](docs/cloud-databases?topic=cloud-databases-dashboard-backups)
* Database sync across accounts:
   * [{{site.data.keyword.cloudant}}](/docs/Cloudant?topic=Cloudant-replication-guide)
   * [{{site.data.keyword.cos_full_notm}}](/docs/cloud-object-storage?topic=cloud-object-storage-rclone)
   * [{{site.data.keyword.databases-for-mongodb}}](https://www.ibm.com/cloud/blog/easier-migrations-from-compose-for-mongodb-to-ibm-cloud-databases){: external}
   * [{{site.data.keyword.databases-for-postgresql}}](https://www.ibm.com/cloud/blog/upgrading-ibm-cloud-databases-for-postgresql-with-minimal-downtime){: external}
   * [{{site.data.keyword.messagehub}}](/docs/EventStreams?topic=EventStreams-mirroring)
   * [{{site.data.keyword.databases-for-elasticsearch}}](docs/databases-for-elasticsearch?topic=databases-for-elasticsearch-esmigration-elasticsearch-snapshot-restore)
   * [{{site.data.keyword.databases-for-redis}}](/docs/databases-for-redis?topic=databases-for-redis-upgrading&interface=ui#upgrading-req-data-migration)
* Configure a redundant [{{site.data.keyword.keymanagementserviceshort}} instance for HA](/docs/key-protect?topic=key-protect-ha-dr#application-level-high-availability) and handling [cross-region or cross-account restore](/docs/hs-crypto?topic=hs-crypto-ha-dr#cross-region-disaster-recovery) for {{site.data.keyword.hscrypto}}.
* To follow an Infrastructure as Code (IaC) approach, resources need to be re-created by using automation within the new account structure. You can easily embrace this strategy by using {{site.data.keyword.cloud_notm}} projects, which rely on automation to create resources.
* Use [deployable architectures](/docs/secure-enterprise?topic=secure-enterprise-what-are-deployable-architectures) to create new compliant infrastructure.
* [Terraformer](https://cloudacademy.com/course/infrastructure-to-code-with-terraformer-1135/what-is-terraformer/) can be used to get a start on building a deployable architecture for existing resources.
* Manual resources and bulk resource tagging by using projects.
* Import an existing schematics workspace into a project.
* [Onboard a deployable architecture](/docs/secure-enterprise?topic=secure-enterprise-onboard-custom&interface=ui) to the catalog for sharing.

## Implementing transition strategies
{: #migrate}

Implement one or more of the technical strategies to adopt the enterprise architecture. The pros and cons of each strategy are included.


### App by app migration
{: #app-app}

With this strategy, a single application or family of related applications is migrated to a set of workload accounts, which exist in parallel with the existing infrastructure for the application. After the migration is complete, unused infrastructure in the original accounts can be decommissioned.

![app-by-app diagram](./images/app-by-app.svg){: caption="App by app migration" caption-side="bottom"}

1. Select a workload for migration and add related resources to a project in preparation for tracking resources during migration.
1. Update the workload as needed to make it configurable and able to run in all locations. These updates might involve code changes to parameterize hostnames, URLs, IP addresses, and ports.
1. Deploy infrastructure as needed in the [nonproduction and production workload](/docs/enterprise-account-architecture?topic=enterprise-account-architecture-infra-account) accounts by deploying architectures from projects that are hosted in the [business unit hub account](/docs/enterprise-account-architecture?topic=enterprise-account-architecture-bu-admin-account). Ensure that appropriate access, networking, and dependencies are in place as part of the infrastructure setup.
1. Configure delivery pipelines to deploy the application to both the original and new infrastructure such that application deployment is synchronized in both environments.
1. Migrate data by backing up, restoring, and syncing all related data from the original data storage or service. If periodically migrating data, this step might need to be repeated before applications are activated on the new infrastructure.
1. Test the new deployment, update the infrastructure and application, and return to step 2 or 3 as needed.
1. Activate applications on the new infrastructure. For example, update DNS records and load balancer. Consider routing only a percentage of traffic to start if data can be synced live. Ensure that a failback is available in case issues occur.
1. Decommission any unused resources from the original deployment. Use the project configuration from the preparation phase to help locate these resources and complete bulk operations.

This strategy is low risk and gains all of the cost and operation savings that are associated with shared infrastructure and IaC managed workload accounts. Using parallel infrastructure allows for a smooth transition and easy failback should problems occur. However, this approach does temporarily double infrastructure costs and can be slow to run. Also, data sync and infrastructure migration can be difficult. In addition, data services encrypted with BYOK might have extra concerns with migration. For more information about data migration, see [relevant capabilities](#capabilities). Despite these drawbacks, this workload migration strategy is likely the best for most organizations.
{: note}

### Piecemeal migration (nonproduction)
{: #piecemeal-non-production}

With this strategy, [nonproduction workloads](/docs/enterprise-account-architecture?topic=enterprise-account-architecture-infra-account) are moved into separate workload accounts.

![piecemeal migration of nonproduction resources](./images/piecemeal-nonprod.svg){: caption="Piecemeal migration of nonproduction resources" caption-side="bottom"}

Options:
* Use the same process as [app by app migration](#app-by-app-migration), but migrate only nonproduction workloads.  Because nonproduction workloads don't typically have critical data, it might not be necessary to migrate data and even if it is, a period of downtime during the migration can often be much easier to manage.
* Bulk migrate your nonproduction workloads to new infrastructure. This is a similar process to [app by app migration](#app-by-app-migration), but the infrastructure for a group of nonproduction workloads is deployed and those workloads are switched to deploy to that infrastructure all together. Bulk migration is most appealing if data migration is not required.

Migrating nonproduction workloads into a separate account from production workloads provides an important separation of concerns, making it easier to ensure that users and processes don't accidentally operate against the wrong data or service. Moving only nonproduction workloads eases data migration concerns and further reduces risk as production isn't touched. This strategy works well combined with [Transform in place](#transform-in-place) for the production workloads.
{: note}

### Piecemeal migration (networking and shared services)
{: #piecemeal-network}

![piecemeal migration of network and shared services](./images/piecemeal-network.svg){: caption="Piecemeal migration of network and shared services" caption-side="bottom"}

With this strategy, [networking and shared services](/docs/enterprise-account-architecture?topic=enterprise-account-architecture-hub-account) are set up in a new account and then linked to existing workload accounts, which creates a hybrid architecture. This strategy works well with [piecemeal migration of nonproduction](#piecemeal-migration-non-production) and isn't required when using [app-by-app migration](#app-by-app-migration) as a duplicate set of these services can be used instead.

1. Add any existing networking and shared services to appropriate projects in the central administrative account in preparation for tracking resources during the migration.
1. Deploy new networking and shared services in the new network and services hub account according to the enterprise architecture. You must also assign appropriate access.
1. [Export transit gateway](/docs/transit-gateway?topic=transit-gateway-ha-dr#disaster-recovery) information and [direct link](/docs/dl?topic=dl-ha-dr#disaster-recovery-dl) information from any existing deployment of those services.
1. Configure the new transit gateway to use a direct link connection.
1. Configure the direct link, by using knowledge from previous direct link
1. Use exported transit gateway information to connect existing VPCs in the original accounts to the new transit gateways.
1. Setup required keys in HPCS or KeyProtect for any BYOK protected services that you require. If existing BYOK-protected services are being retained, this involves reimporting key material and updating the configuration of those BYOK-protected applications as described [here](/docs/key-protect?topic=key-protect-ha-dr#application-level-high-availability).
1. Optionally, migrate any shared applications following an application migration pattern.
1. Decommission original networking and shared services by using projects to locate redundant resources and support bulk operations.

Existing VPCs might have overlapping addresses that conflict with a flat network design. You must resolve overlapping addresses before implementing the flat network described in the enterprise architecture.  This strategy is often best used after separating nonprod from production workloads so that these network changes can be tested with nonproduction workloads. Migrating Key Protect and Hyper Protect Crypto Services to a new account to be used by existing services with KYOK is challenging and might not be possible for all services. Consider leaving existing BYOK protected data services unchanged and using only the new instances of Key Protect/HPCS to protect new data services.
{: note}


### Piecemeal migration (identity and access management)
{: #piecemeal-iam}

With this strategy, identity and access management (IAM) is configured in new accounts to support existing user's job functions. This strategy works well with app by app migration.

1. Analyze existing access groups, access policies, and trusted profiles to determine which groups of users are permitted which general access. Use IAM [audit reports](/docs/account?topic=account-iam-audit-policies&interface=ui) as needed.
1. Analyze these groups of users to determine their job functions, for example, developer, operations, or finance.
1. Map those job functions into access policies tied to access groups within the enterprise architecture.
   The enterprise architecture uses an Infrastructure as Code (IaC) approach, so users don't have direct write access to resources. Instead, users have write access to projects, which are used to deploy and update resources.
   {: note}

1. Update deployable architectures so that the correct access groups are provisioned, trusted profiles are created, and so on. This should include all workload accounts and administration accounts to make sure that users have the correct access for their job functions.

Do not migrate existing access directly into the new architecture, as best practices for access needs to be adopted as a part of this transition. Use trusted profiles, access groups, and projects as a means to create and update resources. The results of adoption are better governance, security, and ease in understanding user access.
{: note}

### New applications only
{: #new}

![new applications only diagram](./images/new-only.svg){: caption="New applications" caption-side="bottom"}

This strategy doesn't attempt to transition existing applications. Rather, it builds out parallel infrastructure for the workload accounts and deploys new applications into that environment. This strategy can be combined with a [transform in place](#transform-in-place), and potentially some piecemeal migration of major common functions like networking and access management.

1. Existing applications remain in place. (option) Consider [transform in place](#transform-in-place) for these.
1. Newly developed or newly migrated to cloud applications are deployed to new [workload accounts](/docs/enterprise-account-architecture?topic=enterprise-account-architecture-infra-account) in alignment with the Enterprise Architecture recommendations.

This strategy is safe and easy, but does not attempt to address existing applications and workloads. The [Enterprise Architecture benefits](./understand#justifying-a-change) will only apply to new applications.
{: note}

### Transform in place
{: #transform-in-place}

With this strategy, data migrations are avoided and existing accounts and resources are refactored to better align with enterprise architecture recommendations. Certain common operations need to be considered, but the exact refactoring operations depend on your enterprise's starting point, resulting in various substrategies.

![transform in place diagram](./images/transform-in-place.svg){: caption="Transform in place" caption-side="bottom"}

*[Adopt Infrastructure as Code](/docs/enterprise-account-architecture?topic=enterprise-account-architecture-principles)*

Move from manual resource management to using infrastructure as code, deployable architectures, projects, and schematics to deploy and update resources.
1. Create deployable architectures to manage your existing resources. Use Terraformer to reverse-engineer existing resource deployments into terraform automation and terraform state.  Generated terraform and any previously existing terraform can be used to help create deployable architectures. See [relevant capabilities](./prep#relevant-capabilities) for more information.
1. Create a series of projects in an [administrative account](/docs/enterprise-account-architecture?topic=enterprise-account-architecture-bu-admin-account) that's separate from your workload accounts. These projects are used to maintain the existing infrastructure by using {{site.data.keyword.cloud_notm}} project governance.
1. Restrict access to existing resources so that changes can be made only by using projects.

This strategy allows existing workloads to continue to run unchanged, but shifts into an Infrastructure as Code mode of operation that is better governed and more repeatable. To reduce risk, new IaC should be used to update nonproduction workloads before production.
{: note}

*[Separate production and nonproduction](/docs/enterprise-account-architecture?topic=enterprise-account-architecture-principles#dev-and-prod)*

An alternative to [migrating nonproduction](#piecemeal-migration-non-production) to new accounts is to use access groups, resource groups, tags, and naming conventions to separate nonproduction workloads from production workloads.

1. Identify all nonproduction and production resources and apply a "nonproduction" tag and a "production" tag to ensure visibility. Also consider adding a prod or nonprod prefix or suffix to the name of all resources.
1. Apply access tags to nonproduction and production resources or use existing resource groups if they happen to properly separate nonprod and prod. Resource groups can also be renamed with and prefix or suffix to make their role clear.
1. Adjust the access policies so that users have access to nonproduction, but have limited access to production.

This strategy provides some of the benefits of the recommended nonprod prod separation, but is not as safe over the long run that is compared with separated accounts. Consider [migrating to nonproduction](#piecemeal-migration-non-production) for increased safety.
{: note}

*[Designate shared compute infrastructure](/docs/enterprise-account-architecture?topic=enterprise-account-architecture-principles#shared-infrastructure)*

Rather than hosting every application on dedicated compute (and potentially DB) resources, designate selected existing compute infrastructure for shared hosting.  Shared infrastructure saves in hosting and operational costs.
1. Designate selected existing compute infrastructure (for example Red Hat OpenShift Clusters) as shared resources
1. Reorganize so that a single team can manages the shared infrastructure.
1. Make any adjustments required to allow the compute infrastructure to be suitable for hosting multiple applications. This might require introducing namespaces in Kubernetes clusters or load balancer pools for VSI clusters.
1. Deploy new workloads onto the existing clusters.  (optional) Consider consolidating some existing workloads onto the shared infrastructure.

This strategy provides many of the shared infrastructure benefits, although it may not be quite an elegant and easy to manage as new compute infrastructure designed specifically for shared use.
{: note}

*[Separate backup infrastructure](/docs/enterprise-account-architecture?topic=enterprise-account-architecture-bcdr#backups)*

Adjust existing data services and applications to send their backups to a separate account for maximum isolation.

1. Create a separate account to store backups with limited user access.
1. Adjust backup automation to ensure that backups are stored in a separate region and in the backup account, where possible.
1. Decommission older backups after they are no longer required.


*[Hub and spoke networking](/docs/enterprise-account-architecture?topic=enterprise-account-architecture-hub-account)*

Refactor the networking to align with the hub and spoke network strategy.
1. Designate the account that currently contains the direct link connection as the network hub account.
1. Connect VPCs to the direct link by using transit gateway in the hub account. This might involve removing transit gateways that are located elsewhere.

This strategy provides most of the network simplification benefits that are described in the Enterprise Architecture, although it might not be quite an elegant and easy to manage as when core network services are provisioned in a central account.
{: note}

### Hybrid (database in place)
{: #hybrid}

The hybrid strategy leaves your existing databases and data services in place, while you migrate applications and nondata services into the new architecture:

![hybrid strategy diagram](./images/hybrid.svg){: caption="Hybrid strategy" caption-side="bottom"}

1. Leave databases and other data services in place, adjusting only access permissions to align with enterprise architecture recommendations.
1. Migrate the applications and nondata services into the enterprise architecture structure by following any of the strategies that are outlined in this white paper. The [App by App](#app-app) strategy is recommended.
1. Configure/update any access policies and context-based restrictions necessary to allow your application to reach the data services across accounts.

This strategy avoids potentially risky data migrations while realizing the benefits of Application workload consolidation, but results in a slightly more complex account architecture as data services are not collocated with their applications. As a result extra care must be taken with access policy and context-based restrictions to ensure that only data services can be accessed appropriately.
{: note}

## Evaluating the transition
{: #evaluate}

Before you decommission any redundant infrastructure post transition, a rigorous evaluation should be performed to ensure that everything is operating as expected.

1. Test workloads in target deployment.
1. Test user access and processes, ensure run-books are updated.
1. Ensure that data is synchronized.
1. When parallel infrastructure is used, begin a gradual cut-over by allocating a percentage of traffic to new deployment if possible.
1. Scale up to support full workload.
1. Complete cut-over and run for burn in period.
1. Decommission any redundant infrastructure.
