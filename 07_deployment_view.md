# Deployment View

## Content

The deployment view describes:

1. the technical infrastructure used to execute the system, including infrastructure elements such as:
   - geographical locations
   - environments
   - computers
   - processors
   - channels
   - network topologies
   - other infrastructure elements

2. the mapping of software building blocks to these infrastructure elements.

Often, systems are executed in different environments, such as development, test, and production environments. In such cases, all relevant environments should be documented.

A deployment view should especially be documented if the software is executed as a distributed system with more than one computer, processor, server, or container, or when custom hardware processors and chips are designed and constructed.

From a software perspective, it is sufficient to capture only those infrastructure elements that are needed to show the deployment of the building blocks.

Hardware architects can go beyond that and describe the infrastructure in as much detail as needed.

## Motivation

Software does not run without hardware.

The underlying infrastructure can influence the system and some cross-cutting concepts. Therefore, the infrastructure needs to be known and documented.

## Form

A highest-level deployment diagram may already be included in section 3.2 as the technical context, with the system’s own infrastructure shown as one black box.

In this section, that black box can be expanded using additional deployment diagrams.

Possible forms are:

- UML deployment diagrams, possibly with nested diagrams when the infrastructure is more complex
- other diagram types that show nodes and channels of the infrastructure, especially when preferred by hardware stakeholders

## Further Information

See the arc42 documentation: [Deployment View](https://docs.arc42.org/section-7/)

## Infrastructure Level 1

Describe, usually with a combination of diagrams, tables, and text:

- distribution of the system across multiple locations, environments, computers, processors, and similar infrastructure elements
- physical connections between these elements
- important justifications or motivations for this deployment structure
- quality and/or performance features of this infrastructure
- mapping of software artifacts to elements of this infrastructure

For multiple environments or alternative deployments, copy and adapt this section for all relevant environments.

**<Overview Diagram>**

### Motivation

_<explanation in text form>_

### Quality and/or Performance Features

_<explanation in text form>_

### Mapping of Building Blocks to Infrastructure

_<description of the mapping>_

## Infrastructure Level 2

Here you can include the internal structure of some infrastructure elements from level 1.

Copy the structure from level 1 for each selected element.

### _<Infrastructure Element 1>_

_<diagram + explanation>_

### _<Infrastructure Element 2>_

_<diagram + explanation>_

...

### _<Infrastructure Element n>_

_<diagram + explanation>_