# Machine Learning - 
Using the package SKlearn

# About the project

The project uses machine learning with the package SKlearn. I tried to predict the house prices.

![Scikitlearn](https://github.com/arielcs309/assets/blob/main/Indicators.png)


## Histogram
![prices](https://github.com/arielcs309/assets/blob/main/Brazil%20map.png)

## Correlation
Price and square feet shows the highest correlation. The others don't have a good correlation since they're close to zero.
![correlation](https://github.com/arielcs309/assets/blob/main/Table%20Clusters.png)

## Dummies
So I had to create dummies with the code below:
```bash
db1 = pd.get_dummies(db, columns = ['Neighborhood'],
                    prefix = 'C')
```
Since there was 3 kinds of neighborhood. 

![dummy](https://github.com/arielcs309/assets/blob/main/dendrogram.png)

## Analysis of Variance (ANOVA)

All variables had a p-value less than 0.05, leading to the rejection of the null hypothesis. This indicates that they demonstrated significance in differentiating the clusters.
Null Hypothesis (H0): The means of the groups are equal.
Alternative Hypothesis (H1): At least one group mean is different from the others.
![P Value](https://github.com/arielcs309/assets/blob/main/P%20value.png)
# Language
![python](https://github.com/arielcs309/assets/blob/main/R%20language.jpg)

# How to execute the project
## Summarizing the project
```bash
# install packages
packages <- c("plotly", #graph platform
             "tidyverse", #load other R packages
             "ggrepel", 
             "knitr", "kableExtra", #format tables
             "reshape2", #'melt' function
             "misc3d", #3D graphs
             "plot3D", #3D graphs
             "cluster", #'agnes' function to elaborate hierarchy cluster
             "factoextra", #função 'fviz_dend' to build dendrograms
             "ade4")

# Use Scale function to make the indicators standart. Average becomes 0 and standart deviation becomes 1.
IBGE_padronizado <- as.data.frame(scale(base[,2:10]))
view(IBGE_padronizado)

# create dissimilarity matrix with the euclidian distance
matriz_D <- IBGE_padronizado %>% 
  dist(method = "euclidean")

# Choosing the linkage with agnes function that allows you to use single, average and complete linkage
cluster_hier_average <- agnes(x = matriz_D, method = "average")

#building the dendrogram
dev.off()
fviz_dend(x = cluster_hier_average, show_labels = F)

#checking if variables help to create groups with ANOVA.
summary(anova_IDH <- aov(formula = IDH_2020 ~ cluster_H,
                            data = IBGE_padronizado))

#analyse the final clusters created with group by according
analise <- group_by(base, cluster_H)%>%
  summarise(IDH_2020 = mean(IDH_2020, na.rm = TRUE),
            Votos_lula = mean(Votos_lula, na.rm = TRUE),
            Votos_bolsonaro = mean(Votos_bolsonaro, na.rm = TRUE),
            PIB = mean(PIB_2021, na.rm = TRUE),
            IDEB = mean(IDEB_2021, na.rm = TRUE),
            Homicidios = mean(Taxa_homicidios, na.rm = TRUE),
            Gini = mean(Indice_gini, na.rm = TRUE),
            Desocupacao = mean(Indice_desocupacao, na.rm = TRUE),
            Rendimento = mean(Rendimento_mensal_domiciliar_per_capita, na.rm = TRUE))

# Also added a Pearson correlation to check how the variables behave with each other
chart.Correlation((base[2:10]), histogram = TRUE)

```

# Author
Ariel Sousa. 
See my [Linkedin](https://www.linkedin.com/in/ariel-candido-22684578/) and my [Kaggle](https://www.kaggle.com/arielsousa)


