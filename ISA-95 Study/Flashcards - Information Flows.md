# ISA-95 Information Flows Flashcards
#flashcards/isa95/part3/flows

## Four Canonical Information Flows

How many canonical information flows are defined in ISA-95 Part 3?::Four

What are the four canonical information flows in ISA-95?
?
1. Product Definition Flow
2. Production Capability Flow  
3. Product Request/Response Flow
4. Production Performance Flow

## Product Definition Flow

Product Definition Flow direction::Primarily from Level 4 to Level 3 (enterprise to control)

What information does Product Definition Flow carry?
?
- Product specifications
- Manufacturing rules
- Quality requirements
- Process definitions

Which activity function is central to Product Definition Flow?::Product Definition Management

## Production Capability Flow  

Production Capability Flow direction::From Level 3 to Level 4 (control to enterprise)

Production Capability Flow informs the enterprise about ==available capacity== and ==equipment capabilities==.

What key information does Production Capability Flow provide to Level 4?
?
- Available production capacity
- Equipment capabilities and constraints
- Resource availability
- Production line status

## Product Request/Response Flow

Product Request/Response Flow involves a ==bidirectional== exchange between Level 4 and Level 3.

What are the two parts of Product Request/Response Flow?
?
1. Product Request: Level 4 → Level 3 (what to make)
2. Product Response: Level 3 → Level 4 (what was made)

Product Request contains::Production orders, quantities, due dates, and priorities from the enterprise

Product Response contains::Actual production results, quantities completed, and quality outcomes

## Production Performance Flow

Production Performance Flow direction::From Level 3 to Level 4 (control to enterprise)

What information does Production Performance Flow carry?
?
- KPIs and metrics
- Production efficiency data
- Quality statistics
- Resource utilization
- Cost and time actuals

Which activity generates Production Performance Flow data?::Production Performance Analysis

## Flow Relationships

Product Definition Flow must occur ==before== Product Request Flow can be meaningful.

Why must Product Definition Flow precede Product Request Flow?::You cannot request production of something that hasn't been defined

Production Capability Flow influences ==production planning== at Level 4.

Which flow closes the feedback loop on production execution?::Production Performance Flow

## Key Concepts

The four information flows create a ==closed-loop== system between enterprise and control levels.

What is the primary purpose of separating these four flows?
?
To maintain clear separation of concerns:
- Definition (what/how to make)
- Capability (what can be made)  
- Execution (make it)
- Performance (how well it was made)

Information flows in ISA-95 always cross between ==Level 4== and ==Level 3==.
