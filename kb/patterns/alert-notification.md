---
title: Alert and Notification Pattern
type: pattern
language: en
last_compiled: 2026-04-02
sources:
  - kb/raw/industry-templates.md
freshness: current
tags:
  - alerts
  - notifications
  - event-driven
  - cross-vertical
verticals:
  - mining
  - investment-advisory
  - insurance-surety
  - auctions
---

# Alert and Notification Systems (Event-Driven Alerting)

Event-driven alerting is the delivery layer that makes all other patterns actionable. Compliance deadlines, model predictions, document processing results, and entity state changes all generate events that must reach the right person through the right channel at the right time.

## Vertical Implementations

| Vertical | Alert Types | Trigger Sources | Primary Recipients |
|----------|------------|----------------|-------------------|
| **Mining** | Environmental compliance deadline alerts, dam safety threshold alerts, equipment failure warnings, CFEM filing deadlines, license renewal reminders | Environmental monitoring sensors, compliance calendar, predictive maintenance models, ANM regulatory calendar | Operations managers, environmental engineers, compliance officers, maintenance teams |
| **Investment Advisory** | Next-best-action prompts, suitability drift alerts, churn risk warnings, CVM 179 disclosure deadlines, portfolio rebalancing triggers, new lead notifications | Portfolio change events, ML churn/scoring models, compliance rules engine, CRM engagement data, market data feeds | Individual advisors, compliance officers, operations leads |
| **Insurance/Surety Bonds** | Claims status alerts, regulatory deadline alerts (25-day proposal response per Lei 15.040/2024, 30-day claims response), SUSEP reporting deadlines, fraud flags, underwriting approval notifications | Policy admin system events, claims processing pipeline, fraud detection models, SUSEP regulatory calendar, OPIN data sharing events | Underwriters, claims managers, compliance officers, brokers |
| **Auctions** | New listing alerts (matching investor criteria), bid deadline notifications, edital publication alerts, legal risk flags, post-arrematacao task deadlines | Auction aggregation engine (500+ sites), edital parser, legal risk scorer, workflow automation system | Individual investors, investment fund analysts, legal teams, advisory firms |

## Common Architecture

```
[Event Sources]  →  [Event Bus]  →  [Matching Engine]  →  [Prioritization]  →  [Delivery]  →  [Tracking]
```

### Stage 1: Event Sources

Events originate from all other pattern components:

- **Compliance engines** emit deadline warnings, validation failures, submission confirmations
- **Predictive models** emit score threshold crossings (churn risk > 0.7, equipment failure probability > 0.8)
- **Document intelligence pipelines** emit extraction completions, risk flags, deadline extractions
- **Data integration layer** emits data quality alerts, ingestion failures, source availability changes
- **External systems** emit market data changes, regulatory updates, new listings

### Stage 2: Event Bus

| Component | Recommended Tools | Use Case |
|-----------|------------------|----------|
| **Message Broker** | Apache Kafka, RabbitMQ | High-throughput event streaming; Kafka for auctions (high-volume listing events); RabbitMQ for lower-volume verticals |
| **Event Schema Registry** | Confluent Schema Registry, custom | Enforce event format consistency across producers |
| **Dead Letter Queue** | Built into Kafka/RabbitMQ | Capture and retry failed event processing |

### Stage 3: Matching Engine

The matching engine connects events to recipients based on configurable rules:

- **User preference profiles**: Each user defines their alert criteria
  - Investment advisors: client segments, AuC thresholds, product types
  - Auction investors: property types, locations, price ranges, discount thresholds
  - Mining managers: equipment categories, compliance domains, severity levels
  - Insurance underwriters: policy types, risk thresholds, geographic regions
- **Role-based routing**: Compliance alerts to compliance officers, operational alerts to operations managers
- **Escalation rules**: Unacknowledged alerts escalate after configurable time windows
- **Suppression rules**: Prevent alert fatigue by throttling similar alerts within time windows

### Stage 4: Prioritization

- **Critical**: Regulatory deadlines within 48 hours, safety thresholds breached, high-confidence fraud flags
- **High**: Model predictions crossing action thresholds, new high-value opportunities, compliance drift detected
- **Medium**: Routine deadline reminders, portfolio rebalancing suggestions, status updates
- **Low**: Informational updates, market commentary, batch processing completions

### Stage 5: Delivery Channels

| Channel | Best For | Implementation | Considerations |
|---------|----------|---------------|----------------|
| **WhatsApp Business API** | Brazil's primary communication channel; urgent alerts; advisor-client communication | WhatsApp Business API (official), message templates for structured alerts, interactive buttons for quick actions | 24-hour response window for template messages; must use approved templates; cost per message; high open rates (98%+) |
| **Email** | Detailed reports, compliance summaries, non-urgent notifications, audit trail | SendGrid, AWS SES, or equivalent | Lower urgency; good for batch summaries; regulatory audit trail |
| **Push notifications** | Mobile app users; real-time alerts for auction deadlines, equipment warnings | Firebase Cloud Messaging (FCM), Apple Push Notification Service (APNs) | Requires mobile app; high immediacy; limited content length |
| **In-app notifications** | Dashboard users; contextual alerts within workflow | WebSocket or SSE for real-time; notification center UI | User must be in the application; best for workflow-integrated alerts |
| **SMS** | Fallback for critical alerts when WhatsApp unavailable | Twilio, Vonage | Higher cost; use only for critical/safety alerts |

### Stage 6: Engagement Tracking

- Delivery confirmation (sent, delivered, read)
- Action tracking (alert acknowledged, action taken, dismissed)
- Response time measurement
- Feedback loop: alert relevance scoring to tune matching engine
- Analytics: alert volume by type, channel effectiveness, response rates

## Vertical-Specific Alert Patterns

### Investment Advisory: Next-Best-Action Prompts
The most sophisticated alert pattern -- combines portfolio analysis, client profile, market conditions, and behavioral signals to generate specific action recommendations for advisors:

- "Client X has 60% in fixed income, profile is moderate, Selic is dropping -- suggest rebalancing conversation"
- "Client Y's engagement has dropped 40% over 90 days, churn risk score is 0.78 -- schedule check-in call"
- "CVM 179 quarterly disclosure due in 5 days for 47 clients -- review and approve batch"

Delivery: WhatsApp Business (advisor's phone) + in-app notification on advisor dashboard.

### Auctions: Opportunity Alerts
Time-critical alerts matching investor criteria against new listings:

- New property matching criteria published within 15 minutes of listing
- Bid deadline approaching (24h, 4h, 1h warnings)
- Price reduction or re-listing of previously tracked property
- Legal risk flag on a property in investor's watchlist

Delivery: WhatsApp Business + push notification + email digest (daily summary).

### Mining: Safety and Compliance Alerts
Highest-stakes alerts with potential for physical harm or criminal liability:

- Dam safety instrumentation readings exceeding thresholds (Lei 14.066/2020)
- Environmental condicionante deadline approaching (license suspension risk)
- Equipment failure prediction above 80% probability (safety risk)
- CFEM filing deadline reminders with pre-calculated values

Delivery: SMS (critical/safety) + WhatsApp Business + email + in-app dashboard.

### Insurance: Regulatory Response Deadlines
Lei 15.040/2024 mandates strict response windows:

- 25-day countdown for proposal responses (with milestone alerts at 20, 15, 10, 5, 2, 1 days)
- 30-day countdown for claims responses
- SUSEP SRO reporting deadlines
- Fraud detection flags requiring immediate review

Delivery: In-app workflow notification + email + WhatsApp for critical deadlines.

## Implementation Considerations

### Alert Fatigue Prevention
- Start with fewer, high-value alerts and expand gradually
- Allow users to customize frequency and channels per alert type
- Implement daily/weekly digest modes as alternative to real-time for lower-priority alerts
- Track dismiss rates and automatically tune down alerts with high dismiss ratios
- Group related alerts (e.g., 5 new matching properties as a single notification, not 5 separate ones)

### Reliability
- Critical alerts (safety, regulatory deadlines) must have guaranteed delivery
- Multi-channel fallback: if WhatsApp delivery fails, escalate to SMS and email
- Idempotency: ensure the same alert is not delivered multiple times
- Monitoring for the monitoring system: alert on alert system failures

### Compliance
- LGPD consent required for marketing-style alerts; operational/compliance alerts may have different legal basis
- Maintain opt-out mechanisms per channel
- Audit trail of all alerts sent (who, what, when, which channel, delivery status)

## Estimated Investment

| Scope | Investment Range | Timeline |
|-------|-----------------|----------|
| **Single-vertical alert system** | R$80K-R$150K | 4-8 weeks |
| **Cross-vertical alert platform** | R$200K-R$400K | 10-16 weeks |
| **WhatsApp Business API integration** | R$30K-R$60K | 2-4 weeks (add-on) |

## Cross-References

- Receives events from: [compliance-automation.md](compliance-automation.md), [predictive-models.md](predictive-models.md), [document-intelligence.md](document-intelligence.md)
- Enriched by: [client-360.md](client-360.md) (recipient context for personalization)
- Depends on: [data-integration.md](data-integration.md) (event sources connected through data layer)
