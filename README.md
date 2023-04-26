# Epi2Me-16S-CSV
Hosting of Deprecated Code from Nanopore Epi2Me Labs for Analysis of CSV Files, and a script for repairing broken Species/Genus Data. 

This is intended to be used on the .CSV files downloaded from the web portal of Epi2Me Agent after running "Fastq 16S". Last tested on Fastq 16S 2022.01.07

To run the tutorial import the .ipynb Jupyter Notebook file into Epi2Me Labs implementation of Jupyter Notebooks. This can be achieved by placing the file in epi2me-resources/tutorials/  with the other tutorial notebooks or just drag and drop or copy and pasting into a new notebook page. Then you can run the code directly in Epi2Me Labs as described here https://labs.epi2me.io/labsquickstart#running-a-tutorial. A .pdf is included for easy reading without import and to compare to ensure it is displaying properly. Note, some lines appear to fall out the bottom of the input boxes, e.g. 
/epi2melabs/16s_lineage
and
VBox(children=(HBox(children=(Label(value='Use sample data', layout=Layout(width='150px')), interactive(childr…

This is origional to this script by Epi2ME beofre I rescued it, however these can or possibly should be moved back into the correct location when you use it. A corrected version by me may folow. 

The notebook adds better lineage information than is downloaded in the .CSV file (but appears present on the online portal).


R_CSV_Fixing_Script 
In some cases the Fastq 16S results in strange behaviour thought to be due to Kraken2 where data is present in species_name but not in species or genus. This R script  coppies data missing to the Genus and Species columns. It breaks the data into multiple parts using dplyr then reasembles them with a check to make sure no new rows have been created. This method is used as it is considerably faster than looping through all data. 

Note this does not bring across family data if that is not present in the family column.

The Data for this script should be the output of the .ipynb tutorial. 

The results can be fed back into the .ipynb tutorial by putting 
annotated output =  "yourpathtoscriptoutput" 
before the last tutorial box to return your fixed data from the script and use the tutorials summary function.

All content worked at last usage 2022 November. 
