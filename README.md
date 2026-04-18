# CRAB Outbreak EQA — DTU / EURGen-RefLabCap 2024

Interactive genomic epidemiology analysis of a fictional multi-hospital **Carbapenem-Resistant *Acinetobacter baumannii*** (CRAB) outbreak, reproduced as part of the EURGen-RefLabCap Multidisciplinary WGS Training Workshop (January 2024).

**Live site:** https://cinnetcrash.github.io/EQA_demo/

---

## Contents

| File | Description |
|------|-------------|
| `index.html` | Landing page — overview, stats, links |
| `dashboard.html` | Interactive D3.js dashboard (tree · heatmap · timeline · SNP matrix) |
| `report.html` | Step-by-step outbreak investigation report |
| `app_data.json` | Master data file (36 isolates, ML tree, AMR genes, SNP matrix) |

---

## The Scenario

A fictional National Reference Laboratory in **Country W** receives 71 *A. baumannii* clinical records from six hospitals spanning January–December 2023. The exercise challenges NRL participants to:

1. Construct an epidemic curve and select 36 priority isolates for WGS
2. Perform MLST, AMR profiling, cgMLST, and SNP phylogenetics on Hospital A data (18 isolates)
3. Expand the analysis to Hospitals B–F (18 additional isolates) and determine inter-hospital links

**All data, hospitals, patients, and country names are entirely fictitious — created for training purposes only.**

---

## Bioinformatics Pipeline

```
36 FASTA assemblies
  ├── MLST           mlst v2.33, Pasteur (abaumannii_2) + Oxford schemes
  ├── AMR Profiling  Abricate v1.0.1, CARD database → 49 unique genes
  ├── cgMLST         Pathogenwatch / Kleborate
  └── Core SNP Alignment  Parsnp v2.1.1 → 75,985 variable sites
        └── ML Phylogeny  IQ-TREE2, GTR+G, 1000 ultrafast bootstrap
              └── SNP Distances  mldist × 4 Mb genome
```

---

## Key Findings

- **Main outbreak:** ST2 (GC2) / OXA-23 CRAB detected in all 6 hospitals (31/36 isolates)
- **Two intra-hospital sub-clusters** confirmed in Hospital A by 18/19 European NRLs:
  - *Cluster A* — ST2/CT1451, ≤210 pairwise SNPs
  - *Cluster B* — ST2/CT607·CT2896, more diverse
- **Sporadic non-outbreak cases:** AB_25 (ST1017), AB_36 (NDM-2), AB_44/45 (ST103/NDM-4)
- **Inter-hospital spread** confirmed by phylogenomics; partly linked to Country Z patient movement

---

## Tools & Visualisation

- [Parsnp 2.1.1](https://github.com/marbl/parsnp) — core-genome SNP alignment
- [IQ-TREE2](http://www.iqtree.org/) — maximum likelihood phylogeny
- [Abricate 1.0.1](https://github.com/tseemann/abricate) — AMR gene detection (CARD)
- [mlst 2.33](https://github.com/tseemann/mlst) — MLST typing
- [D3.js v7](https://d3js.org/) — all interactive visualisations

---

*EURGen-RefLabCap EQA · Statens Serum Institut / DTU · January 2024 · Fictitious training scenario*
