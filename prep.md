---

copyright:
  years: 2023
lastupdated: "2023-11-15"

subcollection: adopt-enterprise-architecture

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Preparing for adoption
{: #prep}

After you select a strategy, check if any of the following prerequisite steps are required and completed.

- [ ] Construct a target enterprise account framework
- [ ] Build or customize any needed deployable architectures in preparation for hosting workloads
- [ ] Add existing workloads to {{site.data.keyword.cloud_notm}} projects for tracking
- [ ] Lay down common infrastructure
- [ ] Determine overall project schedule
- [ ] Ensure that backups for live systems are working and current

## Relevant capabilities
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
