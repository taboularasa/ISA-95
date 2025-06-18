# ISA-95 Flashcard Creation Guide

## Purpose
Create spaced repetition flashcards to master ISA-95 concepts, focusing on:
- Standard definitions and terminology
- Relationships between concepts
- Level interactions
- Information flows
- Activity models

## Flashcard Best Practices

### What to Include
- ISA-95 standard definitions
- Conceptual relationships (e.g., "X receives input from Y")
- Level responsibilities
- Information flow patterns
- Activity functions and their interfaces

### What to Avoid
- Implementation-specific details
- Company-specific mappings
- Technical implementation choices
- System names from our architecture

## Formatting Guide

### Single-line Q&A
```
Question::Answer
```
Example: `What level handles detailed production scheduling?::Level 3`

### Multi-line Q&A
```
Complex question that needs multiple lines?
?
- Point 1
- Point 2
- Point 3
```

### Cloze Deletions
```
The ==hidden text== will be blanked out during review.
```

### Reversed Cards (creates 2 cards)
```
Term:::Definition
```
This creates both Term→Definition and Definition→Term cards.

## Deck Organization

Use hierarchical tags:
- `#flashcards/isa95/overview` - General concepts
- `#flashcards/isa95/part1` - Part 1 models and terminology
- `#flashcards/isa95/part2` - Part 2 object models
- `#flashcards/isa95/part3/activities` - Part 3 activity models
- `#flashcards/isa95/part3/flows` - Part 3 information flows
- `#flashcards/isa95/part4` - Part 4 operations models
- `#flashcards/isa95/part5` - Part 5 B2M transactions

## Review Schedule

The plugin will automatically schedule reviews using spaced repetition. After reviewing a card:
- Easy: Longer interval
- Good: Normal interval
- Hard: Shorter interval
- Again: Reset to beginning

## Creating Flashcards from Notes

When reading ISA-95 sections:
1. Identify key concepts and definitions
2. Note relationships between elements
3. Capture level interactions
4. Document information flows
5. Create cards immediately while context is fresh

## Example Topics for Flashcards

### Terminology
- Eight generic activity functions
- Four information flows
- Level definitions and responsibilities
- Object model components

### Relationships
- Which activities feed into others
- What information flows between levels
- Dependencies between functions

### Concepts
- Why certain functions exist at specific levels
- Design principles behind the standard
- Separation of concerns in the model
