if(!require(pacman)) install.packages("pacman")
pacman::p_load(
  tidyverse,
  inspectdf,
  plotly,
  janitor,
  visdat,
  esquisse,
  table1,
  DataExplorer,
  here)
#load data
#ebola_data <- read_csv("data/ebola_sierra_leone.csv")
ebola_data <- read_csv(here("data/ebola_sierra_leone.csv"))

#View(ebola_sierra_leone)

#cases by districts 
district_tab <- tabyl(ebola_data,district)
#district_tab
#arrange(district_tab,n) # ascending order
district_tab_arranged <- arrange(district_tab,-n) #decsending order

write_csv(x=district_tab_arranged,file = "outputs/district_tabulation_desc.csv")

#Visualizing catagorical variables

p <- ebola_data %>%
  select(where(is.factor)) %>%
  pivot_longer(cols = everything()) %>%
  ggplot(aes(x = value)) +
  geom_bar() +
  facet_wrap(~ name, scales = "free") +
  theme_minimal()

ggsave(filename = "outputs/categorical_plot.png", plot = p, width = 10, height = 6, dpi = 300)
ggsave(filename = "outputs/categorical_plot.pdf", plot = p, width = 10, height = 10, dpi = 300)


#Visualizing numeric variables 
num_var_plot <- show_plot(inspect_num(ebola_data))
num_var_plot

ggsave(filename = "outputs/numerical_plot.png", plot = num_var_plot, width = 10, height = 10, dpi = 300)
ggsave(filename = "outputs/numerical_plot.pdf", plot = num_var_plot, width = 10, height = 10, dpi = 300)










