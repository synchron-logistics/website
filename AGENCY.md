# AGENCY.md — Omnia Agency Dashboard

## Overview

This site will eventually connect to the **Omnia agency dashboard** — a centralized management interface being built by the Omnia Marketing team.

The dashboard is not yet built. This file is a placeholder for the integration specification, which will be added once the dashboard architecture is defined.

---

## What the Integration Will Cover

When the Omnia dashboard is ready, the integration spec will document:

- How this site reports status and health metrics to the dashboard
- Authentication and API key management
- Any shared components or data schemas between client sites and the dashboard
- Deployment pipeline hooks
- Client-facing portal access (if applicable)

---

## Current Status

- Dashboard: **not yet built**
- Integration spec: **pending**
- No action required on this project until the spec is provided

---

## Notes for Future Development

- All client sites in the Omnia system follow the same `site.config.js` convention, which will serve as the primary data source for the dashboard
- The `modules` export in `site.config.js` will likely be used by the dashboard to understand which features are active per client
- When the integration is scoped, update this file with the full spec and link to relevant dashboard repository
