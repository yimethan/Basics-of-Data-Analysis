# 1

## DataFrame

### make dataframe

```python
df = pd.DataFrame({"Name": ["Braund, Mr. Owen Harris", 
                            "Allen, Mr. William Henry", 
                            "Bonnell, Miss. Elizabeth",],
                   "Age": [22, 
                           35, 
                           58],
                   "Sex": ["male", 
                           "male", 
                           "female"],})
```

```python
df['Age']
df.Age
```

+ check data

```python
df.info()
df.describe()
df.dtypes
```

### read tabular data

+ 'State' as index

```python
alco2009 = pd.read_csv(path+filename, index_col="State")
```

### excel

+ df to excel

```python
titanic.to_excel("titanic.xlsx", sheet_name="passengers", index=False)
```

+ excel to df

```python
titanic2 = pd.read_excel("titanic.xlsx", sheet_name="passengers")
```

### add & set values of new column

+ broadcasting

```python
alco2009["Total"] = 0
```

## select rows & columns

### select columns

+ as DataFrame not Series

```python
age_sex = titanic[["Age", "Sex"]]
```

### boolean indexing

```python
above_35 = titanic[titanic["Age"] > 35]
```

### loc

+ df = df.loc[조건, 열]

```python
adult_names = titanic.loc[titanic["Age"] > 35, "Name"]
```

### 조건 slicing in specific column

+ df = df.열[조건]

```python
adult_names = titanic.Name[titanic.Age > 35]
```

+ multiple conditions
  + (C1) & (C2)

```python
survived_female = titanic[(titanic.Survived == 1) & (titanic.Sex == 'female')]
```

### iloc

+ slice by index number
  + .iloc[행, 열]

```python
sliced_1 = titanic.iloc[3:10, 0:2]
```

```python
sliced_2 = titanic.iloc[[0, 2, 4, 6, 8], [0, 2, 4]]
```

## plot

### simple plot

```python
air_quality.plot()
```

## combine tables

### .concatenate

![](https://pandas.pydata.org/docs/_images/08_concat_row.svg)

+ 행이 많아짐
+ 세로로 이어붙이기 (밑에)

```python
air_quality = pd.concat([air_quality_pm25, air_quality_no2], axis=0)
```

### .join

![](https://pandas.pydata.org/docs/_images/08_merge_left.svg)

+ 열이 많아짐
+ 가로로 이어붙이기 (옆에)

```python
air_quality = pd.merge(air_quality_pm25, air_quality_no2, on="date.utc")
```

## sort

```python
air_quality = air_quality.sort_values("date.utc")
```