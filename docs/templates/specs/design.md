# {{feature}} Technical Design

## Architecture Overview

### Component Structure
```mermaid
graph TD
    {{#if design.endpoints}}
    A[Router] --> B[Service]
    {{/if}}
    {{#if design.database}}
    B --> C[Repository]
    C --> D[Database]
    {{/if}}
    {{#if design.events}}
    B --> E[Event Producer]
    F[Event Consumer] --> B
    {{/if}}
    B --> G[Entity]
```

## Domain Model

### Core Entity: {{feature}}Entity
{{#if design.domain_model.entities}}
```typescript
class {{feature}}Entity {
  // Properties
{{#each design.domain_model.entities}}
  {{this}}
{{/each}}

  // Methods
  static fromRequest(dto: any): {{../feature}}Entity
  toRecord(): Record<string, any>
  toResponse(): any
  validate(): ValidationResult
}
```
{{/if}}

### Services
{{#each design.domain_model.services}}
- **{{@key}}**: {{this}}
{{/each}}

## Data Persistence

{{#if design.database}}
### Database Schema
```sql
{{design.database.schema}}
```

### Indexes
{{#each design.database.indexes}}
- {{this}}
{{/each}}
{{/if}}

## API Specification

{{#if design.endpoints}}
### REST Endpoints
{{#each design.endpoints}}
- **{{@key}}**: {{this}}
{{/each}}

### Request/Response Flow
```mermaid
sequenceDiagram
    participant C as Client
    participant R as Router
    participant S as Service
    participant E as Entity
    {{#if design.database}}
    participant D as Database
    {{/if}}

    C->>R: HTTP Request
    R->>S: Business Logic
    S->>E: Domain Operations
    {{#if design.database}}
    E->>D: Data Persistence
    D-->>E: Result
    {{/if}}
    E-->>S: Domain Response
    S-->>R: Service Response
    R-->>C: HTTP Response
```
{{/if}}

## Event Architecture

{{#if design.events}}
### Published Events
{{#each design.events.publishes}}
- **{{this}}**: Emitted when {{@key}} occurs
{{/each}}

### Subscribed Events
{{#each design.events.subscribes}}
- **{{this}}**: Triggers {{@key}} process
{{/each}}

### Event Flow
```mermaid
sequenceDiagram
{{#each design.events.flows}}
    {{this}}
{{/each}}
```
{{/if}}

## Dependencies

### Internal Dependencies
{{#each dependencies.internal}}
- **{{@key}}**: {{this}}
{{/each}}

### External Dependencies
{{#each dependencies.external}}
- **{{@key}}**: {{this}}
{{/each}}

## Implementation Notes

### Validation Rules
{{#each technical_needs.business_rules}}
- {{this}}
{{/each}}

### Performance Considerations
{{#each technical_needs.performance}}
- {{this}}
{{/each}}

### Security Requirements
{{#each technical_needs.security}}
- {{this}}
{{/each}}