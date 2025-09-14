---
description: Generate technical design from specification
argument-hint: <feature_name>
---

# Technical Design: $FEATURE_NAME

<load_context>
## Step 1: Load Requirements & Standards

<subagent name="context">
Read files:
- `docs/specs/$FEATURE_NAME/*.md` → feature requirements
- `docs/specs/$FEATURE_NAME/*.json` → feature requirements
- `docs/standards/tech.md` → architecture (event-driven microservices)
- `docs/standards/patterns/` → design patterns

Extract key decisions needed:
```yaml
requirements:
  entities: [identify from user stories]
  data_persistence: [what needs storing]
  api_needed: [external access required?]
  ui_components: [user-facing elements]
  business_rules: [validation/constraints]
```

### Output: `docs/specs/$FEATURE_NAME/design.json`
```json
{
  "requirements"{
    "entities": {...},
    "data_persistence":{...},
    "api_needed":{...},
    "components":{...},
    "data_persistence":{...},
    "domains": {...},
    "business_rules": {...}
  },
}
```
</subagent>
</load_context>

<analyze_requirements>
## Step 2: Analyze Technical Needs

<subagent name="architect">
From `docs/specs/$FEATURE_NAME/design.json`, Use the sequential thinking tool to determine:

1. **Domain Entities**
   - Core entity: $FEATURE_NAME
   - Related entities: [from spec]

2. **Data Requirements**
   - Persistence needed: [yes/no]
   - Data volume: [expected scale]
   - Access patterns: [how data is queried]

3. **API Requirements**
   - External exposure: [yes/no]
   - Operations: [CRUD/custom actions]

4. **Component Dependencies**
   - Depends on: [existing features]
   - Required by: [future features]

### Output: `docs/specs/$FEATURE_NAME/design.json`
```json
{
  "technical_needs"{
    "domain_model": {
      "entities":{...},
      "services":{...},
    },
    "persistence":{...},
    "router":{...},
    "events":{...},
    "dependencies":{...},
  },
}
```
</subagent>
</analyze_requirements>

<generate_design>
## Step 3: Generate Technical Design

<subagent name="architect">

Read `docs/specs/$FEATURE_NAME/design.json`, for existing context on design
Use the sequential thinking tool to apply standards to create design:

### Component Architecture
```
Router → Service (Domain) → Repository → Database
                ↓
              Entity
```
```
Router → Service (Domain) → Client → External API
                ↓
              Entity
```
```
Consumer → Service (Domain) → Producer
                ↓
              Entity
```
```
Consumer → Service (Domain) → Repository → Database
                ↓
              Entity
```
```
Router → Service (Domain) → Producer
                ↓
              Entity
```

### Domain Model (if needed)
```yaml
entity: $FEATURE_NAMEEntity
methods:
  - fromRequest(dto): validate and transform from API
  - toRecord(): prepare for database
  - toResponse(): format for API response
  - validate(): business rules enforcement
```

### Data Persistence (if needed)
```yaml
database: [from standards]
schema:
  table: ${feature_name}s
  fields: [based on requirements]
  indexes: [for query patterns]
```

### API Specification (if needed)
```yaml
endpoints:
  - GET /api/${feature_name}s
  - GET /api/${feature_name}s/{id}
  - POST /api/${feature_name}s
  - PUT /api/${feature_name}s/{id}
  - DELETE /api/${feature_name}s/{id}
```

### Events (if applicable)
```yaml
publishes:
  - ${FEATURE_NAME}Created
  - ${FEATURE_NAME}Updated
subscribes:
  - [events from dependencies]
```

### Output: `docs/specs/$FEATURE_NAME/design.json`
```json
{
  "design"{
    "domain_model": {
      "entities":{...},
      "services":{...},
    },
    "database":{...},
    "endpoints":{...},
    "events":{...},
    "dependencies":{...},
  },
}
```
</subagent>
</generate_design>

<write_documentation>
## Step 4: Create Design File

<subagent name="scaffold">
Read: `docs/specs/$FEATURE_NAME/design.json`

Template: `~/.claude/docs/templates/specs/design.md`

Generate: `docs/specs/$FEATURE_NAME/design.md`
</subagent>
</write_documentation>

## ✅ Design Complete

Created: `docs/specs/$FEATURE_NAME/design.md`

The design includes:
- Domain model with DDD patterns
- Data persistence strategy
- API specification (if needed)
- Component structure following standards
- Event definitions for async communication

**Next step**: `/spec:plan $FEATURE_NAME` to generate implementation tasks
