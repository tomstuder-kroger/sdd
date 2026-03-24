# [Feature Name] - Spec

**Epic**: [Link to ProductBoard/Jira Epic]
**Date**: YYYY-MM-DD
**Status**: Draft | In Review | Approved | Implemented
**Team**: [PM name], [Designer name], [Engineer names]

---

## Context & Background
**Owner: Product Manager**

> **Instructions**: Link to the Epic and summarize key business context. This information should match or be sourced directly from the Epic in ProductBoard/Jira - don't duplicate, just reference and summarize.

- **Epic Link**: [URL to ProductBoard/Jira Epic]
- **User Problem**: [What problem are we solving? Reference Epic or research]
- **Business Value**: [Why does this matter? Link to success metrics in Epic]
- **Research Insights**: [Links to Dovetail research, key findings]
- **User Journey Context**: [Links to Mural journey maps or service blueprints]
- **Success Metrics**: [From Epic - how will we measure success?]

---

## User Experience
**Owner: Product Designer**
**Contributors: PM (user perspective), Engineering (technical constraints)**

> **Instructions**: Document the user-facing design decisions and flows. Include links to Figma with written rationale for key decisions.

### User Flows
[Describe the happy path and key user flows]

### UI/UX Decisions
[Document key design decisions and rationale]
- **Figma Links**: [Link to design files]
- [Design decision 1 and why]
- [Design decision 2 and why]

### Interaction Patterns & States
- **Loading states**: [How do we show loading?]
- **Error states**: [How do we handle errors?]
- **Empty states**: [What do users see when there's no data?]
- **Success states**: [How do we confirm success?]

### Accessibility Considerations
- **WCAG Compliance**: [Any specific requirements?]
- **Screen Reader Support**: [Key considerations]
- **Keyboard Navigation**: [Tab order, shortcuts, focus management]
- **Color Contrast**: [Any special considerations?]

### Edge Cases (User Perspective)
[Document edge cases from the user's point of view]

---

## Technical Approach
**Owner: Engineering Lead**
**Contributors: Design (technical questions/constraints), PM (scope clarification)**

> **Instructions**: Document the technical architecture and implementation approach. This is the blueprint engineers will follow.

### Architecture Overview
[High-level architecture diagram or description]

### Component Breakdown
[List major components, modules, or services]
- **Component 1**: [Purpose, responsibilities]
- **Component 2**: [Purpose, responsibilities]

### Data Models & Schemas
[Document data structures, database schemas, or state shape]

```
Example:
{
  "userId": "string",
  "exportFormat": "csv" | "json",
  "createdAt": "timestamp"
}
```

### API Contracts
[Document endpoints, request/response formats]

**Endpoint**: `POST /api/exports`
**Request**:
```json
{
  "format": "csv",
  "filters": {...}
}
```
**Response**:
```json
{
  "exportId": "string",
  "status": "pending" | "processing" | "complete"
}
```

### Integration Points & Dependencies
[External services, APIs, libraries, or other systems this depends on]

### Technology Choices & Rationale
[Why did we choose specific technologies or approaches?]

### Performance Considerations
[Load time expectations, optimization strategies, caching]

### Security Considerations
[Authentication, authorization, data validation, sensitive data handling]

---

## Acceptance Criteria
**Owner: Shared (PM drafts, Design & Engineering refine)**

> **Instructions**: Detailed, testable criteria. Start with PM's business criteria, then add Design and Engineering details.

### Functional Requirements
- [ ] [Criterion 1 - specific and testable]
- [ ] [Criterion 2 - specific and testable]
- [ ] [Criterion 3 - specific and testable]

### Edge Cases & Error Handling
- [ ] [How does system handle edge case 1?]
- [ ] [How does system handle error condition 2?]

### Performance Requirements
- [ ] [Load time < X seconds]
- [ ] [Can handle Y concurrent users]

### Accessibility Requirements
- [ ] [Keyboard navigable]
- [ ] [Screen reader compatible]
- [ ] [WCAG 2.1 AA compliant]

### Browser/Device Support
- [ ] [Chrome, Firefox, Safari (latest 2 versions)]
- [ ] [iOS Safari, Chrome mobile]
- [ ] [Responsive design: mobile, tablet, desktop]

---

## Testing Strategy
**Owner: Engineering**
**Contributors: PM (user scenarios), Design (visual/interaction QA)**

> **Instructions**: How will we verify this works correctly?

### Unit Test Coverage
[Which components/functions need unit tests? What's the coverage goal?]

### Integration Test Scenarios
[What integration points need testing?]
- [ ] [Scenario 1]
- [ ] [Scenario 2]

### Manual QA Focus Areas
[What should QA specifically test?]
- [ ] [Focus area 1]
- [ ] [Focus area 2]

### User Acceptance Testing (UAT)
[How will PM/Design validate the implementation?]

### Performance Testing
[Load testing, stress testing, benchmarking needs]

---

## Implementation Plan (Optional)
**Owner: Engineering**

> **Instructions**: How will we break this down and sequence the work?

### Phasing Strategy
[If breaking into multiple PRs, describe the phases]
- **Phase 1**: [Scope]
- **Phase 2**: [Scope]

### Dependencies & Sequencing
[What needs to happen first? What can run in parallel?]

### Estimated Effort
[T-shirt sizing or story points - optional]

### Feature Flags or Rollout Strategy
[Gradual rollout? Beta users first? Feature flag approach?]

---

## Open Questions
**Owner: Shared (anyone can add, team resolves together)**

> **Instructions**: Document unresolved decisions or blockers. This section should be empty before status changes to "Approved".

- [ ] **Question 1**: [What needs to be decided?]
  - **Context**: [Why is this important?]
  - **Options**: [What are we considering?]
  - **Decision**: [To be filled when resolved]

- [ ] **Question 2**: [What needs validation?]
  - **Risk**: [What's the risk if we get this wrong?]
  - **Mitigation**: [How will we validate or reduce risk?]

---

## References
**Owner: Shared**

> **Instructions**: Consolidate all relevant links and prior work.

### Design & Research
- [Figma: Link to design files]
- [Mural: Link to journey maps or service blueprints]
- [Dovetail: Link to research findings]

### Documentation
- [Confluence: Link to discovery docs]
- [Related Spec: Link to related spec files if applicable]

### Technical Resources
- [API Documentation]
- [Library/Framework docs]
- [Architectural Decision Records (ADRs)]

---

## Revision History

| Date | Author | Changes |
|------|--------|---------|
| YYYY-MM-DD | [Name] | Initial draft |
| YYYY-MM-DD | [Name] | Added UX section |
| YYYY-MM-DD | [Name] | Technical review updates |

---

## Approval Sign-Off

**Product Manager**: [Name] - [Date] - [Approved/Pending]
**Product Designer**: [Name] - [Date] - [Approved/Pending]
**Engineering Lead**: [Name] - [Date] - [Approved/Pending]

*Once all roles approve, change Status to "Approved" and begin implementation.*
