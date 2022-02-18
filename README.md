# aula2-analise de dados verão

library(dplyr)
library(Quandl)
library(ggplot2)
##################
data= starwars %>% 
  select(species, skin_color,gender)%>%
  filter (species == "Human")
cdp_SW <- ggplot(data, aes( x= skin_color,fill = gender )) + 
  geom_bar() +
  labs(title = "Skin color of Star Wars characters", y = 'count', x='skin color')

ggsave("Cor de pele em Star Wars.png")
#############


selic.mensal <- Quandl('BCB/4189', type='raw', start_date = '1999-07-01')%>%
  arrange(Date)

ggplot(selic.mensal, 
       aes(x=Date, y =Value)) +  
  geom_line(color= 'red') +   
  labs(title = "Taxa de juros selic", y = 'taxa selic em porcentagem', x='tempo')
ggsave("Taxa selic.png")
###########
