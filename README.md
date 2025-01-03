# RHEL AI/InstructLab POC for DISA/JHU APL
This repository contains a Proof-of-Concept (POC) focused on alignment tuning a IBM Grantite Large Language Model (LLM) using InstructLab. The model incorporates  public data published by the Johns Hopkins University's Applied Physics Laboaratory (JHU APL), a not-for-profit university-affiliated research center in Laurel, Maryland. APL addresses complex research, engineering, and analytical challenges for national security and space exploration. APL publishes its research in many formats, which include periodicals that can be downloaded as .pdf documents.

## Project Goals
The objective of this POC is to fine-tune an LLM to comprehend and generate content relevant to the research areas covered in the APL Technical Digest. By leveraging InstructLab and Granite, we aim to create a specialized model that can assist researchers in the Department of Defense community with greater performance than a general-purpose LLM. 

## Training Data and Knowledge
The APL Technical Digest is an unclassified technical journal published by the Applied Physics Laboratory (APL). Its purpose is to communicate recent advances by the Laboratory in science, technology, engineering, and mathematics, along with expository articles by APL staff members that accelerate education and understanding of new capabilities, results, and discoveries. The Digest serves as a platform to share APL's work with its sponsors, as well as the broader scientific and engineering communities, defense establishments, academia, and industry.

For this POC, we chose the two volumes of the technical digest that were published in 2024:
* Vol. 37, No. 2 (2024) - "APL Research and Development" https://www.jhuapl.edu/sites/default/files/2024-09/37-02-FullBook.pdf
* Vol. 37, No. 3 (2024) - "Concept Design and Realization Branch—Part II" https://www.jhuapl.edu/sites/default/files/2024-09/37-03-FullBook.pdf

## Repository/Taxonomy Structure
The repository is organized as follows:
```

├── data_prepartion
│   ├── documents_collection
│   │   └── 37-02-FullBook.pdf
│   │   └── 37-03-FullBook.pdf
│   ├── documents_converted
│   │   └── 37-02-FullBook.md
│   │   └── 37-02-FullBook.md
│   ├── taxonomy
│   │   └── knowledge
│   │       ├── jhu_apl
│   │           ├── technical_digest
│   │               ├── volume_37-02
│   │                   ├── technical_digest_abstracts
│   │                       ├── qna.yaml
│   │               └── volume_37-02
│   │                   ├── technical_digest_abstracts
│   │                       ├── qna.yaml
```
