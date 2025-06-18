# ISA-95 Roles vs Locations Flashcards
#flashcards/isa95/concepts

## Core Concept

What does ISA-95 deliberately decouple in its model?::ISA-95 decouples "who does what" (roles) from "where they sit" in the Purdue hierarchy

The eight production activity roles define ==what is done==, not ==how it should be organized==.

## Location Hierarchy (Purdue Model)

What are the typical Purdue model levels from top to bottom?
?
1. Enterprise - corporate planning, global ERP
2. Site - plant leadership, master scheduling
3. Area - process area / building
4. Work center - process cell / production line / storage zone
5. Equipment - reactors, conveyors, PLCs

Work center in ISA-95 is defined generically so it can be a ==process cell==, ==production unit==, ==line==, or even a ==storage zone==.

## Role Assignment Flexibility

Why does ISA-95 separate roles from organizational structure?
?
- The same function might live in MES, ERP, or shop-floor controllers
- Depends on regulation, safety, or cost drivers
- Companies draw different boundaries to suit their realities
- Keeps the model portable when boundaries shift

Activities (roles) represent ==what needs to be done== while locations represent ==where they are performed==.

## The Eight Production Roles

List all eight production roles/activities that must exist somewhere in the system
?
1. Product definition management
2. Production resource management
3. Detailed production scheduling
4. Production dispatching
5. Production execution management
6. Production data collection
7. Production tracking
8. Production performance analysis

These eight roles map ==one-to-one== with the eight generic Level 3 functions in ISA-95 Part 1.

## Assignment Patterns

Can a single role span multiple locations in the hierarchy?::Yes, roles can be distributed across multiple levels or locations

Can multiple roles exist in a single system or location?::Yes, one system can perform multiple roles/activities

Primary responsibility vs shared responsibility in role assignment means?
?
- Primary: The location that owns and drives the activity
- Shared/support: Locations that contribute to or support the activity

## Practical Implementation

What is the recommended approach when documenting architecture according to ISA-95?
?
Describe each activity role first ("what") BEFORE binding it to a system or organizational level ("where")

Why document roles before locations?::It keeps the model portable when boundaries inevitably shift

## Common Patterns

Where might Product Definition management typically have responsibilities?
?
- Enterprise: Owns specifications
- Site: Adapts specifications to site capabilities

Where is Data Collection typically performed?
?
- Work center: Raw signals
- Area: Aggregation
- Site: Further aggregation
<!--SR:!2025-06-19,1,230-->

Where does Dispatching typically occur?
?
- Area: Issues Job Orders
- Work center: Real-time dispatching

## Design Implications

What are the risks of concentrating many roles in one system?
?
- Creates a potential monolith
- Single point of failure
- Scaling challenges
- Change impact across multiple activities

What are the benefits of clearly separating roles from systems?
?
- Easier to reorganize systems without losing functionality
- Clear understanding of what must be preserved during changes
- Better interface design between systems
- Portable architecture patterns

When boundaries between systems change, the ==roles== remain constant but their ==location assignments== may shift.

## Key Takeaway

The separation of roles from locations allows companies to ==adapt the model to their specific organizational and system structures== while ensuring all necessary functions are covered.
