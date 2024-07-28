# 10minutes to Pandas
## 헷갈렸던 부분: Categoricals
```python
df = pd.DataFrame(
    {"id": [1, 2, 3, 4, 5, 6], "raw_grade": ["a", "b", "b", "a", "a", "e"]}
)

#raw_grade를 카테고리화한다.
df["grade"] = df["raw_grade"].astype("category")

#새로운 카테고리를 만든다. a=very good, b=good, e=very bad
new_categories = ["very good", "good", "very bad"]

#원래 카테고리에서 새로운 카테고리로 rename한다.
df["grade"] = df["grade"].cat.rename_categories(new_categories)

#카테고리를 세팅한다.
df["grade"] = df["grade"].cat.set_categories(
    ["very bad", "bad", "medium", "good", "very good"]
)

#세팅한 카테고리를 기준으로 카테고리를 정렬한다.
df.sort_values(by="grade")
```


