# Building Block View

## Content

The building block view shows the static decomposition of the system into building blocks, such as modules, components, subsystems, classes, interfaces, packages, libraries, frameworks, layers, partitions, tiers, functions, operations, and data structures, as well as their dependencies, relationships, and associations.

This view is mandatory for every architecture documentation.

In analogy to a house, this is the **floor plan**.

## Motivation

Maintain an overview of your source code by making its structure understandable through abstraction.

This allows you to communicate with your stakeholders on an abstract level without disclosing implementation details.

## Form

The building block view is a hierarchical collection of black boxes and white boxes and their descriptions.

![Hierarchy of building blocks](../images/05_building_blocks-EN.png)

**Level 1** is the white box description of the overall system together with black box descriptions of all contained building blocks.

**Level 2** zooms into some building blocks of level 1. Thus, it contains the white box description of selected building blocks of level 1, together with black box descriptions of their internal building blocks.

**Level 3** zooms into selected building blocks of level 2, and so on.

## Further Information

See the arc42 documentation: [Building Block View](https://docs.arc42.org/section-5/)

## Whitebox Overall System

Here you describe the decomposition of the overall system using the following white box template. It contains:

- an overview diagram
- a motivation for the decomposition
- black box descriptions of the contained building blocks

For the black box descriptions, you can either:

- use one table for a short and pragmatic overview of all contained building blocks and their interfaces
- use a list of black box descriptions of the building blocks according to the black box template

Depending on your tool, this list could be sub-chapters in text files, sub-pages in a Wiki, or nested elements in a modeling tool.

Optionally, you can describe important interfaces that are not explained in the black box templates of a building block but are very important for understanding the white box.

Since there are many ways to specify interfaces, there is no specific template for them. In the worst case, you have to specify and describe syntax, semantics, protocols, error handling, restrictions, versions, qualities, necessary compatibilities, and more.

In the best case, examples or simple signatures are sufficient.

**<Overview Diagram>**

### Motivation

_<text explanation>_

### Contained Building Blocks

_<Description of contained building block black boxes>_

### Important Interfaces

_<Description of important interfaces>_

## Black Boxes Level 1

You can describe black boxes from level 1 in tabular form:

| **Name** | **Responsibility** |
|---|---|
| _<black box 1>_ | _<Text>_ |
| _<black box 2>_ | _<Text>_ |

Alternatively, use a separate black box template for every important building block.

### <Name black box 1>

Here you describe `<black box 1>` according to the following black box template:

- Purpose / Responsibility
- Interfaces, when they are not extracted as separate paragraphs
- Optional quality or performance characteristics, such as availability or runtime behavior
- Optional directory or file location
- Optional fulfilled requirements, if traceability to requirements is needed
- Optional open issues, problems, or risks

_<Purpose/Responsibility>_

_<Interface(s)>_

_<(Optional) Quality/Performance Characteristics>_

_<(Optional) Directory/File Location>_

_<(Optional) Fulfilled Requirements>_

_<(Optional) Open Issues/Problems/Risks>_

### <Name black box 2>

_<black box template>_

### <Name black box n>

_<black box template>_

### <Name interface 1>

...

### <Name interface m>

## Level 2

Here you can specify the inner structure of some building blocks from level 1 as white boxes.

You have to decide which building blocks of your system are important enough to justify such a detailed description.

Prefer relevance over completeness. Specify important, surprising, risky, complex, or volatile building blocks.

Leave out normal, simple, boring, or standardized parts of your system.

### White Box _<building block 1>_

Describes the internal structure of _building block 1_.

_<white box template>_

### White Box _<building block 2>_

_<white box template>_

...

### White Box _<building block m>_

_<white box template>_

## Level 3

Here you can specify the inner structure of some building blocks from level 2 as white boxes.

When you need more detailed levels of your architecture, copy this part of arc42 for additional levels.

### White Box _<building block x.1>_

Specifies the internal structure of _building block x.1_.

_<white box template>_

### White Box _<building block x.2>_

_<white box template>_

### White Box _<building block y.1>_

_<white box template>_