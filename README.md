# Ikea-furniture
ikea <- readr::read_csv('https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2020/2020-11-03/ikea.csv')

ikea %>%

    group_by(category) %>%
    
    summarise(mean=round(mean(price),digits=2))%>%
    
    ungroup() %>%
    
    ggplot(aes(x=reorder(category,mean),y=mean))+
    
    geom_col(fill='grey')+
    
    coord_flip()+
    
    labs(y="Mean price",x="Furniture category",title="Mean Price of each category",subtitle="Ikea furniture",caption="Source: Kaggle")+
    
    theme(panel.background = element_blank(),panel.grid=element_blank(),axis.ticks = element_blank(),
    
          text=element_text(color='grey',size=16),axis.text=element_text(color='grey',size=12),
          
          plot.background = element_rect(fill ='black'))
