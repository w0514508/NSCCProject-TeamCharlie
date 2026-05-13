# Week 4 — Internal Reviews

## Danielle — Review of Temperature & AQI Model from Yashaswi

### Internal Review — Climate / Temperature & AQI Model

Reviewed the data model focusing on structure, grain consistency, and integration across climate domains.

**Strengths:**
- Clear attempt to organize the model using fact and dimension tables
- Separation of domains such as temperature, wind, precipitation, and AQI
- Inclusion of AQI as a separate fact table supports multi-domain analysis
- Use of a central station dimension provides consistent geographic context

**Suggestions:**
- Review table roles to ensure a clear distinction between fact and dimension tables
- Simplify relationships where possible to avoid overly complex cross-filter behaviour
- Consider consolidating date handling into a single calendar dimension
- Validate that all measures are evaluated at the intended grain

**Summary:**
The model provides a solid foundation and supports multi-domain analysis, with opportunities to improve clarity and consistency.
