# ISA-95 Eight Generic Activity Functions Flashcards
#flashcards/isa95/part3/activities

## The Eight Functions

How many generic activity functions are defined in ISA-95 Part 3?::Eight

List all eight generic activity functions in ISA-95 Part 3
?
1. Resource Management
2. Definition Management  
3. Dispatching
4. Execution Management
5. Data Collection
6. Tracking
7. Analysis
8. Disposition (added in Part 3)

## Resource Management Functions

Resource Management in ISA-95 manages ==personnel==, ==equipment==, and ==material== resources.

What are the three types of Resource Management in ISA-95?
?
1. Personnel Resource Management
2. Equipment Resource Management  
3. Material Resource Management

Personnel Resource Management::Manages the personnel resources within Level 3 manufacturing operations

Equipment Resource Management::Manages the equipment resources and their status/availability

Material Resource Management::Manages raw materials, intermediate materials, and finished goods inventory

## Definition Management Functions  

How many types of Definition Management exist in ISA-95?::Two

What are the two types of Definition Management?
?
1. Product Definition Management
2. Process Definition Management

Product Definition Management:::Manages what products can be made and their specifications

Process Definition Management:::Manages how products are made (the manufacturing processes)

## Production Functions

Detailed Production Scheduling::Creates the production schedule based on production requests

Production Dispatching::Manages the flow of production by dispatching work to work centers

Production Execution Management::Manages and directs the execution of work within Level 3

Production Data Collection::Collects production data from Level 2 functions

Production Tracking::Tracks production against the production schedule and production requests

Production Performance Analysis::Analyzes production performance and generates KPIs

## Information Flow Relationships

Production Dispatching receives input from ==Product Definition Management== in the form of Work Masters.

Which activity provides the production schedule to Production Dispatching?::Detailed Production Scheduling

Production Performance Analysis sends ==KPI definitions== to Product Definition Management.

## Level Interactions

All eight generic activity functions operate at which ISA-95 level?::Level 3 (Manufacturing Operations Management)

Level 3 activities receive production requests from ==Level 4== and send production responses back to ==Level 4==.

## Key Concepts

What is the difference between Definition Management and Execution Management?
?
- Definition Management: Defines WHAT can be made and HOW to make it
- Execution Management: Actually manages the making of products

The ==Dispatching== function serves as the bridge between planning/scheduling and actual execution.

Why was Disposition added as the 8th function in Part 3?::To handle the management of production outputs, quality decisions, and material disposition
