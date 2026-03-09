# Feature: Marine Investigation Module

**Goal:**
Provide a structured product feature to investigate marine incidents (e.g., vessel collisions, pollution events, search & rescue cases) enabling investigators to collect evidence, track case timeline, assign tasks, and generate reports—while ensuring an intuitive UX, backend scalability, and maintainable code.

**North Star Impact:**
Reduce time-to-resolution for marine incidents and increase investigator satisfaction (target: investigator task completion rate > 60% within first month of launch).

**Users:**
- Marine Investigator (primary persona): needs to log incidents, attach evidence (photos, GPS tracks), assign follow-ups.
- Operations Manager: needs dashboards and case-status reporting.
- External Stakeholders (port authority, insurers): receive exported reports.

**RICE Score (initial estimate):**
- Reach = 1,000 users / quarter
- Impact = 2 (performance)
- Confidence = 70%
- Effort = 3 person-weeks
- RICE = (1000 × 2 × 0.70) / 3 ≈ 467

**Kano Category:** Performance

**Acceptance Criteria:**
- [ ] Investigator can create a new incident case with title, location (lat/lon), timestamp, and category.
- [ ] Investigator can upload multiple evidence items (images, video links, GPX/KML tracks) with metadata (uploader, timestamp, tags).
- [ ] System stores evidence in scalable object storage (S3-compatible) and returns secure URLs; DB stores references only.
- [ ] Investigator can add chronological timeline entries and mark tasks as open/in-progress/done.
- [ ] Operations Manager can view a dashboard of open cases filtered by region, status, and severity.
- [ ] System can export a PDF incident report (summary + selected evidence thumbnails) for stakeholders.
- [ ] API response times for read operations under typical load: median < 200ms; 95th percentile < 500ms.
- [ ] Data retention and deletion: evidence older than policy window can be archived; deletion requests remove DB references and trigger object deletion.
- [ ] Role-based access control enforced: investigators vs. ops vs. external viewers.

**Out of Scope (initial MVP):**
- Real-time vessel telemetry ingestion (streaming AIS) — spike required later.
- Machine-learning based image forensics/auto-tagging.
- Multi-language localization (English-only MVP).

**Success Metrics:**
- Feature adoption: % of investigators who create ≥1 case within 30 days (target > 60%).
- Time-to-resolution: median days to close a case (target: -15% vs baseline).
- System reliability: error rate < 1% and evidence upload success rate > 99%.
- Performance: median API read latency < 200ms under 95th percentile load.

**Data & Compliance Notes:**
- Evidence storage must support encryption-at-rest and fine-grained ACLs.
- Consider PII handling for witness details; include consent capture in form.

**Technical Spike Requests (first 1-week spike):**
- Validate S3-compatible object storage integration and signed URL flows.
- Prototype DB schema for Cases, Evidence, TimelineEntries, Tasks, and Roles.
- Estimate cost/throughput for evidence storage at scale (1TB/month ingestion scenario).

**Next Steps:**
- Create GitHub issue and assign technical spike to backend. Draft API surface and DB schema after spike.

**Files:**
- Spec: output/specs/marine_investigation.md
- GitHub Issue: TBD

**Related project goals:** Build intuitive UX; Ensure backend scalability; Maintain code quality.
