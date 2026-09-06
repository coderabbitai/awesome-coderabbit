# Start here: Pre-Merge Checks

Pre-merge checks answer one question before code lands: **Does this pull request
meet our standards?** CodeRabbit evaluates them whenever a pull request opens or
updates and reports a pass, failure, or inconclusive result with an explanation.

This folder contains ready-to-adapt packs for common engineering and industry
risks. They are starting points, not universal rules or compliance
certifications.

## Use a pack

1. Enable CodeRabbit's built-in checks for PR titles, descriptions, linked issue
   alignment, and docstring coverage where they fit your workflow.
2. Browse the packs and select only the individual checks that match your
   policies. Mix checks from different files as needed.
3. Adapt their paths, terminology, exceptions, and enforcement modes to the
   repository.
4. Add selected checks in **Settings → Pre-merge checks**, or copy their entries
   into `reviews.pre_merge_checks.custom_checks` in the existing
   `.coderabbit.yaml`. Do not replace unrelated configuration.
5. Consider starting copied checks in `warning` mode while the team evaluates
   false positives and inconclusive results. Promote a check to `error` only
   after it is reliable for that repository. Blocking also requires
   request-changes workflow.

Test before saving with
`@coderabbitai evaluate custom pre-merge check --name <name> --instructions <instructions> --mode warning`.
Run all configured checks with `@coderabbitai run pre-merge checks`.

## Available packs

| Pack | Best for | Primary outcome |
| --- | --- | --- |
| [Security](.coderabbit-security.yaml) | Applications accepting external input or changing dependencies | Prevent injection, exposed credentials, broken object authorization, and dependency risk |
| [Multi-Tenant SaaS](.coderabbit-multi-tenant-saas.yaml) | Services that store or process customer data in shared systems | Prevent cross-tenant reads, writes, cache collisions, and background-job effects |
| [Fintech & Payments](.coderabbit-fintech.yaml) | Banking, checkout, billing, payout, ledger, and payment-integration code | Protect monetary correctness, retry safety, financial data, and transaction auditability |
| [Health Tech](.coderabbit-health-tech.yaml) | Applications that store, expose, or process patient and clinical data | Protect health data, record authorization, minimum-necessary responses, and auditability |
| [Infrastructure](.coderabbit-infrastructure.yaml) | Teams reviewing infrastructure, deployment, and product-readiness concerns | Check IaC versions, Helm locks, analytics, accessibility, and debug output |
| [Data Privacy](.coderabbit-data-privacy.yaml) | Teams shipping data pipelines and production configuration | Check pipeline validation and deployment-ready configuration |
| [Performance](.coderabbit-performance.yaml) | Applications with latency, throughput, or scaling concerns | Surface material algorithmic, query, allocation, and hot-path regressions |
| [PR Hygiene](.coderabbit-pr-hygiene.yaml) | Teams standardizing change communication | Surface breaking changes, missing design context, and stale documentation |
| [Testing](.coderabbit-testing.yaml) | Repositories where behavior changes require reviewable evidence | Check proportionate coverage, test isolation, and validation evidence |
| [Quality](.coderabbit-quality.yaml) | Teams enforcing shared implementation conventions | Check API consistency, error handling, imports, naming, and commit conventions |

## Know the boundaries

Custom checks inspect a secure, read-only workspace. They do not run the test
suite or build, inspect generated build artifacts, verify reviewer approvals, or
post inline review comments. Use CI, branch protection, and normal CodeRabbit
review instructions for those responsibilities.

See the CodeRabbit documentation for [built-in
checks](https://docs.coderabbit.ai/pr-reviews/pre-merge-checks) and [writing
custom checks](https://docs.coderabbit.ai/pr-reviews/custom-checks).

## Industry packs are safeguards, not certifications

An industry pack maps common engineering risks into checks that can be supported
by pull-request evidence. It cannot determine whether an organization complies
with a regulation or standard whose controls also cover people, processes,
runtime systems, vendors, and operations. Validate proposed checks with the
customer's security, privacy, and compliance owners before using them as merge
blockers.
