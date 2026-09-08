# Minecraft Knowledge Graph – Semantic Web Project

[![CI](https://github.com/blw-ofag-ufag/semantic-web-template/actions/workflows/ci.yml/badge.svg)](https://github.com/blw-ofag-ufag/semantic-web-template/actions/workflows/ci.yml)
[![GitHub last commit](https://img.shields.io/github/last-commit/blw-ofag-ufag/semantic-web-template.svg)](https://github.com/blw-ofag-ufag/semantic-web-template/commits)
[![GitHub issues](https://img.shields.io/github/issues/blw-ofag-ufag/semantic-web-template.svg)](https://github.com/blw-ofag-ufag/semantic-web-template/issues)

For demonstrative purposes, this template repository includes a full semantic web pipeline, including
 
1. manual data curation (data files in `src/rdf/data`),
2. data integration from a relational database (using python, specifically `src/python/pipeline/...`),
3. OWL-based inferencing (using the ontology in `src/rdf/model.owl.ttl`),
4. SPARQL-based processing of the graph (using rules in `src/sparql/processing/...`)
5. SHACL-based graph data validation (using `src/rdf/shapes/model.shacl.ttl`)
6. a even more customizable Pytest test suite,
7. local validation and test suites without external deployment
8. interactive educational notebooks (`notebooks/`) explaining Semantic Web theory (RDF, SPARQL, RDFS/OWL reasoning, SHACL) using the Minecraft knowledge graph.

Specifically, this project models a Minecraft knowledge graph (items, blocks, recipes), makes OWL/HermiT inferences, and validates the data against SHACL shapes.

> [!IMPORTANT]
> After using this template repository for a project, you probably want to delete/overwrite any of the aforementioned turtle/sparql/python files.

## Development Tools

This template uses a variety of tools to ensure robust data integration, reasoning, validation, and documentation.

- [HermiT](http://www.hermit-reasoner.com/): An OWL reasoner used for logical reasoning and inferring new knowledge from the ontology and data.
- [Pytest](https://docs.pytest.org/): A testing framework used to run syntax checks and evaluate SHACL validation reports.
- [PySHACL](https://github.com/RDFLib/pySHACL): A Python engine used to validate the generated RDF graphs against SHACL shape definitions.
- [ROBOT](http://robot.obolibrary.org/): CLI tool used to merge, reason, and process RDF graphs.
- [RDFLib](https://rdflib.readthedocs.io/): A Python library used to parse, serialize, and programmatically manipulate RDF data.
- [Quarto](https://quarto.org/): An open-source publishing system used for rendering the documentation.

## Semantic Web Standards

The project relies on core W3C Semantic Web standards to model, link, and validate data effectively.

- [RDF (Resource Description Framework)](https://www.w3.org/RDF/): The foundational data model used to represent information as a directed graph of triples.
- [OWL (Web Ontology Language)](https://www.w3.org/OWL/): Used to define the formal semantics, classes, and properties of the ontology.
- [SHACL (Shapes Constraint Language)](https://www.w3.org/TR/shacl/): Used to declare structural constraints and validate the integrity of the RDF data.
- [SPARQL](https://www.w3.org/TR/sparql11-overview/): The standard query language used to extract, transform, and post-process the RDF graphs.
- [Turtle](https://www.w3.org/TR/turtle/): The primary, human-readable serialization format used for all RDF files in this repository.

## Build and Deployment Orchestration

To streamline the workflow, this project uses `make` as its primary orchestration tool, automating everything from setup to deployment. The `Makefile` defines a single entry point to sequentially execute data integration, logical reasoning, SPARQL updates, SHACL validation, testing, and documentation rendering.

1. Add variables to `.env` (for local execution)

    ``` sh
    USER=********
    PASSWORD=********
    GRAPH=********
    ENDPOINT=********
    ```

2. Set up dependencies

    ``` sh
    make setup
    ```

3. Run the build process

    ``` sh
    make
    ```

    Make sure you pass all tests with `pytest`.

4. Deployment note:

    This didactic Minecraft project is intended for local testing and CI validation. Publishing to LINDAS is disabled.

5. *If* you want to clean all written files:

    ``` sh
    make clean
    ```

## Contact

Do you have questions? Please do not hesitate to contact us at [agridata.ch@blw.admin.ch](mailto:agridata.ch@blw.admin.ch), open an [issue in this repository](../../issues), or directly submit a [Request for Change (RFC) via the official eCH feedback form](https://ech.ch/de/ech-standards/standardisierungsprozess/request-change-rfc).
