---
layout: page
title: Analytics
permalink: /analytics/
---

# Analytics Setup Guide

This site supports Google Analytics 4 (GA4) for tracking visitor behavior and engagement.

## Setup Instructions

### 1. Get Your Google Analytics 4 Measurement ID

1. Go to [Google Analytics](https://analytics.google.com/)
2. Create a new property (or use existing)
3. Get your Measurement ID (format: `G-XXXXXXXXXX`)

### 2. Add to _config.yml

```yaml
google_analytics: G-XXXXXXXXXX
```

### 3. What's Tracked

The implementation automatically tracks:
- **Page Views**: Every page visit
- **Scroll Depth**: 25%, 50%, 75%, 100% milestones
- **Outbound Links**: Clicks on external links
- **File Downloads**: PDF, ZIP, DOC file downloads
- **Engagement Metrics**: Time on page, bounce rate

### 4. Privacy Compliance

- No personal data is collected
- IP addresses are anonymized
- Complies with GDPR (when configured in GA)
- Users can opt-out via browser extensions

### Alternative: Privacy-Focused Analytics

For a more privacy-focused solution, consider:
- **Plausible Analytics**: Privacy-first, no cookies
- **Umami**: Self-hosted, open-source
- **Simple Analytics**: GDPR compliant

To use an alternative, replace the analytics.html include with your preferred solution.

