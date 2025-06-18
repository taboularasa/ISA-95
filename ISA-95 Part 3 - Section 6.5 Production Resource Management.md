# ISA-95 Part 3 - Section 6.5 Production Resource Management

*Part of the [[ISA-95 Part 3 Activity Model Reference|Eight Generic Activity Functions]]*

## Overview
Production Resource Management (Activity 2) is defined as the collection of activities that manage the information about resources required by production operations, and relationships between resources. The resources include machines, tools, labour (with specific skill sets), materials and energy, as defined in the object models given in ISA-95 Part 1.

This activity supports the **Production Capability Flow** described in [[Information Flows – Enterprise ↔ Control  (ISA-95 Part 3 §6 & Figure 6)|ISA-95's four canonical information flows]].

## Key Interfaces (from Figure 8)

### Inputs:
- **Current information** (from Level 1-2 Functions)
- **Work Schedule** (from Detailed Production Scheduling)
- **Work Capability** information requests (from various activities)

### Outputs:
- **Personnel availability** (to Production Dispatching)
- **Equipment availability** (to Production Dispatching)
- **Material and energy availability** (to Production Dispatching)
- **Production capability** (to Level 4)
- **Work Capability** (to Detailed Production Scheduling and Production Analysis)

## Core Responsibilities

### 1. Resource Information Management
- Maintains information about all production resources
- Tracks relationships between resources
- Manages future availability reservations
- Provides resource definitions on demand or scheduled basis

### 2. Resource Types Managed
According to ISA-95, Production Resource Management handles three main resource types:
- **Personnel Resource Management** (Section 6.5.7)
- **Equipment Resource Management** (Section 6.5.8)
- **Material Resource Management** (Section 6.5.9)

### 3. Capability Reporting
Provides information on resource capability classified as:
- **Committed**: Already allocated to production
- **Available**: Ready for allocation
- **Unattainable**: Not available due to maintenance, failures, etc.

## Tasks in Production Resource Management (Section 6.5.3)

The standard defines specific tasks:

a) **Providing resource definitions** - Personnel, material, and equipment definitions to people, applications, or other activities

b) **Providing capability information** - Based on current statuses, future reservations, and future needs identified in production plans

c) **Ensuring resource acquisition** - Initiating requests to meet future operational capabilities

d) **Collecting resource information** - From shop floor, maintenance, receiving, and other sources

e) **Communicating resource issues** - Alerting dispatching when resources fail to meet requirements

## Resource-Specific Management

### Personnel Resource Management (6.5.7)
- Tracks operator skills and qualifications
- Manages skill profiles for task assignment
- Handles work period restrictions (unions, regulations)
- Tracks personnel availability and scheduling

### Equipment Resource Management (6.5.8)
- Manages equipment availability status
- Coordinates with maintenance for planned downtime
- Tracks equipment capability test results
- Handles preventive maintenance scheduling impacts

### Material Resource Management (6.5.9)
- Tracks material and energy availability
- Manages information about material conditions
- Handles material specification changes (QA test results)
- Maintains future material availability for scheduling

## Mapping to Our Architecture

See [[System Architecture Overview]] for complete system details.

### Where Resource Management Lives
In our architecture, Production Resource Management is primarily handled by **FES**, but with significant gaps:

- **Equipment Management**: Partially in FES
- **Tool Management**: Some in FES, needs enhancement
- **Personnel Management**: Minimal implementation
- **Material Management**: Split between FES and warehouse systems

### Key Integration Points
- **Maintenance Systems**: Equipment availability updates
- **HR Systems**: Personnel availability (not integrated)
- **Warehouse Management**: Material availability
- **Quality Systems**: Material specification changes

## Areas of Divergence from ISA-95

1. **Fragmented Resource Data**: ISA-95 assumes centralized resource management; we have it scattered
2. **Limited Capability Reporting**: We don't formally report committed/available/unattainable
3. **Manual Personnel Management**: No automated skill/qualification tracking
4. **Reactive vs Proactive**: We react to resource issues rather than predict them

## Related Concepts
- [[ISA-95 Part 3 Activity Model Reference]] - The eight activities
- [[Understanding ISA-95 Activity Model]] - Conceptual framework
- [[ISA-95 Roles vs Locations]] - Where resource management can be performed
- [[System Architecture Overview]] - Our implementation