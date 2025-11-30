# fedora-asahi-srv-m1m

Production infrastructure on Fedora Asahi (Apple Silicon M1) demonstrating Infrastructure Engineering practices through professional documentation, automated operations, and tested disaster recovery.

**Not a tutorial.** Production-grade infrastructure running real services with documented architecture decisions, validated procedures, and quantified outcomes.

## Infrastructure Overview

**Hardware:** Mac Mini M1 (16GB RAM, ARM64)  
**OS:** Fedora Asahi Linux 40  
**Storage:** 9TB Qwiizlab UH25 Pro (Btrfs, 7.3TB usable, tiered SSD cache)  
**Network:** Localhost-only services (zero external exposure without explicit proxy)

**Services in Production:**
- **Forgejo** - Git hosting (localhost:3000), mirrored to GitHub
- **Vaultwarden** - Password/secrets vault (localhost:8222), PostgreSQL backend
- **Syncthing** - File synchronization (localhost:8384)
- **Ollama** - Local LLM inference (localhost:11434)

## What This Demonstrates

**For Infrastructure/Platform Teams:**

Production infrastructure maturity with 4 services on 9TB tiered storage. Zettelkasten documentation with automated drift detection. Tested disaster recovery procedures with documented RTO/RPO. Professional standards governance via STANDARDS.md.

**Architecture Decisions:**
- Tiered storage design (USB bandwidth vs capacity trade-offs documented)
- Localhost-first security model (systemd sandboxing, zero external exposure)
- Atomic documentation pattern (scales to 1000+ entries without degradation)
- Local-first workflow (Forgejo → sanitize → GitHub demonstrates operational maturity)

## Key Features

### Production Infrastructure
- 7.3TB usable storage with validated performance metrics
- systemd hardening (sandboxing, restricted capabilities, read-only filesystems)
- Pre-commit security scanning (detect-secrets baseline)
- Health monitoring (hourly service checks, logged to /var/log/service-health.log)

### Documentation as Infrastructure
- Atomic unit pattern (00-01-02-03 Zettelkasten structure)
- Real-time drift detection via `audit-docs.sh` automation
- STANDARDS.md as immutable governance source
- AI-parseable structure (MOC indexing, dated entries)

### Disaster Recovery
- Automated daily backups (PostgreSQL, Forgejo, system configs)
- 30-day retention with automated cleanup
- Tested restore procedures: RTO <30min, RPO <24hrs
- Recovery validated quarterly against real backups

### Infrastructure as Code
- Ansible playbooks for complete stack: [ansible-playbooks](https://github.com/ch1ch0-FOSS/ansible-playbooks)
- Bare metal to production in 30 minutes
- Reproducible across environments
- Role-based organization with proper error handling

## Repository Structure

documentation/
├── STANDARDS.md # Immutable governance rules
├── SYSTEM-SPEC.md # Hardware/software baseline
├── RUNBOOK.md # Operational procedures
├── WORKFLOW.md # Human-AI cooperation protocol
├── ROADMAP.md # Phase status and strategy
├── AI-HANDOFF-MANIFEST.md # AI session context
└── phases/ # Project lifecycle (atomic pattern)
├── PHASE-5-STAGING.md # Current: Portfolio completion
└── completed/ # Historical phases

automation/
└── scripts/
├── audit-docs.sh # Drift detection (validates cross-references)
└── batch-fix-docs.sh # Auto-correction

infrastructure/
└── services/ # Per-service configurations
├── forgejo/
├── vaultwarden/
├── syncthing/
└── ollama/

toolkit/ # CLI tools configuration (11 total)


## Documentation Standards

All documentation follows Zettelkasten atomic pattern:

directory/
├── 00-README.md # How to use this directory
├── 01-MOC.md # Map of contents + archive metadata
├── 02-TYPE.tpl # Template for new entries
├── 03-INDEX.md # Current entries (refreshed regularly)
└── YYYY-MM-DD-*.md # Atomic dated entries

**Backup Verification:**

systemctl list-timers | grep backup
cat /var/log/service-health.log | tail -20

**Service Status:**

systemctl status forgejo vaultwarden syncthing ollama


## Related Repositories

| Repository | Purpose | Link |
|------------|---------|------|
| **ansible-playbooks** | IaC automation for complete stack deployment | [View](https://github.com/ch1ch0-FOSS/ansible-playbooks) |
| **disaster-recovery** | Backup/restore procedures and tooling | [View](https://github.com/ch1ch0-FOSS/disaster-recovery) |
| **dotfiles** | Operator toolkit configuration (11 CLI tools) | [View](https://github.com/ch1ch0-FOSS/dotfiles) |
| **infra-case-studies** | Technical narratives explaining design decisions | [View](https://github.com/ch1ch0-FOSS/infra-case-studies) |

## For Infrastructure Engineers

**Understand the architecture:**

cat documentation/SYSTEM-SPEC.md

**Review operations manual:**

cat documentation/RUNBOOK.md

**Inspect governance:**

cat documentation/STANDARDS.md

**See the patterns:**

tree documentation/phases/ # Zettelkasten structure

**Run validation:**

bash automation/scripts/audit-docs.sh

## For Developers

**Check out governance:**

cat documentation/STANDARDS.md

**Understand workflow:**

cat documentation/WORKFLOW.md

**Review phase status:**

cat documentation/phases/PHASE-5-STAGING.md

**Explore services:**

ls infrastructure/services/

## For AI Instances

See `documentation/AI-HANDOFF-MANIFEST.md` for context requirements per session.

**Load critical files first:**
1. SYSTEM-SPEC.md (hardware baseline)
2. STANDARDS.md (governance rules)
3. WORKFLOW.md (cooperation protocol)
4. AI-HANDOFF-MANIFEST.md (context checklist)
5. ROADMAP.md (phase status)

## Technologies

**Infrastructure:** Linux (Fedora Asahi ARM64), systemd, Btrfs, Docker  
**Services:** Forgejo, Vaultwarden, PostgreSQL, Syncthing, Ollama  
**DevOps:** Bash, Git, Ansible, systemd timers  
**Documentation:** Markdown, Zettelkasten pattern, drift detection  
**Security:** SSH hardening, secret scanning, systemd sandboxing, SELinux

## Why srv-m1m?

`srv` = server | `m1` = Mac Mini M1 | `m` = project identifier

Production infrastructure project demonstrating professional operations practices, standards-driven development, and infrastructure engineering thinking.

## License

MIT

---

**Last Updated:** 2025-11-30  
**Next Review:** 2025-12-06 (end of Phase 5 Week 1)


