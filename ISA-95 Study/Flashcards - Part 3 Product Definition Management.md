# ISA-95 Part 3 - Product Definition Management Flashcards
#flashcards/isa95/part3/activities

## Core Concepts

What is the primary purpose of Product Definition Management in ISA-95?::To serve as the bridge between what the business wants to produce (Level 4) and how production actually executes (Level 2)

Product Definition Management is one of the ==eight core production activities== in ISA-95's Level 3 operations management.

Which ISA-95 information flow is Product Definition Management central to?::Product Definition Flow

## Key Interfaces

What are the three main inputs to Product Definition Management according to Figure 7?
?
1. Product Definition (from Level 4)
2. Equipment and process specific production rules (from Level 1-2)  
3. KPI Definitions (from Production Analysis)

What are the main outputs from Product Definition Management?
?
- Product Definition (to Production Dispatching)
- Work Master (to Production Dispatching)
- Interfaces with Detailed Production Scheduling
- Sends production definitions to Production Execution Management

Work Master::Contains work center specific product production rules and detailed production routing

## Core Responsibilities

What are the three core responsibilities of Product Definition Management?
?
1. Product Information Management
2. Work Master Development
3. Production Rule Management

Product Information Management involves ==translating enterprise product definitions into manufacturing-specific formats==.

What does Work Master Development include?
?
- Creates work center-specific production rules
- Defines detailed production routing
- Specifies equipment capabilities and constraints
- Maps abstract product requirements to concrete production steps

## ISA-95 Design Patterns

Process Master:::Defines HOW to make something (equipment-agnostic)

Work Master:::Executable combination of Process Master + Equipment Capabilities

What is the recommended ISA-95 pattern for separating process from equipment?
?
Process Master (abstract HOW)
    ↓
+ Equipment Capabilities  
    ↓
= Work Master (executable)

## Level Interactions

At which level does Product Definition Management operate in ISA-95?::Level 3 (Operations Management)

Product Definition Management receives product definitions from ==Level 4== and equipment rules from ==Level 1-2==.

## Key Terminology

What is the difference between a Process Master and a Work Master?
?
- Process Master: Equipment-agnostic definition of HOW to make something
- Work Master: Executable instructions combining process with specific equipment capabilities

The ==Work Master== contains work center specific product production rules and detailed production routing.
