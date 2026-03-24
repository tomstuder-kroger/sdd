# SDD Framework Enhancements - Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Enhance the Spec Driven Development framework with optional improvements and create example materials for pilot team.

**Architecture:** The core SDD framework (design doc, README, template) is already complete. This plan addresses reviewer recommendations and adds pilot support materials.

**Tech Stack:** Markdown, Git

---

## Context

**Already Completed:**
- ✅ Design document: `docs/superpowers/specs/2026-03-24-spec-driven-development-design.md`
- ✅ Team README: `specs/README.md`
- ✅ Spec template: `specs/TEMPLATE.md`
- ✅ Initial commit to Git

**Reviewer Recommendations (Optional):**
1. Clarify absolute paths and directory structure
2. Specify how/where Spec status should be tracked
3. Add examples for AI assistant integration

**This plan implements:**
- Gitignore configuration
- Spec status tracking guide
- Example spec file for pilot reference
- AI assistant integration guide

---

## File Structure

**New Files:**
- Create: `.gitignore` - ensure proper Git tracking
- Create: `specs/.spec-status-guide.md` - status tracking guidance
- Create: `specs/EXAMPLE-2026-03-csv-export.md` - reference example for pilot team
- Create: `docs/ai-assistant-integration.md` - guide for using specs with AI assistants
- Modify: `specs/README.md` - add links to new resources

---

### Task 1: Git Configuration

**Files:**
- Create: `.gitignore`

- [ ] **Step 1: Create .gitignore file**

Create `.gitignore` to ensure spec files are tracked and common artifacts are ignored.

```gitignore
# IDE
.vscode/
.idea/
*.swp
*.swo
*~

# OS
.DS_Store
Thumbs.db

# Dependencies
node_modules/
venv/
.env
.env.local

# Build artifacts
dist/
build/
*.pyc
__pycache__/

# Logs
*.log
npm-debug.log*
yarn-debug.log*

# Note: specs/ directory SHOULD be tracked
# This is intentional - spec files are part of the repo
```

- [ ] **Step 2: Verify .gitignore works**

Run: `git status`
Expected: `.gitignore` appears as untracked file; `specs/` directory is still tracked

- [ ] **Step 3: Commit .gitignore**

```bash
git add .gitignore
git commit -m "chore: add .gitignore for project artifacts

Ensures spec files remain tracked while ignoring IDE, OS, and build artifacts.

Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>"
```

---

### Task 2: Spec Status Tracking Guide

**Files:**
- Create: `specs/.spec-status-guide.md`

- [ ] **Step 1: Create status tracking guide**

Create `specs/.spec-status-guide.md` with clear guidance on managing spec statuses.

```markdown
# Spec Status Tracking Guide

## Overview

Every spec file has a **Status** field in its header. This guide explains how to track and update spec status throughout the feature lifecycle.

## Status Values

| Status | Meaning | Who Updates | When |
|--------|---------|-------------|------|
| **Draft** | Spec is being written, not ready for review | Authors (PM/Design/Eng) | During initial creation |
| **In Review** | All sections complete, team reviewing | PM or Eng Lead | When all Open Questions resolved |
| **Approved** | Team has signed off, ready for implementation | PM or Eng Lead | After all roles approve |
| **Implemented** | Feature is built and merged | Engineering | After PR merged to main |
| **Archived** | Spec no longer relevant (scope changed, cancelled) | PM | If feature is cancelled |

## How to Update Status

**In the Spec File:**
Edit the status field in the header:

\`\`\`markdown
**Status**: Draft | In Review | Approved | Implemented
\`\`\`

Change to:

\`\`\`markdown
**Status**: Approved
\`\`\`

**Commit the Change:**

\`\`\`bash
git add specs/YYYY-MM-DD-feature-name.md
git commit -m "docs: update spec status to Approved"
\`\`\`

## Status Workflow

\`\`\`
Draft
  ↓
  PM fills Context & Background
  Designer fills User Experience
  Engineer fills Technical Approach
  ↓
In Review
  ↓
  Team resolves Open Questions
  All roles sign off
  ↓
Approved
  ↓
  Implementation begins
  Feature built and tested
  PR merged
  ↓
Implemented
\`\`\`

## Finding Specs by Status

**All approved specs ready for implementation:**
\`\`\`bash
grep -r "Status.*Approved" specs/
\`\`\`

**All implemented specs (historical reference):**
\`\`\`bash
grep -r "Status.*Implemented" specs/
\`\`\`

**All drafts in progress:**
\`\`\`bash
grep -r "Status.*Draft" specs/
\`\`\`

## Best Practices

1. **Update status immediately** when state changes (don't let it get stale)
2. **Include status update in same commit** as the changes that trigger it
3. **Reference the Epic** in commit message when updating to Approved or Implemented
4. **Keep Epic and Spec status aligned** (if Epic is "In Progress", Spec should be "Approved" or "Implemented")

## Examples

**Moving to In Review:**
\`\`\`bash
git add specs/2026-03-user-export.md
git commit -m "docs: spec ready for review

All sections complete, Open Questions resolved. Ready for team sign-off.
Epic: PROD-123"
\`\`\`

**Moving to Approved:**
\`\`\`bash
git add specs/2026-03-user-export.md
git commit -m "docs: spec approved for implementation

PM, Design, and Engineering have signed off. Implementation can begin.
Epic: PROD-123"
\`\`\`

**Moving to Implemented:**
\`\`\`bash
git add specs/2026-03-user-export.md
git commit -m "docs: mark spec as implemented

Feature merged in PR #456. Spec now serves as historical reference.
Epic: PROD-123"
\`\`\`

---

## Questions?

This is a living document. If the status workflow doesn't match your team's needs, update this guide.
```

- [ ] **Step 2: Verify file was created**

Run: `ls -la specs/.spec-status-guide.md`
Expected: File exists

- [ ] **Step 3: Commit status guide**

```bash
git add specs/.spec-status-guide.md
git commit -m "docs: add spec status tracking guide

Addresses reviewer recommendation to clarify how/where spec status is tracked.
Provides clear workflow and Git commands for status updates.

Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>"
```

---

### Task 3: Example Spec File

**Files:**
- Create: `specs/EXAMPLE-2026-03-csv-export.md`

- [ ] **Step 1: Create example spec file**

Create `specs/EXAMPLE-2026-03-csv-export.md` as a reference for the pilot team.

```markdown
# CSV Export Feature - Spec

**Epic**: [https://productboard.example.com/epics/PROD-123](https://productboard.example.com/epics/PROD-123)
**Date**: 2026-03-15
**Status**: Approved
**Team**: Sarah Chen (PM), Jordan Lee (Designer), Alex Rivera (Engineering)

---

## Context & Background
**Owner: Product Manager**

> **Note**: This information is sourced from Epic PROD-123 in ProductBoard.

- **Epic Link**: [PROD-123: Enable Data Export](https://productboard.example.com/epics/PROD-123)
- **User Problem**: Enterprise users need to export their report data for offline analysis in Excel or BI tools. Current workaround is manual copy-paste, which is error-prone and time-consuming.
- **Business Value**: Increases enterprise tier retention by 15% (based on user research showing this is #2 most requested feature). Reduces support tickets related to data access.
- **Research Insights**: [Dovetail Research Summary](https://dovetail.example.com/research/123) - 8 out of 10 enterprise customers requested export functionality in Q4 interviews.
- **User Journey Context**: [Mural Journey Map](https://mural.example.com/journey/reporting) - Export sits at the end of the "Analyze Data" phase.
- **Success Metrics**:
  - 50% of enterprise users use export within first 30 days
  - Export feature drives 10% increase in weekly active usage
  - <5% error rate on export operations

---

## User Experience
**Owner: Product Designer**
**Contributors: PM (user perspective), Engineering (technical constraints)**

### User Flows

**Happy Path:**
1. User views a report with data
2. User clicks "Export" button (top-right of report header)
3. Modal appears with format options (CSV or JSON)
4. User selects CSV, clicks "Download"
5. File downloads immediately (if <1000 rows) OR
6. Toast notification: "Export started, we'll email you when ready" (if >1000 rows)

**Error Flow:**
1. User clicks "Export" on empty report
2. Toast notification: "No data to export. Apply filters to see results."

### UI/UX Decisions

- **Figma Links**: [Export Modal Design](https://figma.com/file/abc123)
- **Button Placement**: Top-right of report header, next to "Share" button (follows established pattern for action buttons)
- **Format Selection**: Radio buttons for CSV/JSON (CSV selected by default based on user research - 90% prefer CSV)
- **Progress Indication**:
  - Small exports (<1000 rows): Immediate download, no loader
  - Large exports (>1000 rows): Email notification pattern (existing pattern used for other async operations)
- **Color & Icon**: Use existing "download" icon from design system, primary blue color

### Interaction Patterns & States

- **Loading states**:
  - Button shows spinner during export generation (0-3 seconds)
  - Modal disabled during generation
- **Error states**:
  - Red toast notification for errors (network failure, permission denied)
  - Error message includes actionable guidance ("Check your connection and try again")
- **Empty states**:
  - Export button disabled (greyed out) when no data available
  - Tooltip on hover: "Apply filters to enable export"
- **Success states**:
  - Green toast: "Export complete! Downloaded to your device."
  - For async exports: "Export started! We'll email you at user@example.com when ready."

### Accessibility Considerations

- **WCAG Compliance**: Level AA required for enterprise tier
- **Screen Reader Support**:
  - Export button has aria-label="Export report data"
  - Modal announces "Export options dialog" when opened
  - Format selection announced as "CSV format selected"
- **Keyboard Navigation**:
  - Export button accessible via Tab
  - Modal can be dismissed with Escape
  - Format selection via arrow keys or Tab
  - Submit with Enter, Cancel with Escape
- **Color Contrast**: Export button meets 4.5:1 contrast ratio (tested in Figma)

### Edge Cases (User Perspective)

- **No data available**: Export button disabled with tooltip
- **Permission denied**: Toast error "You don't have permission to export this report. Contact your admin."
- **Network failure during download**: Toast error "Download failed. Check your connection and try again."
- **File size too large**: Async email pattern with progress tracking

---

## Technical Approach
**Owner: Engineering Lead**
**Contributors: Design (technical questions/constraints), PM (scope clarification)**

### Architecture Overview

```
┌─────────────┐       ┌──────────────┐       ┌─────────────┐
│  React      │──────▶│  Export API  │──────▶│  S3 Bucket  │
│  Component  │       │  (Node.js)   │       │  (temp)     │
└─────────────┘       └──────────────┘       └─────────────┘
                             │
                             ▼
                      ┌──────────────┐
                      │  Email Queue │
                      │  (SQS)       │
                      └──────────────┘
```

Small exports (<1000 rows): Synchronous response with file data
Large exports (>1000 rows): Async job + email notification

### Component Breakdown

- **Frontend Component**: `src/components/ExportButton/ExportButton.tsx`
  - Renders button and modal
  - Handles format selection
  - Triggers download or shows email notification

- **API Endpoint**: `src/api/exports/createExport.ts`
  - Validates user permissions
  - Generates CSV/JSON from report data
  - Returns file directly (small) or queues job (large)

- **Background Worker**: `src/workers/exportWorker.ts`
  - Processes large export jobs
  - Uploads to S3 with signed URL
  - Sends email via SQS

- **Email Template**: `src/templates/exportReady.html`
  - Notification email with download link
  - Link expires after 24 hours

### Data Models & Schemas

**Export Request (POST /api/exports)**
```typescript
interface ExportRequest {
  reportId: string;
  format: 'csv' | 'json';
  filters?: Record<string, any>;
}
```

**Export Response (Sync)**
```typescript
interface ExportResponseSync {
  type: 'sync';
  filename: string;
  data: string; // CSV or JSON string
  mimeType: string;
}
```

**Export Response (Async)**
```typescript
interface ExportResponseAsync {
  type: 'async';
  jobId: string;
  estimatedTime: number; // seconds
  notificationEmail: string;
}
```

**Export Job (Database)**
```typescript
interface ExportJob {
  id: string;
  userId: string;
  reportId: string;
  format: 'csv' | 'json';
  status: 'pending' | 'processing' | 'complete' | 'failed';
  s3Url?: string; // signed URL after complete
  createdAt: Date;
  completedAt?: Date;
  error?: string;
}
```

### API Contracts

**Endpoint**: `POST /api/exports`

**Request Headers**:
```
Authorization: Bearer <token>
Content-Type: application/json
```

**Request Body**:
```json
{
  "reportId": "rpt_abc123",
  "format": "csv",
  "filters": {
    "dateRange": "2026-01-01:2026-03-01",
    "category": "sales"
  }
}
```

**Response (Small Export)**:
```json
{
  "type": "sync",
  "filename": "sales-report-2026-03-15.csv",
  "data": "Name,Value,Date\nItem1,100,2026-01-15\n...",
  "mimeType": "text/csv"
}
```

**Response (Large Export)**:
```json
{
  "type": "async",
  "jobId": "job_xyz789",
  "estimatedTime": 120,
  "notificationEmail": "user@example.com"
}
```

**Error Responses**:
- `403`: Permission denied (user lacks export permission)
- `404`: Report not found
- `429`: Rate limit exceeded (max 5 exports per hour)
- `500`: Server error during export generation

### Integration Points & Dependencies

- **Existing Report API**: `/api/reports/:id` - fetches report data for export
- **Permission Service**: `src/services/permissions.ts` - validates export permission
- **S3 Service**: AWS SDK for S3 - uploads large exports with signed URLs
- **Email Queue**: SQS queue - triggers email notifications
- **Email Service**: SendGrid - sends notification emails with download links

### Technology Choices & Rationale

- **CSV Generation**: Use `papaparse` library (already in use for imports, maintains consistency)
- **JSON Generation**: Native `JSON.stringify()` with streaming for large files
- **Async Processing**: Bull queue on Redis (existing job queue infrastructure)
- **Storage**: S3 with 24-hour signed URLs (existing pattern for file sharing)
- **Row Count Threshold**: 1000 rows (based on load testing - 1000 rows = ~2 second generation time, acceptable for sync response)

### Performance Considerations

- **Load Time Expectations**:
  - Sync exports (<1000 rows): <3 seconds total
  - Async exports: Job queued in <500ms, background processing 1-5 minutes depending on size
- **Optimization Strategies**:
  - Stream data from database to avoid loading full result set in memory
  - Use database cursors for large queries
  - Compress CSV/JSON before S3 upload (gzip)
- **Caching**: No caching (exports should always reflect current data)

### Security Considerations

- **Authentication**: JWT token required (existing auth middleware)
- **Authorization**: Check user has `export:read` permission for the report's organization
- **Data Validation**:
  - Validate reportId exists and user has access
  - Sanitize filter parameters to prevent injection
  - Validate format is 'csv' or 'json' only
- **Sensitive Data Handling**:
  - S3 URLs expire after 24 hours
  - Export jobs deleted from DB after 7 days
  - PII columns (email, SSN) obfuscated unless user has `export:pii` permission
- **Rate Limiting**: Max 5 exports per user per hour (prevent abuse)

---

## Acceptance Criteria
**Owner: Shared (PM drafts, Design & Engineering refine)**

### Functional Requirements

- [ ] User can click "Export" button on any report with data
- [ ] User can select CSV or JSON format in modal
- [ ] Small exports (<1000 rows) download immediately
- [ ] Large exports (>1000 rows) trigger email notification
- [ ] User receives email with download link within 5 minutes for large exports
- [ ] Download link expires after 24 hours
- [ ] Exported CSV includes all visible columns from report
- [ ] Exported CSV respects applied filters
- [ ] Exported JSON uses same schema as Report API response

### Edge Cases & Error Handling

- [ ] Export button disabled when report has no data
- [ ] Error toast shown if user lacks export permission
- [ ] Error toast shown if network fails during download
- [ ] Async export job fails gracefully if S3 upload fails (user receives error email)
- [ ] Retry mechanism for failed async exports (3 retries with exponential backoff)

### Performance Requirements

- [ ] Sync exports complete in <3 seconds (p95)
- [ ] Async export jobs complete in <5 minutes for 100k rows (p95)
- [ ] Export button click responds in <200ms
- [ ] API endpoint returns 403 in <100ms if permission denied

### Accessibility Requirements

- [ ] Export button accessible via keyboard (Tab to focus, Enter to activate)
- [ ] Modal accessible via keyboard (Esc to close, Tab to navigate, Enter to submit)
- [ ] Screen reader announces button label "Export report data"
- [ ] Screen reader announces modal title "Export options"
- [ ] WCAG 2.1 AA compliant (4.5:1 contrast, keyboard nav, screen reader support)

### Browser/Device Support

- [ ] Works in Chrome, Firefox, Safari (latest 2 versions)
- [ ] Works in iOS Safari, Chrome mobile
- [ ] Modal responsive on mobile (320px width)
- [ ] File download works on iOS (prompts "Save to Files")

---

## Testing Strategy
**Owner: Engineering**
**Contributors: PM (user scenarios), Design (visual/interaction QA)**

### Unit Test Coverage

**Target**: 80% coverage for new code

**Components to Test**:
- `ExportButton.tsx`: Render states (enabled/disabled), click handling, modal open/close
- `createExport.ts`: Permission validation, sync vs async logic, CSV/JSON generation
- `exportWorker.ts`: Job processing, S3 upload, email queueing, retry logic

**Example Test** (ExportButton):
```typescript
describe('ExportButton', () => {
  it('disables button when no data available', () => {
    render(<ExportButton reportData={[]} />);
    expect(screen.getByRole('button', { name: /export/i })).toBeDisabled();
  });

  it('opens modal when clicked', () => {
    render(<ExportButton reportData={mockData} />);
    fireEvent.click(screen.getByRole('button', { name: /export/i }));
    expect(screen.getByText(/export options/i)).toBeInTheDocument();
  });
});
```

### Integration Test Scenarios

- [ ] **Scenario 1**: Small export flow
  - User clicks Export → selects CSV → clicks Download
  - Verify API called with correct params
  - Verify file downloaded with correct name and content

- [ ] **Scenario 2**: Large export flow
  - User clicks Export on 5000-row report → selects CSV → clicks Download
  - Verify async job created in database
  - Verify user sees "email notification" toast
  - Verify email sent after job completes

- [ ] **Scenario 3**: Permission denied
  - User without `export:read` permission clicks Export
  - Verify API returns 403
  - Verify error toast shown

- [ ] **Scenario 4**: Network failure
  - Mock network failure during export API call
  - Verify error toast shown with actionable message

### Manual QA Focus Areas

- [ ] **Visual QA**:
  - Export button matches Figma design (color, icon, size, placement)
  - Modal matches Figma design (layout, spacing, typography)
  - Toast notifications match design system

- [ ] **Interaction QA**:
  - Button hover state shows correct cursor and color
  - Modal animates smoothly on open/close
  - Radio buttons update correctly when clicked
  - Download triggers browser's native download UI

- [ ] **Accessibility QA**:
  - Tab order: Export button → Modal → Format options → Download/Cancel
  - Escape closes modal
  - Screen reader announces all states correctly
  - High contrast mode works (Windows, macOS)

### User Acceptance Testing (UAT)

**PM/Design Validation**:
- [ ] Test with real report data (10 rows, 500 rows, 5000 rows)
- [ ] Verify CSV opens correctly in Excel
- [ ] Verify JSON is valid and matches API schema
- [ ] Test error flows (no permission, no data, network failure)
- [ ] Verify email notification for large exports

**Beta User Testing** (1 week before GA):
- [ ] 5 enterprise customers test export on production-like data
- [ ] Gather feedback on UX, performance, file format quality

### Performance Testing

- [ ] **Load Test**: 100 concurrent export requests
  - Target: <5% error rate, p95 response time <3 seconds (sync exports)

- [ ] **Stress Test**: 1000-row export generation
  - Target: <3 seconds total (p95)

- [ ] **Async Job Test**: 100k-row export
  - Target: <5 minutes total (p95)

---

## Implementation Plan
**Owner: Engineering**

### Phasing Strategy

**Phase 1**: Sync exports only (CSV format, <1000 rows)
- Simpler implementation, lower risk
- Delivers value to 80% of users (based on usage data)
- PR #1: Frontend component + API endpoint

**Phase 2**: Async exports (>1000 rows, email notification)
- More complex, requires background worker + email
- PR #2: Background worker + S3 upload + email queue

**Phase 3**: JSON format support
- Lower priority (10% of users prefer JSON)
- PR #3: Add JSON generation to both sync and async paths

### Dependencies & Sequencing

**Must Complete First**:
- [ ] Obtain `export:read` permission added to permission service (Eng team)
- [ ] S3 bucket created for exports with lifecycle policy (DevOps team - ticket INFRA-456)
- [ ] Email template approved by Design (Jordan Lee)

**Can Run in Parallel**:
- Frontend component development
- Backend API development
- Background worker development

### Estimated Effort

- **Phase 1** (Sync CSV): 5 points (1 sprint)
- **Phase 2** (Async + Email): 8 points (1.5 sprints)
- **Phase 3** (JSON format): 3 points (0.5 sprint)
- **Total**: 16 points (~2.5 sprints)

### Feature Flags or Rollout Strategy

**Feature Flag**: `export_feature_enabled`
- **Week 1**: Enable for internal team only (dogfooding)
- **Week 2**: Enable for 10% of enterprise users (beta)
- **Week 3**: Enable for 50% of enterprise users
- **Week 4**: Enable for 100% of enterprise users (GA)

**Rollback Plan**: If error rate >5% or negative user feedback, disable flag immediately

---

## Open Questions
**Owner: Shared (anyone can add, team resolves together)**

*All questions resolved during review - spec approved for implementation.*

---

## References
**Owner: Shared**

### Design & Research

- [Figma: Export Modal Design](https://figma.com/file/abc123)
- [Figma: Button Placement Exploration](https://figma.com/file/abc124)
- [Mural: User Journey Map - Reporting](https://mural.example.com/journey/reporting)
- [Dovetail: Q4 Enterprise Research Summary](https://dovetail.example.com/research/123)

### Documentation

- [Confluence: CSV Export Discovery](https://confluence.example.com/discovery/csv-export)
- [Confluence: Export Feature PRD](https://confluence.example.com/prd/export-feature)

### Technical Resources

- [Report API Documentation](https://docs.example.com/api/reports)
- [Permission Service Documentation](https://docs.example.com/services/permissions)
- [S3 Upload Guide](https://docs.example.com/guides/s3-upload)
- [Email Queue Documentation](https://docs.example.com/services/email-queue)

---

## Revision History

| Date | Author | Changes |
|------|--------|---------|
| 2026-03-10 | Sarah Chen | Initial draft (Context, Acceptance Criteria) |
| 2026-03-11 | Jordan Lee | Added User Experience section |
| 2026-03-12 | Alex Rivera | Added Technical Approach, Testing Strategy, Implementation Plan |
| 2026-03-13 | Team | Collaborative review, resolved Open Questions |
| 2026-03-15 | Alex Rivera | Updated status to Approved after all sign-offs |

---

## Approval Sign-Off

**Product Manager**: Sarah Chen - 2026-03-13 - **Approved**
**Product Designer**: Jordan Lee - 2026-03-13 - **Approved**
**Engineering Lead**: Alex Rivera - 2026-03-13 - **Approved**

*Status changed to "Approved" on 2026-03-15. Implementation begins 2026-03-18.*
```

- [ ] **Step 2: Verify example file was created**

Run: `ls -la specs/EXAMPLE-2026-03-csv-export.md`
Expected: File exists

- [ ] **Step 3: Commit example spec**

```bash
git add specs/EXAMPLE-2026-03-csv-export.md
git commit -m "docs: add example spec file for pilot reference

Provides concrete example of a well-structured spec for the pilot team.
Demonstrates all sections with realistic content, ownership, and detail level.

Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>"
```

---

### Task 4: AI Assistant Integration Guide

**Files:**
- Create: `docs/ai-assistant-integration.md`

- [ ] **Step 1: Create AI assistant integration guide**

Create `docs/ai-assistant-integration.md` with guidance on using specs with AI coding assistants.

```markdown
# AI Assistant Integration Guide

## Overview

Spec files are designed to be AI-friendly. They live in Git, use structured markdown, and contain all the context an AI coding assistant needs to implement a feature correctly.

This guide shows how to leverage specs with AI assistants like GitHub Copilot, Cursor, Claude Code, and others.

---

## Why Specs Work Well with AI Assistants

**AI assistants work best when they have:**
1. **Complete context** - specs consolidate business requirements, design decisions, and technical approach
2. **Structured format** - markdown sections are easy to parse and reference
3. **Version control** - specs live in Git alongside the code they describe
4. **Clear acceptance criteria** - AI can validate implementations against testable criteria

**Specs address common AI coding problems:**
- "I don't know what business logic to implement" → Context & Background section
- "I don't know what the UI should look like" → User Experience section
- "I don't know which architectural approach to use" → Technical Approach section
- "I don't know how to test this" → Testing Strategy section

---

## How to Use Specs with AI Assistants

### 1. Context Loading (Before Starting)

**Give the AI the full spec as context:**

```
I'm implementing the feature described in specs/2026-03-csv-export.md.
Please read this spec and let me know when you're ready to start.
```

**Why this works**: AI reads the entire spec and understands the full scope before writing any code.

### 2. Section-by-Section Implementation

**Reference specific sections when asking for code:**

```
Based on the "Technical Approach" section of the spec, implement the
ExportButton component described in specs/2026-03-csv-export.md.
```

**Why this works**: AI focuses on the relevant section, reducing hallucination and off-spec implementations.

### 3. Acceptance Criteria Validation

**Ask AI to validate against acceptance criteria:**

```
Review my implementation of the export feature against the "Acceptance Criteria"
section in specs/2026-03-csv-export.md. Are there any criteria I haven't met?
```

**Why this works**: AI acts as a checklist, ensuring nothing is missed.

### 4. Test Generation

**Use the Testing Strategy section for test guidance:**

```
Generate unit tests for ExportButton.tsx based on the "Testing Strategy" section
in specs/2026-03-csv-export.md.
```

**Why this works**: AI generates tests that match the spec's testing approach, not generic tests.

---

## Best Practices

### ✅ DO

- **Load the spec first**: Give AI the full spec before asking for implementations
- **Reference sections explicitly**: "Based on the Technical Approach section..."
- **Validate against acceptance criteria**: Ask AI to check completeness
- **Use spec for test generation**: Reference Testing Strategy section
- **Update spec if requirements change**: Keep spec and code in sync

### ❌ DON'T

- **Don't ask AI to guess requirements**: Always provide the spec
- **Don't let AI deviate from the spec**: If AI suggests changes, discuss with team first
- **Don't skip validation**: Always check AI code against acceptance criteria
- **Don't assume AI remembers**: Re-load spec context if AI seems off-track

---

## Example Workflows

### Workflow 1: Implement a New Feature from Spec

```
Step 1: Load context
"I'm implementing the feature in specs/2026-03-csv-export.md. Read the spec."

Step 2: Plan implementation
"Based on the spec, what order should I implement the components in?"

Step 3: Implement component by component
"Implement ExportButton.tsx according to the User Experience and Technical Approach sections."

Step 4: Generate tests
"Generate unit tests based on the Testing Strategy section."

Step 5: Validate
"Review my implementation against all Acceptance Criteria. What's missing?"
```

### Workflow 2: Review Existing Code Against Spec

```
Step 1: Load spec and code
"Here's the spec (specs/2026-03-csv-export.md) and my implementation (src/components/ExportButton.tsx)."

Step 2: Ask for comparison
"Does my implementation match the spec? Highlight any deviations."

Step 3: Identify gaps
"Which Acceptance Criteria are not met by my current implementation?"

Step 4: Fix deviations
"Update my code to match the Technical Approach section more closely."
```

### Workflow 3: Generate Documentation from Spec

```
"Based on specs/2026-03-csv-export.md, generate:
1. API documentation for the /api/exports endpoint
2. README section explaining how to use the export feature
3. User-facing help text for the export modal"
```

---

## Tool-Specific Tips

### GitHub Copilot

- Add spec path as a comment in your code file:
  ```typescript
  // Implementation of specs/2026-03-csv-export.md - ExportButton component
  ```
- Copilot will use nearby file context, including the spec if it's in the same repo

### Cursor

- Use Cursor's "Add to Context" feature to load the spec file
- Reference specific sections: "@specs/2026-03-csv-export.md#technical-approach"

### Claude Code (CLI)

- Use `/read` command to load spec:
  ```
  /read specs/2026-03-csv-export.md
  ```
- Claude Code can read multiple files, so you can load spec + existing code simultaneously

### ChatGPT / Claude (Web)

- Copy/paste the spec markdown into the chat
- Use headings to reference sections: "Based on the ## Technical Approach section..."

---

## Keeping Specs and Code in Sync

### When Code Diverges from Spec

**If you discover the spec is wrong during implementation:**
1. Stop coding
2. Discuss with PM/Design/Engineering
3. Update the spec first
4. Then continue implementation

**If you make a small deviation (e.g., slightly different variable name):**
- OK to proceed if it doesn't affect behavior
- Document deviation in PR description

**If you make a significant deviation (e.g., different architecture):**
- Not OK - this bypasses the spec review process
- Update spec, get team re-approval, then implement

### Updating Specs After Implementation

When a feature is complete:
1. Update spec status to "Implemented"
2. If any deviations occurred, note them in "Revision History"
3. Commit spec update with implementation PR

```bash
git add specs/2026-03-csv-export.md
git commit -m "docs: mark export spec as implemented

Feature merged in PR #456. Minor deviation: used Bull queue instead of SQS
for async jobs (team decision in standup on 2026-03-20).

Epic: PROD-123"
```

---

## Troubleshooting

### AI is generating code that doesn't match the spec

**Problem**: AI suggests a different approach than what's in the Technical Approach section.

**Solution**:
```
"Please stick to the architecture described in the Technical Approach section
of specs/2026-03-csv-export.md. Don't suggest alternative approaches."
```

### AI is missing acceptance criteria

**Problem**: Implementation looks good but fails some acceptance criteria.

**Solution**:
```
"Review all checkboxes in the Acceptance Criteria section. Which ones does my
current implementation not satisfy?"
```

### AI can't find the spec file

**Problem**: AI says it can't access the file.

**Solution**: Copy/paste the spec content directly into the chat, or use your tool's file upload feature.

---

## Benefits of Spec-Driven AI Coding

**Speed**: AI implements faster when it has complete context upfront
**Quality**: AI code matches team decisions (architecture, patterns, testing approach)
**Consistency**: Multiple AI sessions produce similar implementations (they all follow the same spec)
**Validation**: AI can self-check against acceptance criteria
**Onboarding**: New team members + AI can ramp up quickly by reading specs

---

## Example Prompts

### Starting a Feature
```
I'm implementing the CSV export feature. The spec is at specs/2026-03-csv-export.md.

Step 1: Read the spec and summarize the key requirements.
Step 2: Suggest an implementation order for the components.
Step 3: Implement ExportButton.tsx according to the spec.
```

### Reviewing Code
```
Here's my implementation of ExportButton.tsx [paste code].

Compare it to the spec at specs/2026-03-csv-export.md.
- Does it match the User Experience section?
- Does it satisfy the Acceptance Criteria?
- What's missing or incorrect?
```

### Generating Tests
```
Generate unit tests for ExportButton.tsx based on:
1. The Testing Strategy section in specs/2026-03-csv-export.md
2. The example test shown in that section
3. Coverage for all Acceptance Criteria related to the button
```

### Updating Documentation
```
The export feature is now implemented. Based on specs/2026-03-csv-export.md,
generate user-facing documentation explaining:
- What the export feature does
- How to use it (step-by-step)
- What file formats are supported
- What to do if export fails
```

---

## Questions?

This guide will evolve as the team gains experience using specs with AI assistants. Share your tips and workflows!
```

- [ ] **Step 2: Verify AI guide was created**

Run: `ls -la docs/ai-assistant-integration.md`
Expected: File exists

- [ ] **Step 3: Commit AI integration guide**

```bash
git add docs/ai-assistant-integration.md
git commit -m "docs: add AI assistant integration guide

Addresses reviewer recommendation to include AI assistant integration examples.
Provides workflows, best practices, and tool-specific tips for using specs
with GitHub Copilot, Cursor, Claude Code, and other AI coding assistants.

Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>"
```

---

### Task 5: Update README with New Resources

**Files:**
- Modify: `specs/README.md`

- [ ] **Step 1: Read current README**

Run: `cat specs/README.md | head -20`
Expected: See current content

- [ ] **Step 2: Add links to new resources**

Add a new "Additional Resources" section before the final "Questions?" section:

```markdown
## Additional Resources

- **Spec Status Tracking**: [`.spec-status-guide.md`](.spec-status-guide.md) - How to update and track spec statuses
- **Example Spec**: [`EXAMPLE-2026-03-csv-export.md`](EXAMPLE-2026-03-csv-export.md) - Reference example for pilot team
- **AI Assistant Integration**: [`../docs/ai-assistant-integration.md`](../docs/ai-assistant-integration.md) - Using specs with AI coding assistants
```

Insert this section right before:
```markdown
## Questions?
```

- [ ] **Step 3: Verify README updated correctly**

Run: `grep -A 5 "Additional Resources" specs/README.md`
Expected: See the new section with links

- [ ] **Step 4: Commit README update**

```bash
git add specs/README.md
git commit -m "docs: add links to new resources in README

Links to status guide, example spec, and AI integration guide for easy discovery.

Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>"
```

---

## Implementation Complete

All tasks completed! The SDD framework now includes:

**Core Framework** (already completed):
- ✅ Design document with Epic/Spec boundary and workflow
- ✅ Team README explaining when and how to create specs
- ✅ Spec template with ownership and sections

**Enhancements** (this plan):
- ✅ Gitignore configuration
- ✅ Spec status tracking guide
- ✅ Example spec file for pilot reference
- ✅ AI assistant integration guide
- ✅ Updated README with resource links

**Final Repository Structure**:
```
/Users/ts73344/sdd/
├── .gitignore
├── docs/
│   ├── ai-assistant-integration.md
│   └── superpowers/
│       ├── plans/
│       │   └── 2026-03-24-sdd-framework-enhancements.md
│       └── specs/
│           └── 2026-03-24-spec-driven-development-design.md
└── specs/
    ├── .spec-status-guide.md
    ├── EXAMPLE-2026-03-csv-export.md
    ├── README.md
    └── TEMPLATE.md
```

**Next Steps for User**:
1. Review the implementation plan
2. Choose execution approach (subagent-driven or inline)
3. Execute the plan to create the enhancement files
4. Share framework with PM and Engineering partners
5. Select pilot feature and begin SDD pilot

---

## Navigation

**Team Docs:**
[Team README](../../../specs/README.md) · [Spec Template](../../../specs/TEMPLATE.md) · [Example Spec](../../../specs/EXAMPLE-2026-03-csv-export.md) · [Status Tracking](../../../specs/.spec-status-guide.md)

**Guides:**
[AI Integration](../../ai-assistant-integration.md) · [Pilot Discussion](../../../PILOT-DISCUSSION-GUIDE.md)

**Framework:**
[Design Document](../specs/2026-03-24-spec-driven-development-design.md) · [Implementation Plan](2026-03-24-sdd-framework-enhancements.md) · [CLAUDE.md](../../../CLAUDE.md)
