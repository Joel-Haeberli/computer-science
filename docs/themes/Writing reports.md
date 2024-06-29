tags: #web-security

# Writing reports

links: [[507 WS TOC - Testing|WS TOC - Testing]] - [[themes/000 Index|Index]]

---

Before we can write a report we need to value the risks.

## Value the real risk

First some definitions that are needed for the calculation.

### Definitions

Each indicator has a score between 1 and 9. 1 means low/small/easy and 9 means high/big/hard.

- Threat agent factors
	- Skill level
	- Motive
	- Opportunity
	- Size
- Vulnerability factors
	- Ease of discovery
	- Ease of exploit
	- Awareness
	- Intrusion detection
- Technical impact
	- Loss of confidentiality
	- Loss of integrity
	- Loss of availability
	- Loss of accountability
- Business impact
	- Financial damage
	- Reputation damage
	- Non-compliance
	- Privacy violation

### Calculations

 $$\text{Risk} = \text{likelihood} \times \text{impact}$$

To find both of those variables several steps are defined:

1. First identify a risk
2. Assess likelihood factors (threat agent and vulnerability)
3. Assess impact factors (technical and business)
4. Calculate the risk
5. Decide what should be fixed
6. Adapt your risk rating model


Then you arrive at this final formula:

$$\text{Risk} = \frac{\text{thread agent factors} + \text{vulnerability factors}}{2} \times \frac{\text{technical impacts} + \text{business impacts}}{2}$$
## Write the report

The report is structured as follows:

1. **Executive Summary**:
    - Provide an overview that is easily understandable, summarizing key findings and recommendations.
2. **Technical Management Overview**:
    - Contains more details than the executive summary.
    - Describe the scope of the assessment.
    - List the targets included and any caveats, such as system availability.
    - Provide an introduction to the risk rating methodology used.
    - Offer a technical summary of the findings​​.
3. **Assessment Findings**:
    - Target the technical level and include all necessary information.
    - For each control tested:
        - Write a technical description of the issue found.
        - Include a section on resolving the issue.
        - Provide the risk rating and the impact value of the finding.
    - Document whether a control has been tested and its results​​.
4. **Toolbox**:
    - Describe the methodology used in the assessment.
    - Detail the technological tools used for testing.
    - Indicate the thoroughness of the assessment and the areas that were included in the test​​.

## Conclusion

- Formalism: Make sure to not forget anything
- Multiple techniques : Combine findings where necessary
- Biggest issue: **Social engineering**

---
links: [[507 WS TOC - Testing|WS TOC - Testing]] - [[themes/000 Index|Index]]