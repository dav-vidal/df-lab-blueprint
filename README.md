# DF Lab Blueprint

Schema and design repo for DF-style unit generation and stat calculation.
- Species profiles with 7-cutoff percentile arrays
- UnitGenerator spec (percentile bucket rolls)
- ConfigManager (thresholds, synergies, fallback)
- Pipelines (start with EMB; more later)
- Tests as task files

## Layout
Core/ … specs for ConfigManager, UnitGenerator  
Configs/Species … Human, Dwarf, Elf profiles + SpeciesIndex  
Pipelines/EMB … Embark pipeline spec  
Outputs/ … generated artifacts (gitignored)  
Tests/ … task-based sanity checks  
Docs/ … notes

## Next
- Add more species
- Add more pipelines (MIL, NOB, IND)
- Optionally implement a CLI in a separate repo
