
Manufacturing sits between two very different worlds:  
*Level 4* enterprise planning & logistics, and *Level 2* process-control.  
ISA-95 bundles all traffic that crosses these boundaries into **four canonical
flow types** – think of them as the “verbs” of integration:

| Flow Type | Purpose | Typical Direction |
|-----------|---------|-------------------|
| **Product definition** | *What* & *how* to make | L4 → L3 → L2 |
| **Production capability** | What the plant *can* do | L2/L3 → L4 |
| **Production schedule** | *When/where* to make | L4 → L3 → L2 |
| **Production performance** | *What actually happened* | L2/L3 → L4 |

ISA-95 Part 3 makes these flows concrete for **production operations** with the
interfaces called out in §6.3:

* **Equipment & process specific production rules** – downloadable recipes, CNC
  programs, unit operations, etc. sent from Level 3 to Level 2    
* **Operational commands** – start/stop/setup instructions pushed to Level 2  .  
* **Operational responses** – acknowledgements / completion statuses coming back
  from Level 2 
* **Equipment & process specific data** – measurements and contextual data
  captured at Level 2 and bubbled upward 

### Putting it together  

```

        ┌──────────────────────┐          Product definition
        │ Enterprise (Level 4) │ ───────► Production schedule
        └─────────┬────────────┘          ▲
                  │                       │
                  │ Production performance│
                  ▼                       │
        ┌──────────────────────┐          │ Production capability
        │  Operations (Level 3)│──────────┘
        │  – Eight activity    │
        │    functions         │
        └─────────┬────────────┘
                  │  (rules / commands / data / responses)
                  ▼
        ┌──────────────────────┐
        │ Control (Level 2–1)  │
        └──────────────────────┘
```

> **Boundary note** – Not every request/response must cross the L3↔L4
> boundary; many stay entirely within manufacturing to handle rework,
> intermediates, or consumables


## Our Implementation Context

### System Architecture
- **Level 4**: Distributed Order Management (DOM) - *planned*
- **Level 3**: Factory Execution System (FES) - *existing*
- **Level 2/1**: Equipment controllers and automation

### Key Design Questions

We're mapping these four canonical flows to our DOM/FES integration:

1. **Product Definition Flow (L4 → L3 → L2)**
   - DOM maintains business product catalog
   - FES handles [[ISA-95 Part 3 - Section 6.4.3 Tasks in Product Definition Management|Product Definition Management]]
   - FES translates business products to work masters and equipment instructions

2. **Production Capability Flow (L2/L3 → L4)**
   - How does FES communicate manufacturing constraints to DOM?
   - Should DOM query FES for feasibility before order acceptance?
   - Real-time vs batch capability updates

3. **Production Schedule Flow (L4 → L3 → L2)**
   - DOM manages customer demand and order priorities
   - FES performs detailed scheduling considering equipment availability
   - Need clear handoff between business scheduling and shop floor sequencing

4. **Production Performance Flow (L2/L3 → L4)**
   - Shop floor data collection through FES
   - Aggregation and contextualization for business reporting
   - KPI calculation and performance metrics

### Insights from Our Study

From our [[ISA-95 Part 3 - Section 6.4.3 Tasks in Product Definition Management|Product Definition Management analysis]], we identified that the **Product Definition flow** is particularly complex in our environment due to:
- Multiple equipment platforms (10+ machine types)
- Need to separate abstract process definitions from equipment-specific details
- Current practice of using work orders as templates (mixing concerns)

### Implementation Considerations

1. **Asynchronous vs Synchronous Flows**
   - Which flows need real-time integration?
   - Where can we use event-driven patterns?

2. **Data Ownership Boundaries**
   - Clear separation between business data (DOM) and manufacturing data (FES)
   - Avoid data duplication while maintaining system autonomy

3. **Error Handling and Feedback Loops**
   - How do operational responses flow back to influence business decisions?
   - Exception handling across system boundaries

### Next Steps
- Map each flow type to specific integration points
- Define data models for each boundary crossing
- Establish governance for master data synchronization