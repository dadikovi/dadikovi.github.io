---
layout: post
title:  "Why every organization should create a design system"
date:   2020-10-02 12:34:19 +0200
categories: design
comments: true
---
The thinking procedure during implementation of a new user interface is the following:

![design-process](/images/design-process.png)

1. Design examples in sketch

    Visually they are perfect, but the structure of elements is not available or it is not completely suitable for implementing directly.
    
2. Decomposition of design examples

    The visual structure is tranformed into a tree-structure of design elements. Together with these elements, attributes and states of them are also identified.
    
    This "transformation" is actually a long sequence of design decisions, where we find the answer for this questions: 
    
    *Exactly what kind of objects with what kind of attributes can make the same look as I can see on the design plan?* 
    
    Most of the time within the implementation process is spent on this part.
    
    If some of the identified design elements is covered by the design system, lots of decisions has been already made, in this case the implementation process will be faster.
    
3. Abstraction into the design system

    By checking different examples of the same design element, general, abstract rules can be extracted. At the end of this process new components or sub-atoms are born in the design system.
    
    High quality decomposition and abstraction processes guarantee that any composition of the elements of the design system will result visually perfect and unified user interfaces.
    
    If the original design example is constructed from design elements of the design system, this whole process can be skipped, implementation gets much easier. 

## Why we need a design system

Basically a design system – from developer point of view – is not else than a large collection of design decisions, represented as design tokens, visual behaviors (css classes) and components.

The thing is, that **someone has to make these decisions**, before creating a new user interface. 

If a dedicated team does, the user interfaces will have a constant look-and-feel, the maintenance and implementation costs will be lower, and they can be estimated more precise.

Otherwise different developers must make the same decisions over and over again. Actually, the design system will be done, but unconsciously, with a much worse quality.
