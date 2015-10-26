# Phyloseq_Basic
Basic code for implmenting phyloseq package using R to analyze micro biome data
# Loading required libraries (packages)
> library("phyloseq")

> library("biom")

#Naming the dataset as mydata

> mydata<-import_biom("C:/Users/SaiDheeraj/Desktop/Phyloseq/Biome file/QIIME.organism2.data.biom")

# reading the data and stroing it under name “new”

> new=read_biom("C:/Users/SaiDheeraj/Desktop/Phyloseq/Biome file/QIIME.organism2.data.biom")

# Defining the out_table data class

> otumat = as(biom_data(new), "matrix")

> OTU = otu_table(otumat, taxa_are_rows=TRUE)

# Defining the tax_table data class

> taxmat = as.matrix(observation_metadata(new), rownames.force=TRUE, byrows=FALSE)

> TAX = tax_table(taxmat)

# Defining the phyloseq class

> physeq = phyloseq(OTU, TAX)

# Displays the data of the new phyloseq class

> Physeq

# Displays the top 10 abundant taxa, with their families

> most_abundant_taxa <- sort(taxa_sums(physeq), TRUE)[1:10]

> ex2 <- prune_taxa(names(most_abundant_taxa), physeq)

> ex2

> topFamilies <- tax_table(ex2)[, "taxonomy3"]
as(topFamilies, "vector")



