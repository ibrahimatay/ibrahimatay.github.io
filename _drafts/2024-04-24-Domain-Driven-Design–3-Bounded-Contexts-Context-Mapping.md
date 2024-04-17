---
layout: post
author: İbrahim ATAY
title: "Domain Driven Design: Bounded Contexts & Context Mapping"
categories: [Domain Driven Design]
paginate: true
date: 2024-04-24
url: Domain-Driven-Design–3-Bounded-Contexts-Context-Mapping
---
# Introduction

Complexity is inevitable in software development. Designing and building large, complex systems can be challenging, especially when multiple teams and stakeholders are involved. Domain-Driven Design (DDD) is an approach used to manage this complexity and create better software systems.

![image](/assets/media/Domain-Driven-Design–3-Bounded-Contexts-Context-Mapping/Bounded-Contexts-Context-Mapping.jpg)

# Bounded Contexts and Context Mapping

Two fundamental concepts of DDD are Bounded Contexts and Context Mapping. These concepts help to break down the system into smaller, manageable parts and define the relationships between those parts.

# Bounded Contexts

A Bounded Context is a clear boundary that encapsulates a specific domain model, defining its scope, language, and rules.

- Acts as an autonomous unit within a larger system, ensuring consistency and reducing coupling.
- *Goals*:
    - ***Encapsulation***: Protects domain logic and data from external complexities, preventing unwanted coupling and side effects.
    - ***Consistency***: Provides a consistent model and a unified language within its boundaries, reducing misunderstandings and aligning with business goals.
    - ***Autonomy***: Allows each context to be developed and evolved independently, fostering agility and adaptability to changing requirements.

# Context Mapping

A technique that visually represents the relationships and interactions between Bounded Contexts in a system.

- Promotes alignment and avoids integration issues by clarifying how different contexts communicate and collaborate.
- *Goals*:
    - ***Visualization***: Provides a clear overview of the system's domain structure, facilitating understanding and communication among stakeholders.
    - ***Relationship Management***: Identifies potential integration challenges and suggests appropriate patterns to address them, enabling effective collaboration between contexts.
    - ***Collaboration Support***: Helps teams working on different contexts understand their dependencies and coordinate efforts, reducing inconsistencies and friction.


Primary Context Mapping Patterns

- Customer-Supplier
- Partnership
- Shared Kernel
- Conformist
- Anti-Corruption Layer
- Open Host Service
- Published Language

Benefits of Bounded Contexts and Context Mapping

- Improved Modularity
- Enhanced Communication
- Reduced Coupling
- Increased Agility
- Better Alignment with Business