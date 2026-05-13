# Amazon 2023 CIS - 26th June 2023

## 1.3.0 based on v1.0.0 - Branch 2026_MAY_QA

- 2026_MAY_QA branch
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
  - Removed stale workflow files
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
  - initial release

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
