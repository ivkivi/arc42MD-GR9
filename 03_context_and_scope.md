# Context and Scope

## Contents

Context and scope, as the name suggests, delimit your system, meaning your scope, from all its communication partners, such as neighboring systems and users, meaning the context of your system. It thereby specifies the external interfaces.

If necessary, differentiate the business context, meaning domain-specific inputs and outputs, from the technical context, meaning channels, protocols, and hardware.

## Motivation

The domain interfaces and technical interfaces to communication partners are among your system's most critical aspects. Make sure that you completely understand them.

## Form

Various options:

- Context diagrams
- Lists of communication partners and their interfaces

## Further Information

See the arc42 documentation: [Context and Scope](https://docs.arc42.org/section-3/)

## Business Context

### Contents

Specification of **all** communication partners, such as users and IT systems, with explanations of domain-specific inputs and outputs or interfaces.

Optionally, you can add domain-specific formats or communication protocols.

### Motivation

All stakeholders should understand which data are exchanged with the environment of the system.

### Form

All kinds of diagrams that show the system as a black box and specify the domain interfaces to communication partners.

Alternatively or additionally, you can use a table.

The title of the table is the name of your system. The three columns contain the name of the communication partner, the inputs, and the outputs.

**<Diagram or Table>**

**<optionally: Explanation of external domain interfaces>**

## Technical Context

### Contents

Technical interfaces, such as channels and transmission media, link your system to its environment.

In addition, there should be a mapping of domain-specific input/output to the channels, meaning an explanation of which input/output uses which channel.

### Motivation

Many stakeholders make architectural decisions based on the technical interfaces between the system and its context.

Especially infrastructure or hardware designers decide these technical interfaces.

### Form

For example, a UML deployment diagram describing channels to neighboring systems, together with a mapping table showing the relationships between channels and input/output.

**<Diagram or Table>**

**<optionally: Explanation of technical interfaces>**

**<Mapping Input/Output to Channels>**