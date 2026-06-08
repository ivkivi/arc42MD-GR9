# Quality Requirements

## Content

This section contains all relevant quality requirements.

The most important quality requirements have already been described in section 1.2, Quality Goals, and should therefore only be referenced here.

This section can also include quality requirements with lower importance. These requirements may not create high risks if they are not fully achieved, but they can still be useful or nice to have.

## Motivation

Quality requirements have a strong influence on architectural decisions.

Therefore, it is important to know which qualities are really important for stakeholders in a specific and measurable way.

## Further Information

- See the arc42 documentation: [Quality Requirements](https://docs.arc42.org/section-10/)
- See the Q42 quality model: [quality.arc42.org](https://quality.arc42.org)

## Quality Requirements Overview

### Content

This section gives an overview or summary of quality requirements.

### Motivation

In many projects, there are many detailed quality requirements.

This overview should summarize them, for example by using categories or topics such as ISO 25010 or Q42.

If these summary descriptions are already precise, specific, and measurable enough, the detailed quality scenarios section may be skipped.

### Form

Use a simple table in which each row contains a category or topic and a short description of the quality requirement.

Alternatively, a mind map or a quality attribute tree can be used to structure the quality requirements.

A quality attribute tree uses the generic term “quality” as the root and refines it into more specific quality attributes.

Bass, Clements, and Kazman introduced the term “Quality Attribute Utility Tree” for this purpose.

## Quality Scenarios

### Content

Quality scenarios make quality requirements concrete and help decide whether they are fulfilled, in the sense of acceptance criteria.

Scenarios should be specific and measurable.

Two kinds of scenarios are especially useful:

- **Usage scenarios**, also called application scenarios or use case scenarios, describe the system’s runtime reaction to a certain stimulus. This also includes scenarios that describe efficiency or performance.
  - Example: The system reacts to a user’s request within one second.
- **Change scenarios** describe the desired effect of a modification or extension of the system or its immediate environment.
  - Example: Additional functionality is implemented, or requirements for a quality attribute change, and the effort or duration of the change is measured.

### Form

Typical information for detailed scenarios includes the following.

In short form, as favored in the Q42 model:

- **Context / Background**: What kind of system or component is involved, and what is the environment or situation?
- **Source / Stimulus**: Who or what initiates or triggers a behavior, reaction, or action?
- **Metric / Acceptance Criteria**: A response including a measure or metric.

The long form of scenarios, favored by the SEI and Bass et al., is more detailed and includes:

- **Scenario ID**: A unique identifier for the scenario.
- **Scenario Name**: A short, descriptive name for the scenario.
- **Source**: The entity, such as a user, system, or event, that initiates the scenario.
- **Stimulus**: The triggering event or condition the system must address.
- **Environment**: The operational context or condition under which the system experiences the stimulus.
- **Artifact**: The building blocks or other elements of the system affected by the stimulus.
- **Response**: The outcome or behavior the system exhibits in reaction to the stimulus.
- **Response Measure**: The criteria or metric by which the system’s response is evaluated.

### Examples

See the Q42 quality model website for detailed examples of quality requirements: [quality.arc42.org](https://quality.arc42.org)

### Further Information

- Len Bass, Paul Clements, Rick Kazman: *Software Architecture in Practice*, 4th Edition, Addison-Wesley, 2021.