# Phyloseq_Basic
Basic code for implmenting phyloseq package using R to analyze micro biome data
> library("phyloseq")
> library("biom")
# Loading required libraries (packages)
> mydata<-import_biom("C:/Users/SaiDheeraj/Desktop/Phyloseq/Biome file/QIIME.organism2.data.biom")
#Naming the dataset as mydata
> new=read_biom("C:/Users/SaiDheeraj/Desktop/Phyloseq/Biome file/QIIME.organism2.data.biom")
# reading the data and stroing it under name “new”
> otumat = as(biom_data(new), "matrix")
> OTU = otu_table(otumat, taxa_are_rows=TRUE)
# Defining the out_table data class
> taxmat = as.matrix(observation_metadata(new), rownames.force=TRUE, byrows=FALSE)
> TAX = tax_table(taxmat)
# Defining the tax_table data class
> physeq = phyloseq(OTU, TAX)
# Defining the phyloseq class
> Physeq
# Displays the data of the new phyloseq class
> most_abundant_taxa <- sort(taxa_sums(physeq), TRUE)[1:10]
> ex2 <- prune_taxa(names(most_abundant_taxa), physeq)
> ex2
> topFamilies <- tax_table(ex2)[, "taxonomy3"]
as(topFamilies, "vector")
# Displays the top 10 abundant taxa, with their families

