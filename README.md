### EX-04: Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 19-09-2025
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program-1:
```python
import pandas as pd
import matplotlib.pyplot as plt
df=pd.read_csv('clustervisitor (Salary).csv')
cluster={"Young":(df['Age']<=30),"Middle":((df['Age']>30) & (df['Age']<=50)),"Older":(df['Age']>50)}
print(cluster)
count=[]
for g,c in cluster.items():
  visitors=df[c]
  count.append(len(visitors))
  print(f'Visitors in {g} Group')
  print(visitors)
  print('Count of Groups')
  print(count)
plt.figure(figsize=(8, 6))
plt.bar(cluster.keys(), count, color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()
```
### Output:
<img width="434" height="734" alt="image" src="https://github.com/user-attachments/assets/e8b4a5b4-e468-4c71-b6a0-b07980dac9f1" />
<img width="756" height="550" alt="image" src="https://github.com/user-attachments/assets/e494066f-6ce8-43c2-9924-baf404f10207" />


### Program-2:
```python
import pandas as pd
import matplotlib.pyplot as plt
df=pd.read_csv('clustervisitor (Salary).csv')
df1=df['Age']
df2=df['Salary']
df3=pd.concat([df1,df2],axis=1)
df3
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
sc=StandardScaler()
df4=sc.fit_transform(df3)
print(df4)
kmeans=KMeans(n_clusters=3,random_state=32)
df3['cluster']=kmeans.fit_predict(df3)
print(df3)
plt.scatter(df3['Age'],df3['Salary'],c=df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Salary in thousands')
plt.title('Kmeans Cluster')
plt.show()
```

### Output:
<img width="254" height="550" alt="image" src="https://github.com/user-attachments/assets/8f48851a-71d7-498b-b929-3b69a7d1c731" />
<img width="649" height="451" alt="image" src="https://github.com/user-attachments/assets/d01ead70-edc3-41ea-bf19-f87031fa775a" />


### Result:
Thus the Implementation of Cluster and Visitor Segmentation for Navigation patterns executed successfully.
