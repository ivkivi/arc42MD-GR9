# Runtime View

## Contents

The runtime view describes concrete behavior and interactions of the system’s building blocks in the form of scenarios from the following areas:

- important use cases or features: how building blocks execute them
- interactions at critical external interfaces: how building blocks cooperate with users and neighboring systems
- operation and administration, such as launch, start-up, and stop
- error and exception scenarios

The main criterion for choosing possible scenarios, sequences, or workflows is their **architectural relevance**.

It is **not** important to describe a large number of scenarios. Instead, a representative selection should be documented.

## Motivation

You should understand how instances of the building blocks of your system perform their tasks and communicate at runtime.

Scenarios are mainly captured in the documentation to communicate the architecture to stakeholders who are less willing or able to read and understand static models, such as the building block view or deployment view.

## Form

There are many notations for describing scenarios, for example:

- numbered lists of steps in natural language
- activity diagrams or flow charts
- sequence diagrams
- BPMN or EPCs, meaning event process chains
- state machines

## Further Information

See the arc42 documentation: [Runtime View](https://docs.arc42.org/section-6/)

## <Runtime Scenario 1>

- _<insert runtime diagram or textual description of the scenario>_
- _<insert description of the notable aspects of the interactions between the building block instances depicted in this diagram>_

## <Runtime Scenario 2>

## ...

## <Runtime Scenario n>