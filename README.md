# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output

Data cleaning process:
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df

![359429919-4527d27f-ce48-44cb-b8ce-34bbd266e130](https://github.com/user-attachments/assets/d90fc5c3-83c3-4786-b5b8-905042c99e17)


df.head()

![359430246-75445d50-f356-4172-a260-7744a4b8a5d0](https://github.com/user-attachments/assets/eda866be-69f9-415c-9823-1c07b0c81fe7)


df.tail(5)

![359430844-0aad2483-f1d4-4161-8819-6dd578b6c0b7](https://github.com/user-attachments/assets/5c999868-4deb-4616-a89b-a797a043fc5f)

df.isnull()

![359431245-e3ad59dc-d554-42fa-ab22-1a0b8dccd19a](https://github.com/user-attachments/assets/d6a1178c-459d-4973-be0a-51099fd7e48a)


df.notnull()

![359431612-cab8a38c-0423-4657-8487-85a5b7cc4d9d](https://github.com/user-attachments/assets/9c6db864-3688-4e6f-9832-fc9279d92d27)


df.dropna(axis=0)


![359432233-6848d1b2-2b91-4d7b-aae2-89f3d5ebbd83](https://github.com/user-attachments/assets/366ec892-01bc-4524-b839-ffa54b660798)

df.dropna(axis=1)

![359432527-551c2074-915a-4d95-8596-fbc85c7d3a34](https://github.com/user-attachments/assets/d5a0ecfb-2bf3-4a56-b8ee-d3fad81c24fc)


df.fillna(0)

![359432819-d79561f9-7a81-4137-bd4e-1f44c82ca40c](https://github.com/user-attachments/assets/3300507b-1ea0-4d7e-ab69-9c38670af4bc)


print(df.shape)

![359433687-b1907a5f-ab9b-4ce5-a72c-7767076de54b](https://github.com/user-attachments/assets/df3b3ea8-6f46-4212-8b26-b8d55df54eb0)


IQR:

import pandas as pd
import seaborn as sns
ir=pd.read_csv('/content/iris.csv')
ir


![359434303-5f92ae1d-167b-4412-8e99-312c878199d7](https://github.com/user-attachments/assets/d1ad53e0-e854-492d-97ae-b9d6382dfe84)

ir.describe()

![359434586-cc69d12e-9f65-4b57-a506-b8f9194f2749](https://github.com/user-attachments/assets/3c43d6e1-d313-45fc-a812-135bda1e6224)


sns.boxplot(x='sepal_width',data=ir)

![359434907-7c8b93dc-1649-4b07-bf99-39ce4448edeb](https://github.com/user-attachments/assets/1ef4725d-67ee-49eb-b1dc-6f19c189f394)


c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)

![359435194-c3276452-72db-4363-a9e0-3b0a7e0a8563](https://github.com/user-attachments/assets/cd656d47-e4bd-4e4d-be1a-8be0493c95e3)

rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']

![359435513-4d29e256-9386-4ea4-82a6-02e0f5175f3c](https://github.com/user-attachments/assets/9c1e878e-56a4-474e-89cf-712833165c0f)


delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid

![359435755-b5da97d6-af4b-4690-b448-c1ff0697ea18](https://github.com/user-attachments/assets/fa43e92a-3e46-4633-b707-77bc3bd56791)


sns.boxplot(x='sepal_width',data=delid)


![359436022-1fb5cdcf-87ba-4631-b643-d2aeb0b2f8a2](https://github.com/user-attachments/assets/f2039f6d-453d-4b26-ac3a-1a705f9201c3)


Z SQUARE

import matplotlib.pyplot as plt
import pandas as pd
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset

![359436930-2f2868d2-4002-4f47-82c4-8c0ad8a19392](https://github.com/user-attachments/assets/6fafff02-a866-473d-8888-a01b2e4ddbdd)


df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr

![359437229-2dae9f2a-a47a-4249-90a6-159aea236d8d](https://github.com/user-attachments/assets/dc66dfd3-a78f-4f4b-90ed-d8af6fe75588)


low = q1 - 1.5*iqr
low

![359437858-68c83441-a0b3-4821-96c4-8113ec2d0abb](https://github.com/user-attachments/assets/e2d175ca-c31b-42b6-a97a-ab203f08c548)


high = q3 + 1.5*iqr
high

![359438348-734158d2-fc68-4f4b-b315-b58ff808ae2c](https://github.com/user-attachments/assets/35d811a2-2269-4ac2-8729-6eef5db33be5)

df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1

![359438726-c6f95d8a-8a60-48bf-9fc0-3bb251eeabec](https://github.com/user-attachments/assets/3f2c51f9-0d8c-401d-b6e4-ebd058a6af44)

z = np.abs(stats.zscore(df['height']))
z

![359439236-0f13eb15-f41a-4de2-b43a-47c5062c495b](https://github.com/user-attachments/assets/5eff85d6-89bc-40ec-b09e-f395a7d71968)


 df1 = df[z<3]
 df1

 ![359439595-2c5a2fc4-cbec-4311-bf01-d85c236ecef3](https://github.com/user-attachments/assets/dc155f2f-ca30-45a5-9716-b0aec21f1fd9)

 


# Result
          Thus the Data Cleaning Process and Detecting and Removal of Outliers is executed successfully.
