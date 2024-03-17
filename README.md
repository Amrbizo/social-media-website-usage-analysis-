# social-media-website-usage-analysis-
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import random
import numpy as np
cat=['fashion', 'sports', 'memes', 'technology','music', 'culture', 'family','health']


# Generating the DataFrame
dict = {
    'date': pd.date_range(start='2022-01-01', periods=500),
    'categories': [random.choice(cat) for _ in range(500)],
    'likes': [np.random.randint(0, 10000) for _ in range(500)]
}
df = pd.DataFrame(dict)
stacked = df.stack()

# Display value counts
print(stacked.value_counts())

# Convert 'likes' column to integer
df['likes'] = df['likes'].astype(int)

# Check the data type of the 'likes' column after conversion
print(df['likes'].dtype)
df.describe()
df.info()
df.head()
plt.hist(df['likes'], bins=10 ,color='skyblue', edgecolor='black')

# Add labels and a title
plt.xlabel('Likes')
plt.ylabel('count')
plt.title('Histogram of Likes')

# Show the plot
plt.show()
# Create a boxplot
plt.boxplot(df['likes'])

# Add labels and title
plt.xlabel('categories')
plt.ylabel('likes')
plt.title('boxplot of likes')

# Show the plot
plt.show()
df.groupby('categories')['likes'].mean()

            

