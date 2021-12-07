# scMuscle_atlas_symphony

In summary, I used Symphony to map Tabula muris data ("Muscle" and "Bladder") on to scMuscle_Mckellar_Cosgrove atlas (integrated with Harmony).

### To jump to the results directly: run notebook @ scripts/TM_MapQuery_Plots.ipynb

### Summary:
#### Tabula Muris - Limb Mucsle:


#### Tabula Muris - Bladder:


## Step 1: Made symphony-compatible reference

### Script
scripts/MakeSymphonyReference.R

### Input
scMuscle_diet_v1-1.h5Seurat (Data from David Mckellar)

### Procedure
Followed https://github.com/immunogenomics/symphony/blob/main/vignettes

1. Extracted the (a)Normalized genes x cells matrix; (b) Variable genelist from scMuscle_diet_v1-1; (c) Metadata (including original cluster labels);  
2.  Recalculated pca-embeddings and loadings;
3. Reran harmony with harmony::HarmonyMatrix;
4. Made reference with symphony::buildReferenceFromHarmonyObj.

### Output
Symphony-compatible reference (output: scMus_SymphonyRef.rds)



## Step 2:  Map Tabula Muris data

### Input
a) TM droplet data - "Muscle" and "Bladder"
https://figshare.com/ndownloader/files/10038325
source:
https://scrnaseq-course.cog.sanger.ac.uk/website/tabula-muris.html

b) scMus_SymphonyRef.rds

### Script
scripts/TabulaMuris_Cosgrove.Rmd

### Procedure
1. Process data using this notebook as a reference: https://github.com/czbiohub/tabula-muris/blob/master/00_data_ingest/Droplet_Notebook.Rmd
2. Map to Symphony Ref

### Output
Predicted cell types


## Step 3: Visualize results

Run scripts/TM_MapQuery_Plots.ipynb
