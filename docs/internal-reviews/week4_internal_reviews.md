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


---

## Danielle — Review of GHG Model from Michael

### Internal Review — GHG Data Model and Measures

Reviewed the GHG model with focus on data structure, table design, and measure definition.

**Strengths:**
- Clear separation of fact and dimension tables, with Fact_GHG as central table
- Use of Dim_Province and Dim_Sector enables flexible analysis
- Inclusion of forecast table supports predictive layer
- Identified measures align with analytical goals

**Suggestions:**
- Review the role of Dim_Date, as it contains measure-like fields that should be defined as DAX measures
- Ensure consistent definition of calculated metrics as measures
- Validate that the model preserves a clear grain (province, sector, year)
- Confirm relationship structure supports correct filter propagation

**Summary:**
The model provides a solid structural foundation. Refining table roles and measure definitions will improve clarity and consistency.

