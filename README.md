# NBA Fantasy League Analaysis


```
import pandas as pd

salary_file = 'NBA Player Salaries_2000-2025.csv'
stats_file = 'NBA Player Stats_1998-2025.csv'

salary_df = pd.read_csv(salary_file)
stats_df = pd.read_csv(stats_file)

merged_df = pd.merge(salary_df, stats_df, on=['Player', 'Year'], how='left')

merged_df.dropna().to_csv('my_data.csv',index=False)
```

