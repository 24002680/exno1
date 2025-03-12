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
                  Data Cleaning
import pandas as pd


import numpy as np


df = pd.read_csv('SAMPLEIDS.csv')


df.head()

![359341766-f44e8649-ee8a-414d-92b0-dd0d9f65e8be](https://github.com/user-attachments/assets/6cd77702-6e58-4849-8a33-81f0caec3d23)

df.isnull().sum()

![359342975-ceb582b2-1277-4135-8dc7-411445b0aa53](https://github.com/user-attachments/assets/f0054c55-1fcd-46fb-b246-c9611b4f9f51)

df.isnull().any()

![359343363-deae6d6e-8c45-45f5-be72-4c495692fd93](https://github.com/user-attachments/assets/01f72562-51ac-4b4f-b1b6-68311ac56438)

df.dropna(axis=0)

![359343829-157c8b98-36df-4c6a-a504-5cba2b2823db](https://github.com/user-attachments/assets/1237b6b8-922e-4b16-a719-ca736d60ad2e)

df.fillna(0)

![359344379-b5d3d43c-7db3-44a9-b2f0-ce21a5ad5e01](https://github.com/user-attachments/assets/2cc7f2d4-7874-4b68-ac24-3083c4399179)

df.fillna(method='ffill')

![359344796-c9631b32-2ca7-4608-95ce-9fa0529946d7](https://github.com/user-attachments/assets/0d02c7ce-b96e-44dc-a573-4684f9e2b6fb)

df.fillna(method='bfill')

![359344990-3ec2ed10-1f30-481e-8f37-e4884441f7b7](https://github.com/user-attachments/assets/e36de03c-72b8-4684-ba0b-796df8050672)

 df_dropped = df.dropna()

 
 df_dropped

 ![359345414-44cead82-91b0-40a5-b9ac-113ee046fd21](https://github.com/user-attachments/assets/1d194279-e457-4b5d-8fd7-b61b11a06f7a)

df.fillna({'GENDER':'FEMALE','NAME':'PRIYU','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})

![359345548-c7e2a295-4135-4e02-951e-52e34108cb8c](https://github.com/user-attachments/assets/5052b4b7-2b0f-42f3-b6df-ae0e381ebd6e)

                          IQR(Inter Quartile Range)


import pandas as pd


import numpy as np


import seaborn as sns


ir = pd.read_csv('iris.csv')

ir

![359346510-ed22d468-5c28-473b-95ae-d320a20318ed](https://github.com/user-attachments/assets/37aa4a8a-6c49-470e-877d-b4fc6f45e8d7)

df.describe()

![359346713-8f5c18cc-090b-4d2f-b7b8-d9c567075880](https://github.com/user-attachments/assets/fef5d7cd-a635-404f-8f49-1a71d60019b5)

sns.boxplot(x='sepal_width',data=ir)

![359346978-878c8eb5-0cb4-4bae-92b1-e009c7a0f2d5](https://github.com/user-attachments/assets/4fac0a20-d130-48df-af6c-52e065d8ed5a)

c1=ir.sepal_width.quantile(0.25)


c3=ir.sepal_width.quantile(0.75)


iq=c3-c1


print(c3)

![359347190-fdeb48e0-9ff1-4797-a9d2-dd8cffa13ab0](https://github.com/user-attachments/assets/737a4fb1-3907-4bad-a5e1-e3c7b0cb0e47)

rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']

![359347382-66784894-6712-4158-9ab1-06141fa1afba](https://github.com/user-attachments/assets/8b39ad8b-2626-4fe4-90f9-55fc6b7c744f)

delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid

![359347582-1c04e5dd-0c4e-4401-889a-904b868c669f](https://github.com/user-attachments/assets/a2b74b5e-43fb-44bf-99b5-cb268adc18f9)

sns.boxplot(x='sepal_width',data=delid)

![359347723-b9b8ca1c-75f1-412a-82ce-01fd46f8eb7f](https://github.com/user-attachments/assets/64e0523b-e8a0-464c-abf7-e346f458cf1e)

                         Z-Score

import matplotlib.pyplot as plt


import pandas as pd


import numpy as np


import scipy.stats as stats



dataset=pd.read_csv("heights.csv")


dataset

![359348457-5a8e71e5-679c-4701-b5e9-1b9ab3608f65](https://github.com/user-attachments/assets/31dfcb9a-6cc0-466b-a022-745eafe33ccf)

df = pd.read_csv("heights.csv")


q1 = df['height'].quantile(0.25)


q2 = df['height'].quantile(0.5)


q3 = df['height'].quantile(0.75)



iqr = q3-q1


iqr

![359348704-ced4f0f5-1ac0-4fb9-b95f-656d7d63803e](https://github.com/user-attachments/assets/f3f3f85f-1f19-4594-88b0-4653dee95033)

low = q1 - 1.5*iqr


low

![359348809-f1db4ad4-4c6b-4461-9eab-27cb09ceaa5c](https://github.com/user-attachments/assets/465ec76f-24ac-4da6-a168-dd0a5762a5a8)

high = q3 + 1.5*iqr


high

![359348994-49676c23-9961-4e90-bf6b-e1d41c22b4c6](https://github.com/user-attachments/assets/8ce3da69-ad5e-437a-9a07-cc3cffbb4224)

df1 = df[((df['height'] >=low)& (df['height'] <=high))]


df1

![359349173-72acbf1b-2c51-413b-b831-f81a3b4457ae](https://github.com/user-attachments/assets/5f3baf4e-2aa0-4789-babd-458b8a9cb8bd)

z = np.abs(stats.zscore(df['height']))


z

![359349473-1fe0e609-cd7d-422c-8312-c0f963fc7a20](https://github.com/user-attachments/assets/997a1d9a-1a8c-4d67-ae63-bac8632f3b7b)

df1 = df[z<3]


df1

![359349669-c3efb880-635b-47f5-a6dc-4e45d0f0a35b](https://github.com/user-attachments/assets/c5c38d59-0471-4c6f-bce5-e7508ed7227e)

# Result
          Hence the data was cleaned , outliers were detected and removed.
