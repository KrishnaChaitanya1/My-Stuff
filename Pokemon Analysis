"""
Created on Sun Dec 10 12:31:23 2017

@author: Krishna
"""

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

data = pd.read_csv(r'C:\Simulation Kernel\The Tings\Arcanefiles\Datasets\Pokemon.csv') # Path for the file
#data.info()

#print(data.isnull().sum())
#print(data.head(10))
data.drop(['#'], inplace=True, axis=1)
#print(data.head())

data = data.set_index('Name')
#print(data.head(10))
data.index = data.index.str.replace(".*(?=Mega)", "")
#print(data.head(10))

#print(data.shape)
#print(data.columns)

data['Type 2'].fillna(data['Type 1'], inplace=True)
#print(data.head(10))
#print(data.isnull().sum())

#print('Pokemon with High HP: ', data['HP'].argmax())
#print('Pokemon with Low HP: ', data['HP'].argmin())
#print('Pokemon with High Attack: ', data['Attack'].argmax())
#print('Pokemon with Low Attack: ', data['Attack'].argmin())
#print('Pokemon with High Defense: ', data['Defense'].argmax())
#print('Pokemon with Low Defense: ', data['Defense'].argmin())

#print(data.describe())

# Total Overview of The Pokemon Types
#print(data['Type 1'].value_counts(), '\n', data['Type 2'].value_counts())
labels = 'Water', 'Normal', 'Grass', 'Bug', 'Psychic', 'Fire', 'Electric', 'Rock', 'Other'
sizes= [112, 98, 70, 69, 57, 52, 44, 44, 175]
colors= ['b', 'm', '#00FF00', '#808000', '#008080', 'r', 'y', '#641E16', '#00FFFF']
explode= (0.1, 0.1, 0.1, 0.1, 0.1, 0.1, 0.1, 0.1, 0.1)
plt.pie(sizes, explode=explode, labels=labels, colors=colors, shadow=True, 
    autopct='%1.1f%%')
plt.title('Percentage of Different Types of Type 1 Pokemon')
fig=plt.gcf()
fig.set_size_inches(10, 10)
#plt.close()
plt.show()

# Univariate Plots
f, ax=plt.subplots(1, 3, figsize=(15, 5))
sns.distplot(data['Attack'], color='c', bins=25, ax=ax[0])
ax[0].set_title('Attack Univariate Plot')
sns.distplot(data['Defense'], color='m', bins=25, ax=ax[1])
ax[1].set_title('Defense Univariate Plot')
sns.distplot(data['HP'], color='b', bins=25, ax=ax[2])
ax[2].set_title('HP Univariate Plot')
#plt.close()
plt.show()

# Bivariate Comparision Plots

f, ax=plt.subplots(1, 3, figsize=(15, 5))
sns.boxplot(x=data['Type 1'], y=data['Attack'], data=data, ax=ax[0], linewidth=0.5)
ax[0].set_title('Type 1 vs Attack Scatter Plot')
ax[0].set_xticklabels(data['Type 1'],rotation=90)

sns.boxplot(x=data['Type 1'], y=data['Defense'], data=data, ax=ax[1], linewidth=0.5)
ax[1].set_title('Type 1 vs Defense Scatter Plot')
ax[1].set_xticklabels(data['Type 1'],rotation=90)

sns.boxplot(x=data['Type 1'], y=data['HP'], data=data, ax=ax[2], linewidth=0.5)
ax[2].set_title('Type 1 vs HP Plot')
ax[2].set_xticklabels(data['Type 1'],rotation=90)
#plt.close()
plt.show()

f, ax=plt.subplots(1, 3, figsize=(25, 5))
sns.violinplot(x=data['Type 2'], y=data['Attack'], data=data, ax=ax[0], split=True)
ax[0].set_title('Type 2 vs Attack Violin Plot')
ax[0].set_xticklabels(data['Type 2'], rotation=90)

sns.violinplot(x=data['Type 2'], y=data['Defense'], data=data, ax=ax[1], split=True)
ax[1].set_title('Type 2 vs Defense Violin Plot')
ax[1].set_xticklabels(data['Type 2'], rotation=90)

sns.violinplot(x=data['Type 2'], y=data['HP'], data=data, ax=ax[2], split=True)
ax[2].set_title('Type 2 vs HP Violin Plot')
ax[2].set_xticklabels(data['Type 2'], rotation=90)
#plt.close()
plt.show()

plt.subplots(figsize=(15, 5))
plt.title('Strongest Generation')
sns.violinplot(x=data['Generation'], y=data['Total'], data=data)
#plt.close()
plt.show()

# Correlation plot
f, ax = plt.subplots(figsize=(10, 10))
sns.heatmap(data.corr(), annot=True, fmt='.2f', linewidths=0.5, ax=ax)
#plt.close()
plt.show()
