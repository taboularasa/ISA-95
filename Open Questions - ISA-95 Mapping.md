# Open Questions - ISA-95 Mapping for Our Systems

## Overview
As we map our existing and planned systems to ISA-95 concepts, several architectural questions emerge. These questions highlight areas where our modern manufacturing IT landscape doesn't fit neatly into ISA-95's model, or where we need to make key design decisions.

## Capacity Management Questions

### 1. Shared Capacity Service Architecture
- **Current State**: Capacity planning exists in both QTO (for quoting) and FES (for execution)
- **Questions**:
  - Should we create a dedicated Capacity Service that serves both L4 and L3?
  - How do we reconcile ISA-95's view (capacity is L3) with business needs (quoting needs capacity)?
  - What's the source of truth for capacity - FES (actual) or a shared service?

### 2. Capacity Change Management
- **Scenario**: Capacity changes between quote and order fulfillment
- **Questions**:
  - How do we handle quotes that become invalid due to capacity changes?
  - Should DOM re-validate capacity when converting QTO POs to production orders?
  - Do we need capacity "reservations" or "soft bookings" during quote validity periods?

### 3. Real-time vs Planned Capacity
- **Challenge**: QTO needs forward-looking capacity, FES has real-time capacity
- **Questions**:
  - How do we model future capacity considering maintenance, new equipment, etc.?
  - Should capacity planning include workforce availability?
  - How granular should capacity models be (machine-level, work center, plant)?

## System Integration Questions

### 4. DOM and QTO Integration
- **Design Decision**: Where does QTO end and DOM begin?
- **Questions**:
  - Should PO acceptance trigger automatic DOM order creation?
  - How do we handle PO modifications after DOM has started scheduling?
  - Who owns customer delivery promises - QTO, DOM, or shared?

### 5. Product Definition Authority
- **Current**: Part data exists in multiple systems (QTO, Part Service, FES)
- **Questions**:
  - During migration, how do we maintain consistency?
  - Should FES cache part data or always query Part Service?
  - How do we handle part revision changes during active production?
  - What's the "release to manufacturing" process?

### 6. Master Data Synchronization
- **Challenge**: Multiple L4 systems with overlapping data domains
- **Questions**:
  - Should we implement event-driven architecture for master data changes?
  - How do we handle conflicts (e.g., different quality specs for same part)?
  - Do we need a Master Data Management (MDM) strategy?

## ISA-95 Conceptual Challenges

### 7. Multi-Equipment Process Definitions
- **From Meeting Notes**: "Don't want to manage 10 different process masters for one part"
- **Questions**:
  - How do we implement ISA-95's Work Master concept with equipment flexibility?
  - Should we use inheritance, composition, or parameter-driven approaches?
  - Where do equipment-specific optimizations live?

### 8. Modern Manufacturing Concepts
- **Gap**: ISA-95 doesn't address modern concepts like 3D models, AI/ML (Copilot), cloud architectures
- **Questions**:
  - How do we extend ISA-95 for digital manufacturing assets?
  - Where does AI/ML fit in the ISA-95 hierarchy?
  - How do we handle cloud/edge computing splits?

### 9. Customer-Specific Variants
- **Reality**: Customer part variants in Part Service
- **Questions**:
  - How do we map customer variants to standard ISA-95 product definitions?
  - Should work masters be customer-variant aware?
  - How do we handle customer-specific quality requirements?

## Information Flow Questions

### 10. Event-Driven vs Request-Response
- **Observation**: Mix of gRPC (sync) and Kafka (async) in QTO
- **Questions**:
  - Which ISA-95 flows should be event-driven?
  - How do we handle eventual consistency across levels?
  - Do we need event sourcing for audit trails?

### 11. Performance Data Aggregation
- **ISA-95 Flow**: Production Performance (L3→L4)
- **Questions**:
  - What granularity of data should flow to L4?
  - Should we aggregate in FES or in a dedicated analytics service?
  - How do we correlate performance to quotes/orders?

### 12. Feedback Loops
- **Challenge**: Multiple systems need production feedback
- **Questions**:
  - How does actual performance influence future quotes?
  - Should QTO capacity planning learn from FES actuals?
  - Where do we close the loop on continuous improvement?

## Organizational Questions

### 13. System Ownership
- **Note**: "we lack teams and leadership in this area"
- **Questions**:
  - Who owns the ISA-95 integration architecture?
  - How do we govern changes that span L3/L4 boundaries?
  - Should we create a manufacturing systems architecture team?

### 14. Migration Strategy
- **Reality**: Systems in transition (DFM extraction, Part Service migration)
- **Questions**:
  - How do we maintain ISA-95 compliance during migration?
  - Should we implement new patterns in legacy systems or wait?
  - What's the sequence for system modernization?

## Next Steps
1. Prioritize questions based on DOM/FES integration timeline
2. Create proof-of-concepts for critical integration patterns
3. Establish architecture decision records (ADRs) for key choices
4. Consider creating a Manufacturing Systems Architecture team

## Related Documents
- [[ISA-95 Part 3 - Section 6.4.3 Tasks in Product Definition Management]]
- [[Understanding ISA-95 Activity Model]]
- [[Information Flows – Enterprise ↔ Control  (ISA-95 Part 3 §6 & Figure 6)]]


## DFM-Specific Challenges to ISA-95

### 15. Bridge Systems Between Levels
- **Challenge**: DFM operates between L4 (business) and L3 (operations)
- **Questions**:
  - Should we recognize "bridge" systems as a valid architectural pattern?
  - How do we govern systems that need deep knowledge of multiple levels?
  - Is there a need for a new level between L4 and L3 for engineering/design services?

### 16. Customer-Facing Manufacturing Systems
- **Reality**: DFM provides direct customer interfaces for manufacturability analysis
- **Questions**:
  - How do we model external customer access to manufacturing intelligence?
  - Where do self-service manufacturing tools fit in ISA-95?
  - How do we maintain security while exposing manufacturing capabilities?

### 17. Iterative Design-Manufacturing Feedback
- **Challenge**: Redlining and design review create complex feedback loops
- **Questions**:
  - How do we model iterative processes that span levels?
  - Who owns the "truth" during design iteration - customer, DFM, or FES?
  - How do we track changes that affect multiple systems?

### 18. Engineering Master vs Work Master
- **Observation**: DFM creates "candidate Engineering Masters" before production
- **Questions**:
  - Is Engineering Master the same as ISA-95's Work Master?
  - Should recipe creation happen in DFM (pre-order) or FES (post-order)?
  - How do we handle multiple valid ways to manufacture the same part?

### 19. Risk Assessment and Prediction
- **Gap**: ISA-95 doesn't address pre-production risk analysis
- **Questions**:
  - Where does manufacturing risk assessment belong in the hierarchy?
  - How do we feed historical performance back into risk models?
  - Should predictive analytics be centralized or distributed?

### 20. Multi-Context Service Delivery
- **Reality**: DFM serves different purposes (quoting, PO approval, design review)
- **Questions**:
  - How do we architect systems that serve multiple contexts?
  - Should we have different DFM instances for different use cases?
  - How do we maintain consistency across contexts?

### 21. Automation vs Human Judgment
- **DFM Approach**: 25-50% automated with manual override always available
- **Questions**:
  - How do we model human-in-the-loop systems in ISA-95?
  - Where do we draw the line between automation and human expertise?
  - How do we capture and encode manufacturing expertise?

### 22. External Tool Integration
- **Future**: DFM embedded in customer CAD systems, third-party tools
- **Questions**:
  - How do we expose manufacturing constraints to external design tools?
  - What's the governance model for external DFM deployments?
  - How do we maintain consistency with embedded DFM modules?

## Integration Architecture Questions

### 23. DFM Data Flow Patterns
- **Challenge**: DFM consumes from everywhere, produces for everywhere
- **Questions**:
  - Should DFM cache data from Reference Services, Part Service, etc.?
  - How do we handle DFM's need for real-time manufacturing capabilities?
  - What's the source of truth for manufacturability decisions?

### 24. Change Propagation from DFM
- **Scenario**: DFM identifies need for design change or process adjustment
- **Questions**:
  - How do DFM-initiated changes flow to other systems?
  - Should DFM directly update Part Service or go through workflows?
  - How do we prevent circular dependencies in change management?

### 25. DFM as a Service Platform
- **Vision**: DFM as standalone service, embedded in customer systems
- **Questions**:
  - How do we version and deploy DFM across different contexts?
  - What's the business model for external DFM consumption?
  - How do we protect IP while enabling self-service?

## Philosophical Questions

### 26. Manufacturing Knowledge Management
- **Core Issue**: DFM encodes manufacturing expertise into software
- **Questions**:
  - How do we keep encoded knowledge current with factory evolution?
  - Who owns manufacturing knowledge - DFM, FES, or humans?
  - How do we balance standardization with factory-specific optimizations?

### 27. The Cost of Flexibility
- **Observation**: DFM's micro-frontend architecture enables flexibility
- **Questions**:
  - Is the complexity of federated modules worth the flexibility?
  - How do we maintain consistency across distributed DFM components?
  - Where do we draw boundaries between DFM modules?