# Data Mesh Glossary

## Polysemes
**Polysemes** represent core business concepts that exist across multiple domains, but with distinct attributes, behaviors, and interpretations depending on the domain's context. For example, the concept of a "customer" is a polyseme because:

- In the **sales domain**, a customer might include attributes like *purchase history* and *preferred products*.
- In the **support domain**, a customer might focus on *open tickets* and *support history*.
  
These variations are influenced by each domain's **bounded context**, a key principle in DDD (Domain Driven Design) that delineates how a concept is modeled and used within a specific domain.

### **Polysemes and Data Mesh**

A **data mesh** enables domains to own their analytical data as products while maintaining autonomy. When combined with polysemes, this approach provides a mechanism to model shared business concepts with domain-specific adaptations. Here's how:

1. **Bounded Contexts in Domains**:
   - Each domain models a polyseme independently, capturing attributes and behaviors relevant to its needs.
   - For example, the **sales domain** might model a "customer" polyseme with attributes like *lifetime value* and *conversion rate*, while the **support domain** focuses on *ticket response time* and *satisfaction score*.

2. **Cross-Domain Mapping**:
   - Despite their contextual differences, polysemes are linked through a **global identifier** (e.g., a customer ID). This enables a unified view across domains for cross-domain analysis.
   - Example: Analysts could join data from sales and support domains to understand how customer support interactions influence purchasing behavior.

3. **Preserving Autonomy with Interoperability**:
   - Domains remain autonomous, modeling their polysemes according to their bounded context.
   - However, **data product contracts** define how the shared attributes (e.g., global identifiers) are exposed, ensuring interoperability while maintaining domain independence.

### **Benefits of Polysemes in a Data Mesh**
- **Contextual Adaptation**: Domains can model polysemes with attributes and behaviors specific to their needs without disrupting other domains.
- **Shared Understanding**: Polysemes ensure that all domains share a common core concept, promoting consistency in business terminology.
- **Scalable Analysis**: With global identifiers, businesses can perform cross-domain analysis, providing insights that span multiple facets of the organization.
- **Flexibility and Evolution**: As domains evolve, their representations of polysemes can change independently without breaking global mappings.

By leveraging polysemes in a data mesh architecture, organizations can balance the need for domain autonomy with the ability to unify and analyze shared business concepts across the enterprise. This approach fosters collaboration, reduces data silos, and enables deeper insights while respecting the nuances of each domain.