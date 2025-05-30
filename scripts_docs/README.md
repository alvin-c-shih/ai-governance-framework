# Scripts

This directory contains scripts for downloading external references, processing governance framework files, and maintaining project consistency.

## dl_ffiec-itbooklets.py
   - Downloads and converts FFIEC IT Handbook booklets to Markdown format.
   - Generates YAML mappings, downloads HTML files (with navigation filtering), and converts to Markdown using pandoc.
   - Requires: `pip install requests beautifulsoup4 pyyaml` and `pandoc`
   - Usage: `python dl_ffiec-itbooklets.py --all` (or `--yml`, `--html`, `--md` individually)

## dl_eu-ai-act.py
   - Downloads EU AI Act Explorer content and extracts table of contents and annexes into structured Markdown and YAML files.
   - Generates `eu-ai-act-toc.md` (human-readable) and `eu-ai-act.yml` (machine-readable) with hierarchical document structure.
   - Requires: `pip install requests beautifulsoup4 pyyaml roman`
   - Usage: `python dl_eu-ai-act.py` (add `--download` to force fresh download)

## dl_owasp_llm.py
   - Downloads OWASP LLM Top 10 markdown files and generates YAML mappings.
   - Creates structured references to all LLM security risks with proper URLs.
   - Requires: `pip install requests pyyaml`
   - Usage: `python dl_owasp_llm.py`

## dl_nist-pdfs.py
   - Extracts precise bookmarks from NIST documents (SP 800-53r5, AI 600-1) with object-based deep links.
   - Supports multiple output formats: fancy/plain Markdown or YAML for Jekyll integration.
   - Can extract leaf nodes only (`--leafs`) for individual controls/risks, or full hierarchical structure.
   - Generates YAML files in `docs/_data/` with normalized keys (e.g., `ac-1`, `2-1`) for easy reference.
   - Requires: `pip install requests pypdf pyyaml`
   - Usage: `python dl_nist-pdfs.py --document ai-600-1 --leafs --format yaml`

## annotate_yaml_front_matter.py
   - Adds title comments to YAML front matter in risk and mitigation files for better readability.
   - Processes external risks, risks, and mitigations to create cross-referenced annotations.
   - Requires: `pip install PyYAML`
   - Usage: `python annotate_yaml_front_matter.py`

## rename-with-titles
   - Renames risk and mitigation files to include their titles in the filename.
   - Supports dry-run mode for preview and separate processing of risks vs mitigations.
   - Usage: `./rename-with-titles --ri --dryrun` or `./rename-with-titles --mi`

## lint-check
   - Validates filename conventions and project structure consistency.
   - Checks that files follow expected naming patterns.
   - Usage: `./lint-check`
