# DM2024-Lab1-Master

ISA5810 Lab 1 Notebook

Exercise 2
1. **Counts for each category**:
   ```python
   X['category_name'].value_counts()

2. **Filter by values or condition**:
   ```python
   X[X['category_name'].isin(['comp.graphics','sci.med'])]

3. **Querying rows where a text column contains certain keywords**
   ```python
   X[X['text'].str.contains("Michael", case=False)]

4. **Dissection by category**
   ```python
   #1. Define
   alt_atheism = X[X['category_name'] == 'alt.atheism']
   comp_graphics = X[X['category_name'] == 'comp.graphics']
   sci_med = X[X['category_name'] == 'sci.med']
   soc_religion_christian = X[X['category_name'] == 'soc.religion.christian']

   #2. Store each category DataFrame
   category_dfs = {category: X[X['category_name'] == category] for category in X['category_name'].unique()}

   #3. Example
   print(category_dfs['comp.graphics'].head())

Exercise 5
   ```python
   entry_types = NA_df.map(type)
   print(entry_types)

   # The 3rd row is supposed to be TRUE while the 5th row should be FALSE
   # That is because the empty string ('') interprets the entries as string and NoneType respectively.
   # In Pandas, only entries of type float containing np.nan and NoneType (i.e., None) are interpreted as missing values.
```

Exercise 8
1. **Combine the counts into a dataframe for comparison**:
   ```python
   category_comparison = pd.DataFrame({'X':X.category_name.value_counts(), 'X_sample': X_sample.category_name.value_counts()}).fillna(0)
   category_comparison = category_comparison.sort_values(by='X', ascending=False)

2. **Plotting**:
   ```python
   fig, ax = plt.subplots(figsize=(7, 5))
   bar_width = 0.2

3. **Create bars for X and X_sample**:
   ```python
   plt.bar(x, category_comparison['X'], width=bar_width, label='category_name')
   plt.bar([pos + bar_width for pos in x], category_comparison['X_sample'], width=bar_width, label='category_name')

4. **Labels, title, and legend**:
   ```python
   plt.xlabel('Category')
   plt.title('Category distribution')
   plt.xticks([pos + bar_width / 2 for pos in x], category_comparison.index)
   plt.legend()
   plt.show()
