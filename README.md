# DM2024-Lab1-Master

ISA5810 Lab 1 Notebook
#Exercise 2
#Counts for each category:
X['category_name'].value_counts()

#Filter by values or condition
X[X['category_name'].isin(['comp.graphics','sci.med'])]

#Querying rows where a text column contains certain keywords
X[X['text'].str.contains("Michael", case=False)]

#Dissection by category
alt_atheism = X[X['category_name'] == 'alt.atheism']
comp_graphics = X[X['category_name'] == 'comp.graphics']
sci_med = X[X['category_name'] == 'sci.med']
soc_religion_christian = X[X['category_name'] == 'soc.religion.christian']
#Dictionary to store each category DataFrame
category_dfs = {category: X[X['category_name'] == category] for category in X['category_name'].unique()}
#Example
print(category_dfs['comp.graphics'].head())
