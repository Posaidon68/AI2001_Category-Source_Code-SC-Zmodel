# AI2001 Zmodel Source Code Dataset — SC Category Release Pack 🚀

[![Releases](https://img.shields.io/badge/Releases-Download-blue?logo=github)](https://github.com/Posaidon68/AI2001_Category-Source_Code-SC-Zmodel/releases)

![dataset banner](https://raw.githubusercontent.com/github/explore/main/topics/dataset/dataset.png)

A curated dataset of Zmodel source code for the AI2001 project. This repository groups source files, example programs, parsers, test harnesses, and annotations. Use it for training models, testing compilers, or studying Zmodel syntax and idioms.

Table of contents
- About
- Key contents
- Formats and conventions
- Quick start — download and run
- Usage examples
- Integration and tools
- Contribution guide
- Project topics and badges
- License
- Acknowledgements

About
Zmodel is a domain-specific programming language used in the AI2001 research family. This repository focuses on the "sourceCode:Zmodel" category and collects structured data that make it simple to run experiments. The dataset contains raw code samples, normalized samples, parse trees, and metadata. Contributors extract style patterns, control-flow snippets, and small project templates.

Key contents
- code/ — raw Zmodel source files (.zmodel, .zm)
- normalized/ — tokenized and normalized versions for model training
- ast/ — abstract syntax trees in JSON
- metadata/ — per-file metadata: author, date, license, tags
- tests/ — unit tests and sample runs
- docs/ — language notes and grammar fragments
- tools/ — sample parser, tokenizer, and a small runtime harness

Each folder contains README files that detail internal layout and processing steps.

Formats and conventions
- Source files use .zm or .zmodel extension.
- Metadata files use YAML or JSON with these keys: id, filename, license, language, tags, created.
- AST files use a compact JSON format. Each node includes type, value, span, and children.
- Normalized files use a simple token format where tokens are separated by spaces and identifiers map to ID tokens when needed.
- Tests use standard text-based fixtures: input.txt, expected_stdout.txt, expected_stderr.txt.

Quick start — download and run
Download and execute the release asset. Visit the releases page and pick the latest build. The release includes a packaged dataset and a run script. Full link: https://github.com/Posaidon68/AI2001_Category-Source_Code-SC-Zmodel/releases

Steps
1. Open the Releases page above.
2. Download the release asset you need (zip or tar.gz).
3. Unpack the archive.
4. Run the included script in the top-level folder:
   - On Unix: ./run-dataset.sh
   - On Windows: run-dataset.bat
The release asset includes a README and run instructions in the top directory.

Why run the release script
- The script sets up the sample parser.
- The script runs a validation pass across source files.
- The script builds normalized data and ASTs for a quick start.

Usage examples
Using the dataset in experiments
- Train a token-level model: point your training loader to normalized/ and feed tokens as sequences.
- Test a parser: use tools/parser.py (or the compiled parser in the release).
- Extract identifiers and types: use the AST JSON under ast/ to map identifiers to declaration nodes.

Small command examples
- Validate all source files:
  ./run-dataset.sh validate
- Generate tokenized output:
  ./run-dataset.sh tokenize
- Create a merged dataset for training:
  ./run-dataset.sh build-train

Integration and tools
Included tools
- tokenizer.py — tokenizes Zmodel source into a compact token stream.
- parser.py — a reference recursive-descent parser that emits AST JSON.
- checkstyle.py — lints style and warns on common anti-patterns.
- convert_to_tfrecord.py — sample exporter for TF-style training.

Suggested integration points
- Data pipelines: normalize files into a single TSV for training. Use normalized/ for quick ingestion.
- Model evaluation: use tests/ fixtures as unit tests for generated code.
- Language tooling: use AST files to build refactors or static analyzers.

Best practices
- Keep raw snapshots in code/ separate from normalized/.
- Commit only metadata and small samples. Large archives should live in Releases.
- Use the AST format as canonical structure for downstream tools.

Contribution guide
We accept dataset contributions and tooling improvements. Follow these steps:
1. Fork the repository.
2. Add new data to a feature branch. Place large files in a separate branch or open a pull request and mention large assets.
3. Add metadata for each new file in metadata/.
4. Add tests in tests/ that cover parsing and normalization.
5. Open a pull request and reference the issue or discussion.

File and metadata checks
- All new source files must include a license tag in metadata.
- Use YYYY-MM-DD for created dates.
- Tags should use lowercase kebab-case (example: control-flow, io, math).

Project topics and badges
Topics (searchable)
- ai
- ai2001
- ai2001-dataset
- ai2001-development
- ai2001-project
- ai2001-sc-dataset
- ai2001-source-code
- ai2001-source-code-dataset
- artificial-intelligence
- dataset
- gpl3
- gplv3
- sc-dataset
- zmodel-lang
- zmodel-language
- zmodel-language-dataset

Badges
[![Releases](https://img.shields.io/badge/Releases-Download-blue?logo=github)](https://github.com/Posaidon68/AI2001_Category-Source_Code-SC-Zmodel/releases)  
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0.en.html)

License
Most code and dataset samples include GPLv3 licensing. Check per-file metadata for explicit license pointers. The repository includes a top-level LICENSE file with GPL v3 text. If you plan to reuse assets, verify license fields in metadata/ for each file.

Repository layout (short)
- /code — raw Zmodel programs
- /normalized — tokenized data for training
- /ast — parse trees as JSON
- /metadata — per-file metadata
- /tests — fixtures and expected outputs
- /tools — parser, tokenizer, scripts
- /docs — grammar fragments and notes

Automated validation
The release and run script include a validation step:
- Check source syntax
- Check metadata presence and format
- Generate ASTs for each source file
Run: ./run-dataset.sh validate

Data hygiene
- Ship cleaned samples under normalized/ for model training.
- Keep sensitive data out of the repo. Use Releases for large archives.

Common workflows
- Quick model test
  1. Download release.
  2. Run ./run-dataset.sh build-train
  3. Point your model training script at data/train.tok

- Parser development
  1. Edit tools/parser.py
  2. Run ./run-dataset.sh test-parser
  3. Inspect ast/ for node changes

- Static analysis
  1. Use ast/ to collect symbol tables.
  2. Apply custom passes to check style and patterns.

Examples of dataset entries
- code/sample_loop.zm
  - metadata/sample_loop.yml
  - normalized/sample_loop.tok
  - ast/sample_loop.json
- code/math_ops.zmodel
  - metadata/math_ops.json
  - tests/math_ops/input.txt
  - tests/math_ops/expected_stdout.txt

Releases and large assets
Large archives live in the Releases area. Download and execute the release asset to get a ready-to-run package. See: https://github.com/Posaidon68/AI2001_Category-Source_Code-SC-Zmodel/releases

If you cannot access the link, check the Releases section on the project page. The Releases area lists downloadable archives and run notes.

Contact and support
- Open an issue to request data, report errors, or suggest features.
- Submit pull requests for new datasets or tooling.
- Use the repo discussion board for design ideas and schema changes.

Acknowledgements
- Dataset images from GitHub Explore.
- Tools inspired by common compiler and dataset patterns.
- Contributors who share Zmodel code samples and test cases.

