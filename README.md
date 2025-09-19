# DF Lab Blueprint

DF Lab Blueprint is a specification project for **accurate Dwarf Fortress–style unit generation**.  
It defines how creatures (dwarves, humans, elves, etc.) are described, how their attributes are rolled,  
and how those attributes are evaluated using DF’s percentile cutoff model.

## Purpose
- Model physical and mental attributes with **7 cutoff ranges** per DF raws.
- Generate units with reproducible rolls and body modifiers.
- Initialize **all skills at 0**, using DF’s 11-tier skill scale.
- Evaluate attributes with an **8-class model** (very_low → exceptional).
- Provide schema files only — no pipelines or gameplay mechanics mixed in.

## Repository Layout

Configs/ Creatures/        # Creature definitions (DWARF.txt, HUMAN.txt, ELF.txt, …) CreatureIndex.txt # Maps creature keys to their definition files Core/ ConfigManager.txt # Global defaults and fallback rules UnitGenerator.txt # Attribute rolling logic Evaluator_8class.txt # Attribute classification Skills.txt        # Skill codes and 11-tier scale Unit_RAW_Template.txt # Template for generated units Validator.txt     # Schema checks (cutoffs ascending, keys present, bounds) Loader.txt        # Load order, fallback chain, caching Tests/ test_species_loading.task test_normal_fallback.task test_evaluator_8class.task test_distribution_human.task test_distribution_dwarf.task test_distribution_elf.task FactoryIndex.txt    # Boot plan (Core + Configs only) README.md .gitignore

## Attribute Evaluation (8-class model)
Each attribute value is compared against its species’ cutoffs and placed in a class:

- **very_low**: below c1  
- **low**: between c1–c2  
- **below_avg**: c2–c3  
- **avg**: c3–c4  
- **above_avg**: c4–c5  
- **high**: c5–c6  
- **elite**: c6–c7  
- **exceptional**: ≥ c7  

## Skills
All skills are initialized at 0.  
Scale: 0 (No skill) → 11 (Great).

## Notes
- This repo is schema-only.  
- No embark, military, or noble pipelines are included here.  
- Future work: add more creatures, extend personality/values modeling, refine validation.