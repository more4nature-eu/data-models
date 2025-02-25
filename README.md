# More4nature data Schema

The provided schema implements a comprehensive metadata structure for citizen science datasets using JSON Schema for validation and JSON-LD for semantic linking. It combines established standards including DCAT (Data Catalog Vocabulary), Dublin Core Terms, and domain-specific vocabularies like Darwin Core and SensorThings API. The schema enables detailed dataset description, covering aspects from basic metadata to spatial coverage, organizational attribution, and data access methods.

The schema's architecture separates structural validation (JSON Schema) from semantic context (JSON-LD), allowing robust data validation while maintaining semantic interoperability. Key features include support for multiple data standards, explicit data access specifications through DCAT distributions, spatial coverage definition using Simple Features, and organizational attribution via the Organization Ontology. This dual approach ensures both machine readability and semantic richness, facilitating dataset discovery, access, and integration across different citizen science initiatives.

``` mermaid
graph TD
    A[Citizen Science Data] --> B{What type of data?}
    B -->|Environmental Monitoring| C{Real-time data?}
    B -->|Biodiversity| D{Species data?}
    B -->|Earth Observation| E{Satellite/Remote?}
    B -->|Other use| N{Structured Data?}
    
    C -->|Yes| F[SensorThings API]
    C -->|No| G[CSVW]
    
    D -->|Yes| H[Darwin Core]
    D -->|No, sensor based| I[SensorThings API]
    D -->|No, manual records| J[CSVW]
    
    E -->|Yes| K[STAC]
    E -->|No, ground sensors| L[SensorThings API]
    E -->|No, field surveys| M[CSVW]

    N -->|Yes| O[CSVW]
    N -->|Evaluate| P[Review Requirements]
    

    classDef default fill:#f9f9f9,stroke:#333,stroke-width:2px;
    classDef question fill:#ffeb3b,stroke:#f57f17,stroke-width:2px;
    classDef sensorAPI fill:#81c784,stroke:#2e7d32,stroke-width:2px;
    classDef csvw fill:#64b5f6,stroke:#1565c0,stroke-width:2px;
    classDef darwin fill:#ba68c8,stroke:#7b1fa2,stroke-width:2px;
    classDef stac fill:#ff8a65,stroke:#d84315,stroke-width:2px;
    classDef review fill:#e0e0e0,stroke:#424242,stroke-width:2px;
    
    class A default;
    class B,C,D,E,N question;
    class F,I,L sensorAPI;
    class G,J,M,O,Q csvw;
    class H darwin;
    class K stac;
    class P review;
```
