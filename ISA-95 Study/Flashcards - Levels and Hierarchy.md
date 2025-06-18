# ISA-95 Levels and Hierarchy Flashcards
#flashcards/isa95/fundamentals

## Purdue Model Levels

How many levels are in the Purdue Enterprise Reference Architecture?::5 levels (0-4)

What are the five levels of the Purdue model from bottom to top?
?
- Level 0: Physical Process
- Level 1: Basic Control
- Level 2: Area Supervisory Control
- Level 3: Manufacturing Operations Management
- Level 4: Business Planning and Logistics

## Level 0 - Physical Process

Level 0 represents the ==physical process== itself - the actual production equipment and processes.

What exists at Level 0?::The actual physical production process - equipment doing the work

## Level 1 - Basic Control

Level 1 contains ==sensors== and ==actuators== that directly interface with the physical process.

What are typical Level 1 devices?
?
- Sensors (temperature, pressure, flow)
- Actuators (valves, motors)
- Local indicators
- Basic I/O devices

## Level 2 - Area Supervisory Control

Level 2 performs ==supervisory control== and ==data acquisition== (SCADA).

What are typical Level 2 systems?
?
- PLCs (Programmable Logic Controllers)
- DCS (Distributed Control Systems)
- HMIs (Human Machine Interfaces)
- SCADA systems

Level 2 provides ==real-time control== of the manufacturing process.

## Level 3 - Manufacturing Operations Management

Level 3 is responsible for ==managing== and ==optimizing== the production operations.

What is the timeframe for Level 3 operations?::Days, shifts, hours, minutes

ISA-95 primarily focuses on defining ==Level 3== activities and their interfaces with ==Level 4==.

What are typical Level 3 systems?
?
- MES (Manufacturing Execution Systems)
- LIMS (Laboratory Information Management Systems)
- WMS (Warehouse Management Systems)
- Batch Management Systems

## Level 4 - Business Planning and Logistics

Level 4 handles ==business planning== and ==logistics== for the manufacturing enterprise.

What is the timeframe for Level 4 operations?::Months, weeks, days

What are typical Level 4 systems?
?
- ERP (Enterprise Resource Planning)
- SCM (Supply Chain Management)
- CRM (Customer Relationship Management)
- Financial systems

## ISA-95 Focus

Which levels does ISA-95 primarily address?::The interface between Level 3 and Level 4

ISA-95 defines the ==activities==, ==information flows==, and ==objects== exchanged between Levels 3 and 4.

## Level Characteristics

What is the key difference in time horizons between levels?
?
- Level 1-2: Real-time (seconds, milliseconds)
- Level 3: Operations time (minutes, hours, shifts)
- Level 4: Business time (days, weeks, months)

As you go up the hierarchy, the time horizon ==increases== and the level of detail ==decreases==.

## Information Flow

Information flows ==bidirectionally== between adjacent levels in the hierarchy.

What type of information typically flows from Level 4 to Level 3?
?
- Production schedules
- Product definitions
- Material requirements
- Business objectives

What type of information typically flows from Level 3 to Level 4?
?
- Production performance
- Actual production
- Resource utilization
- Quality data

## Common Misconceptions

Must each level be implemented as a separate system?::No, levels represent functional layers, not necessarily separate systems

Can functions from different levels exist in the same system?::Yes, but it's important to maintain clear separation of concerns

The Purdue model describes ==functional hierarchy==, not ==system architecture==.

## Key Design Principle

Why is it important to respect level boundaries?
?
- Different time scales require different technologies
- Separation of concerns improves maintainability
- Clear interfaces enable system evolution
- Prevents real-time systems from being burdened by business logic

Level separation ensures that ==real-time control== is not compromised by ==business processing==.
