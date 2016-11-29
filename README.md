# Hospital-Information
```{r}
library(dplyr)
hospital.data <- read.csv("data/hospital_data.csv", stringsAsFactors = F)
hospital.data.shortened <- hospital.data %>%
  select(Provider.City, Provider.State, Average.Covered.Charges) %>% 
  group_by(Provider.State) %>% 
  summarize(State.Covered.Charges = mean(as.numeric(gsub("\\$", "", Average.Covered.Charges))))
source("scripts/choropleth.r")
makeChoropleth(hospital.data.shortened)
```