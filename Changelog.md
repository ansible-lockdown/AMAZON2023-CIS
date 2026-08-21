# Amazon 2023 CIS - 26th June 2023

## 1.3.1 based on v1.0.0

- Aug26_align branch
  - 6.2.1: stdout_line typo, pwconv remediation added, block retagged PATCH (addresses #179) - Thank you @mariot8
  - 5.2.3.6: var prefix and empty exclude filter fixed, privileged command rules now generated (addresses #181) - Thank you @bjammal
  - 5.2.1.3: correct registered var used, audit=1 no longer dropped (addresses #182) - Thank you @bjammal
  - ipv6 logic fixed #183 thansk to @bjammali
  - 1.3.1: AIDE db build gated on exists/age, async race removed
  - 4.4.1: changed_when no longer overrides creates
  - Section 1.1: mount options accumulate instead of replacing fstab options
  - Section 1.1: prelim mount facts, remount_tmp.yml and paired mount handlers added
  - Audit bridge template renamed lockdown_audit.yml.j2
  - Added missing audit_bin_validate_certs
  - Bridge template: ssh and faillock vars no longer hardcoded
  - 1.2.4: yum.conf -> dnf.conf
  - ansible_facts bracket notation applied
  - tmp.mount.j2: managed-by-Ansible header and typo
  - Linting: .yamllint key fixed, .pre-commit-config indentation
  - Idempotency verified on host: 147 -> 4 -> 2 changed over three runs
  - audit benchmark renamed to 1.0.0 droping the v
  - audit goss location moved to krameff
  - ansible dot notation replaced
  - set -o pipefail and args executable added to all piped shell tasks (110 changes, 51 lint findings -> 1)
  - amzn2023cis_shell_executable added to vars, replacing undefined default_shell references
  - authselect profile check: rc 2 accepted, authselect exits 2 when no profile is selected and pipefail stopped masking it
  - Workflows: actions/checkout v6.0.2 -> v7.0.0
  - README: Twitter badge migrated to X
  - .gitignore: prompt.md and test_inv added
  - 1.4.1: grub file modes octal -> symbolic, when moved above loop
  - post.yml: tags added to Update sysctl
  - Removed orphans: check_prereqs.yml, aide.cron.j2, crypt_audit_procs.conf.j2, 4 unused handlers
  - README updates and updated contributing and contributors

## 2026_MAY_QA2

- 2026 May follow-up QA pass
  - Fixed warn_control_id placement: moved from block level to task level in 19 locations (post.yml, cis_1.1.2-8.x, cis_1.2.x, cis_1.6.1.x, cis_2.4.yml, cis_3.4.2.x, cis_4.6.1.x, cis_5.1.2.x, cis_6.2.x)
  - Fixed 1.1.8.1 subtask title: was "Ensure separate partition exists for /home" (copy-paste from 1.1.7.1), now "Ensure /dev/shm is a separate partition"
  - Fixed 2.2.12 subtask typo: "smpd" -> "snmpd" in two subtask titles
  - Fixed 2.2.18 subtask inconsistency: "rsync service" -> "rsyncd service" in one subtask title
  - Added update_audit_template: false and default_shell: /bin/bash to public AMAZON2023-CIS/vars/main.yml
  - Rule coverage: 243/243 (100%)
  - QA tools: 0 issues (coverage, var_naming, register_order, yamllint)
  - Cross-repo: 14 PASS / 0 FAIL / 3 WARN (no regressions from prior pass)

## 1.3.0 based on v1.0.0

- Full QA pass with automated tooling and molecule testing
- Fixed min_ansible_version: 2.10.1 -> 2.16.1 (meta/main.yml and vars/main.yml)
- Fixed company name casing: MindPoint Group - A Tyto Athene Company (meta, vars, LICENSE)
- Added missing toggle: amzn2023cis_rule_6_1_13 (Ensure SUID and SGID files are reviewed)
- Created vars/is_container.yml with comprehensive container-incompatible rule list
- Fixed container detection: added community.docker.docker connection type
- Fixed SSH handler: added sshd -t validation before restart using listen chain
- Fixed handler register order: register before failed_when/changed_when
- Fixed register order in tasks (cis_1.2.x, cis_1.6.1.x, cis_5.1.1.x)
- Fixed file mode inconsistencies: octal and absolute symbolic modes to relative
- Fixed SSH allowusers when clause for container/root environments
- Added container guard to Restart auditd handler
- Removed export_badges_public.yml from private repo workflows
- Removed duplicate Changelog.md (standardized on CHANGELOG.md)
- Removed incorrect galaxy_tags (stig, disa) from meta/main.yml
- Created molecule scenarios (default, localhost, wsl)
- Molecule converge passing with audit enabled
- Idempotency verified (second run changed=4, audit-related only)
- Audit results: 322 tests, 19 failures (container-skipped rules)
- Fixed handler notify mismatch: added listen: Restart auditd to auditd handler
- Fixed amzn2023cis_pam_faillock dict notation to flat vars in cis_4.4.x.yml
- Fixed hardcoded amzn2023cis_rule_2_4: true in goss template
- Added amzn2023cis_rule_6_1_13 to goss template
- Fixed missing handler "update auditd" notify reference in cis_5.2.3.x.yml
- Fixed rule 5.2.3.18 changed_when -> when clause
- Added crond to molecule prepare service start list
- Fixed 1.7.2/1.7.3: write directly to /etc/issue and /etc/issue.net as regular files (Amazon Linux ships these as symlinks to /usr/lib/ which report mode 777 in goss)
- Fixed 1.7.5/1.7.6: permission tasks now target /etc/ paths per CIS benchmark
- Fixed 6.1.x off-by-one shift: renumbered 6.1.2-12 to 6.1.3-13, added new 6.1.2 for CIS duplicate /etc/passwd entry (addresses #162)
- Rule coverage: 243/243 (100%)
- Cross-repo: 14 PASS / 0 FAIL / 3 WARN
- Audit results: 322 tests, 20 failures (container-skipped rules)
- Fixed 4.6.6 root password check: accepts any encryption method, not just SHA512 (addresses #172) — Thank you @dean-kirby

## 1.2.8 based on v1.0.0

- March26_align branch
  - Version alignment updated
  - Naming and company name updates
  - Titles updated for alignment
  - Default settings added
  - 2.2.18: tidy up legacy var
  - Linting applied
  - Audit: version update, latest versions aligned
  - Audit: separated fails, YAML headers
  - Audit: removed legacy setting and content
  - lint updates
  - title and meta alignment
  - audit sync on vars naming
  - 4 -> 2 spacing
  - var renaming to remove sub options for easier var override
  - initial private release

## 1.2.7 based on v1.0.0

- 2026 Jan Updates
  - QA and linting fixes
  - Fixed spelling errors in README.md, CONTRIBUTING.rst, and task files
  - Updated .ansible-lint config to remove deprecated options
  - Updated .yamllint config to use consistent spacing (matches repo style)
  - YAML lint passing
  - Update ReadMe

## 1.2.4 based on v1.0

- 2025 Oct
  - Improvements and QA Fixes
  - #135 thanks to @gee-mo
  - workflow updates
  - audit updates
  - new files and logic
  - max-concurrency added
  - linting and alignment
  - variable standards updated
  - new readme added
  - addresses #140, Thank you @joffotron

## 1.0.2 based on v1.0

- #13 addressed
- #75
- #82

- audit updated removed jmespath dependency and improved functionality
- workflows updated to improved mechanism
- pre-commit updates

## 1.0.1

- thanks to @DianaMariaDDM
  - #59
  - #60
  - #61
  - #62

- #64 thanks to @tom-henderson

- extended with new options to force changes for 4.6.1.1|2|3 default false
  - amzn2023cis_force_user_maxdays
  - amzn2023cis_force_user_mindays
  - amzn2023cis_force_user_warndays

- pre-commit updates

- general tidy up

## 1.0 Multiple changes

- Audit binary updated goss 0.4.4
- audit_only option now added
  - audit_only: true

- Many Prs and associated issues
  massive thanks to @DianaMariaDDM for all the PRs and Issues and time

## 0.91

- issue #2 thanks to @babinskiy
- moved to self hosted action after forking from arillso

## Initial release 0.9
