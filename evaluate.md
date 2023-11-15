---

copyright:
  years: 2023
lastupdated: "2023-11-15"

subcollection: adopt-enterprise-architecture

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Evaluating the transition
{: #evaluate}

Before you decommission any redundant infrastructure post transition, a rigorous evaluation should be performed to ensure that everything is operating as expected.

1. Test workloads in target deployment.
1. Test user access and processes, ensure run-books are updated.
1. Ensure that data is synchronized.
1. When parallel infrastructure is used, begin a gradual cut-over by allocating a percentage of traffic to new deployment if possible.
1. Scale up to support full workload.
1. Complete cut-over and run for burn in period.
1. Decommission any redundant infrastructure.
