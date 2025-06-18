# ISA-95 Part 3 - Section 6.7 Production Dispatching

*Part of the [[ISA-95 Part 3 Activity Model Reference|Eight Generic Activity Functions]]*

## Overview
Production Dispatching (Activity 4) is defined as the collection of activities that manage the flow of production by dispatching production to equipment and personnel. This activity serves as the critical link between planning/scheduling and actual execution.

This activity is central to the **Product Request/Response Flow** described in [[Information Flows – Enterprise ↔ Control  (ISA-95 Part 3 §6 & Figure 6)|ISA-95's four canonical information flows]].

## Key Interfaces (from Figure 13)

### Inputs:
- **Work Schedule** (from Detailed Production Scheduling)
- **Work Master** (from Product Definition Management)
- **Resource Network** (from Production Resource Management)
- **Work Capability** information
- **Work Alerts** (from Production Execution, Data Collection, Tracking)

### Outputs:
- **Job List** (to Production Execution Management and Production Tracking)
- Work assignments to various resources
- Status and progress information

## Core Responsibilities

### Primary Functions
According to ISA-95, Production Dispatching may include:
a) Scheduling batches to start in a batch control system
b) Scheduling production runs to start in production lines
c) Specifying standard operating condition targets in production units
d) Sending job orders to work centers
e) Issuing job orders for manual operations

### Examples of Dispatched Job Orders
- Machine set-up
- Grade change switchovers
- Equipment cleaning
- Run rate set-up
- Production flow set-up

## Tasks in Production Dispatching (Section 6.7.3)

The standard defines four key tasks:

### a) Issuing job orders as identified by the schedule
- Converts work schedule into executable job orders
- Ensures proper sequencing and timing

### b) Assigning local resources to production
- Personnel assignment
- Equipment allocation
- Material assignment
- Storage and other resource allocation

### c) Releasing local resources to start job orders
- Authorizes start of production
- Ensures all prerequisites are met

### d) Handling conditions not anticipated in the work schedule
- Managing workflow disruptions
- Buffer management
- Coordinating rework and salvage processes
- Communicating changes to scheduling and tracking

## Job List for Production (Section 6.7.4)

The Job List is the primary output of Production Dispatching:
- Collection of job orders for production
- Includes sequencing instructions
- Assigns resources to specific work centers
- Contains information needed by Production Execution

**Figure 14 Example**: Shows how job lists map work requests to specific resources (process cells, production lines, storage zones) over time

## Work Assignment Activities (Section 6.7.6)

Production Dispatching includes:
- **Material Assignment**: Allocating specific lots/batches to job orders
- **Equipment Assignment**: Designating specific machines/units
- **Personnel Assignment**: Allocating operators with required skills
- **Storage Assignment**: Designating input/output locations

Additional capabilities:
- Work-in-process control through buffer management
- Rework and salvage process management
- Job cancellation or reduction when needed

## Mixed Facility Example (Figure 15)

The standard provides an example of dispatching in a mixed facility:
- **Continuous premix operation**: Job lists specify set-up and initial charging
- **Batch primary production**: Defines sequence of batches
- **Discrete packaging**: Defines set-up of back-end packaging system

This demonstrates how dispatching adapts to different production modes within a single facility.

## Mapping to Our Architecture

See [[System Architecture Overview]] and [[TMS and Production Dispatching Mapping]] for detailed implementation analysis.

### Where Production Dispatching Lives
In our architecture, Production Dispatching is primarily implemented in **TMS (Task Management System)** with support from **FES**:

- **TMS**: Performs the core dispatching logic
  - Receives tasks from producers (mainly FES)
  - Manages station queues
  - Implements rule-based assignment
  - Tracks task state transitions

- **FES**: Acts as primary task producer
  - Generates work order tasks
  - Provides work masters and routing
  - Handles completion notifications

### Key Implementation Details
1. **Pull-based Model**: Stations poll TMS for tasks (vs ISA-95's push assumption)
2. **Centralized Service**: Single TMS aggregates all tasks (vs distributed dispatching)
3. **Clear Separation**: TMS owns assignment, stations own execution
4. **Real-time Updates**: Event-driven task state changes

## Areas of Divergence from ISA-95

1. **Centralized vs Distributed**: ISA-95 assumes dispatching might be distributed; we centralize in TMS
2. **Pull vs Push**: We use pull-based (stations request work) vs push-based dispatching
3. **Limited Resource Assignment**: TMS focuses on station assignment; other resources handled elsewhere
4. **Simplified Job Structure**: Our tasks are simpler than ISA-95's comprehensive job orders

## Related Concepts
- [[ISA-95 Part 3 Activity Model Reference]] - The eight activities
- [[ISA-95 Part 3 - Section 6.6 Detailed Production Scheduling|Detailed Production Scheduling]] - Provides work schedule input
- [[TMS and Production Dispatching Mapping]] - Detailed mapping analysis
- [[Understanding ISA-95 Activity Model]] - Conceptual framework
- [[System Architecture Overview]] - Our implementation