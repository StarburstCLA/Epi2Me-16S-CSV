library(dplyr)

data <- read.csv("yourpath")

#separate for analysis

NoSpec <- data %>%   filter(species %in% "")

Spec <- data %>%   filter(species != "")

NoSpecNoNA <- NoSpec %>% filter(species_name != "")

Unidents <- NoSpec %>% filter(species_name == "")

NoSpecNoNA <- NoSpecNoNA %>% separate(species_name, c("genus","species"), sep = " ", remove = FALSE)

#Re-merge

NoSpecNoNA <- unite(NoSpecNoNA, species, c(genus, species), sep = " ", remove = FALSE)

#Move columns to end correctly

NoSpecNoNA <- NoSpecNoNA %>% relocate(genus, .after = family)

NoSpecNoNA <- NoSpecNoNA %>% relocate(species , .after = genus)

#merge

FixedData = bind_rows(Spec, NoSpecNoNA, Unidents)

#Check no new rows have been created in error

print(paste("Number of new rows ", nrow(FixedData),"Number of old rows" , nrow(data), "Same =", nrow(FixedData)==nrow(data) ))

#Save to file

write.csv(FixedData, "yourpath", row.names=TRUE)
