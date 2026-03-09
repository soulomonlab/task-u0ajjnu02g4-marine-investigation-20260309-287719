# Feature: Marine Investigation
**Goal:** Provide investigators an integrated platform to ingest, analyze, and report on marine incidents (collisions, pollution events, vessel tracking anomalies) with an intuitive UX and scalable backend.

**North Star Impact:** Reduce time-to-insight for marine incident investigations by 60% for operational users.

**Users:**
- Maritime Safety Investigators: review incident timelines, sensor logs, and generate reports.
- Analysts: correlate AIS/vessel telemetry, sensor data, and eyewitness reports.
- Ops teams: monitor active incidents and triage urgent events.

**RICE Score:** Reach=2000 × Impact=2 × Confidence=70% / Effort=4w = 700

**Kano Category:** Performance

**Acceptance Criteria:**
- [ ] Investigator can create a new investigation record with metadata (location, time, vessel IDs).
- [ ] System can ingest and store bulk telemetry logs (AIS, GPS, sensor CSV) and associate them with an investigation.
- [ ] Investigator can view an interactive timeline and map of events for an investigation (pan/zoom, event drilldown).
- [ ] Investigator can filter events by time range, vessel ID, event type, and sensor source.
- [ ] Investigator can generate/export a PDF or CSV summary report of an investigation.
- [ ] Backend ingestion supports 10k events/day with horizontal scale; query latency for dashboard views < 200ms p95 for typical queries.
- [ ] Authentication & authorization: only authorized investigator roles can access investigations.
- [ ] Edge case: partial upload (network interruption) resumes or reports clear error with retry token.

**Out of Scope:**
- Automated root-cause ML analysis / anomaly detection (future phase).
- Mobile native client (web-only for initial release).

**Success Metrics:**
- Time-to-first-insight (median) reduced from baseline to <= 30 minutes per investigation.
- Adoption: 60% of active investigators use the tool for new incidents within first quarter.
- Reliability: ingestion error rate < 0.5% and dashboard p95 latency < 200ms.

**GitHub Issue:** TBD
