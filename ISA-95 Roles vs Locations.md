
ISA-95 deliberately **decouples “who does what” (roles) from “where they sit”**
in the Purdue hierarchy.  Figure 6 reminds us that the **eight production
activity roles** are purely functional – they *“define what is done, not how it
should be organized”*  [oai_citation:5‡S_950003_62264_3_pdf.pdf](file-service://file-EvNgoVSnSuVbBHSqhDqddb).

## 1  Core production roles

1. Product definition management  
2. Production resource management  
3. Detailed production scheduling  
4. Production dispatching  
5. Production execution management  
6. Production data collection  
7. Production tracking  
8. Production performance analysis  [oai_citation:6‡S_950003_62264_3_pdf.pdf](file-service://file-EvNgoVSnSuVbBHSqhDqddb)

*These map one-to-one with the eight generic “Level-3” functions in Part 1.*

## 2  Location hierarchy (Purdue model excerpt)

| Purdue level | Typical scope examples |
|--------------|------------------------|
| **Enterprise** | corporate planning, global ERP |
| **Site** | plant leadership, master scheduling |
| **Area** | process area / building |
| **Work center** | process cell / production line / storage zone |
| **Equipment** | reactors, conveyors, PLCs |

> *“Work center” is defined generically so it can be a process cell,
> production unit, line, or even a storage zone*  [oai_citation:7‡S_950003_62264_3_pdf.pdf](file-service://file-EvNgoVSnSuVbBHSqhDqddb).

## 3  Assigning roles to locations   (illustrative matrix)

| Role ↓ / Location →  | Enterprise                                  | Site                         | Area                | Work center   |
| -------------------- | ------------------------------------------- | ---------------------------- | ------------------- | ------------- |
| Product definition   | ● owns specs                                | ○ adapts to site             |                     |               |
| Detailed scheduling  | ● DOM allocates order to plant & start date | ● Finite-capacity sequencing | ○ line-level        |               |
| Dispatching          |                                             | ○                            | ● issues Job Orders | ● real-time   |
| Execution mgmt       |                                             |                              | ○ supervises        | ●             |
| Data collection      |                                             | ○ aggregates                 | ●                   | ● raw signals |
| Tracking             |                                             | ○                            | ● batches           | ● units/lots  |
| Performance analysis | ● integrates KPI                            | ● OEE/site KPIs              | ○                   | ○             |

Legend: **●** primary responsibility ○ shared/support

## 4  Why roles ≠ org chart

Annex A shows multiple *lines of responsibility & technical integration*; the
same function might live in MES, ERP, or shop-floor controllers depending on
regulation, safety, or cost drivers
Consequently, companies draw different “role vs location” boundaries (Figure A.1
lines A–E) to suit their realities
### Practical takeaway  

*When documenting your own architecture, describe each activity role first
(“what”) **before** binding it to a system or organizational level (“where”).  
That keeps the model portable when boundaries inevitably shift.*


## How This Maps to Our Systems

See [[System Architecture Overview]] for our complete architecture.

### Role Assignments in Our Architecture

| Role | Primary System | Notes |
|------|---------------|--------|
| Product definition management | [[ISA-95 Part 3 - Section 6.4.3 Tasks in Product Definition Management\|FES]] | Manages work masters and production rules |
| Production resource management | FES | Equipment and tool management |
| Detailed production scheduling | FES (future: DOM?) | Currently in FES, may split with DOM |
| Production dispatching | FES | Work order release to shop floor |
| Production execution management | FES | Shop floor control |
| Production data collection | FES | Real-time data from equipment |
| Production tracking | FES | WIP and order status |
| Production performance analysis | FES → BI? | KPIs and analytics |

### Key Observations

1. **FES Concentration**: Currently, most Level 3 roles live in FES
   - Pro: Integrated operations management
   - Con: Potential monolith risk
   - See [[Open Questions - ISA-95 Mapping#13. System Ownership]]

2. **Blurred Boundaries**: Some roles span systems
   - Scheduling: QTO (capacity) vs DOM (orders) vs FES (detailed)
   - Product Definition: Part Service (data) vs DFM (analysis) vs FES (execution)

3. **Evolution Path**: As we decompose systems
   - Consider which roles should be extracted
   - Maintain clear interfaces between role implementations