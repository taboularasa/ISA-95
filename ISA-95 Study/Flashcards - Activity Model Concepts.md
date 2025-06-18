# ISA-95 Activity Model Concepts Flashcards
#flashcards/isa95/part3/concepts

## Core Purpose

What fundamental question does the ISA-95 Activity Model answer?::"What work needs to be done to run manufacturing operations, regardless of how you organize it?"

The Activity Model identifies the irreducible =="verbs"== of manufacturing operations.

## Why Activities Not Systems

Why does ISA-95 describe activities rather than systems?
?
1. Technology changes, activities don't
2. Organizations vary in their implementations
3. System boundaries shift with reorgs and upgrades

Activities represent ==what needs to be done== while systems represent ==software that does it==.

## The Checklist Approach

What question does each of the eight activities answer?
?
1. Product Definition - Do we know HOW to make products?
2. Resource Management - Do we know WHAT resources we have?
3. Detailed Scheduling - Do we know WHEN to make things?
4. Dispatching - Can we START production?
5. Execution Management - Can we CONTROL production?
6. Data Collection - Can we CAPTURE what happened?
7. Tracking - Can we TRACE products through production?
8. Performance Analysis - Can we IMPROVE based on results?

If any activity is missing, you have a ==gap in your operations capability==.

## Network vs Hierarchy

How should the eight activities be viewed in terms of their relationships?::As a network of interactions, not a hierarchy or sequence

Activities happen in ==parallel== with ==feedback loops==, not in sequence.

## Information Flow Examples

What does Product Definition tell Scheduling?::"Here's what can be made"

What does Resource Management tell Scheduling?::"Here's what we have to work with"

What does Scheduling tell Dispatching?::"Here's the sequence"

What does Performance Analysis tell other activities?::"Here's how we actually performed"

The magic is in the ==interfaces== between activities, not just the activities themselves.

## Functional Decomposition

The Activity Model represents breaking down "run manufacturing" into what?
?
Essential functions:
- Know what to make
- Know what you have
- Decide when to make it
- Start making it
- Control the making
- Record what happened
- Track where things are
- Learn from results

This decomposition helps ensure ==nothing falls through the cracks==.

## Design Questions

When designing a new system, what three questions should you ask about activities?
?
1. Which activities are we moving/splitting?
2. What are the interfaces?
3. Are we creating gaps?

## Common Pitfalls

What are four common pitfalls when working with the Activity Model?
?
1. Thinking activities = systems
2. Ignoring the interfaces between activities
3. Sequential thinking instead of parallel
4. Level confusion (mixing L3 with L4 activities)

One system can do ==multiple activities==, and one activity can ==span systems==.

## Architecture Implications

What does it mean if one system owns 7 of 8 activities?
?
- Creates a monolith
- System is critical - if it fails, everything stops
- Changes to any activity might impact others
- Scaling challenges - can't scale activities independently

An orphaned activity is one that has ==no clear system owner==.

## The Bottom Line

The Activity Model is a ==functional architecture== for manufacturing operations.

What is your job when implementing ISA-95's Activity Model?
?
1. Ensure all eight activities are covered
2. Design clean interfaces between them
3. Assign them to systems in a way that makes sense
4. Monitor that no activity becomes orphaned during evolution

## Key Insight

Why is the Activity Model considered a "completeness check"?::It ensures that all essential manufacturing operations functions are addressed somewhere in your Level 3 systems

The Activity Model helps identify ==gaps== and ==overlaps== in your manufacturing systems architecture.
