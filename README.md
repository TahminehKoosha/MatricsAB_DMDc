# MatricsAB_DMDc
## Overview
Welcome to "MatricAB", an innovative Python repository. My focus is on analyzing complex systems within the realms of neuroscience and psychology. The centerpiece of this repository is the `MatricAB` function, which is meticulously designed to calculate A and B matrices in linear time-invariant systems. These calculations are instrumental in dissecting the dynamics of neural networks and psychological states, offering a window into the intricate workings of the human mind and behavior.


## Installation
To get started with `MatricAB`, clone the repository and install the required Python packages:
```bash
git clone https://github.com/PsyControLab/MatricAB_DMDc.git
cd MatricAB_DMDc
pip install numpy pandas
```
## Usage
The MatricAB function is user-friendly and can be integrated easily into your data analysis workflow. Here's a step-by-step guide to using it:

```python
import pandas as pd
from MatricAB_DMDc import MatricAB_DMDc as PyC

# Example: Load your dataset into a pandas DataFrame
df = pd.read_csv('your_data.csv')

# Define parameters for the function
id_col = 'entity_id'  # This should be the name of the column with unique identifiers in your dataset
X_cols = ['state_var1', 'state_var2', 'state_var3']  # List of columns representing state variables
U_col = 'input'  # Column name for the input variable
n = 'd'  # The dimension of your state variable (n in A_{n x n})

# Execute the function to calculate the A and B matrices
df_AB = MatricAB(df, id_col, X_cols, U_col, n)

# Display the first few rows of the output
print(df_AB.head())

# Grouping df by 'Group' and 'entity_ids' and taking the first occurrence
df_grouped = df.groupby(['Group', 'entity_ids'], as_index=False)['entity_ids'].first()

# Merging df_grouped with df_AB on 'entity_ids'
df_final = df_AB.merge(df_grouped, on='entity_ids')

# Printing the shape of the merged DataFrame
print(df_final.shape)

# Displaying the first 3 rows of the merged DataFrame
df_final.head(3)

```
The function processes your data and returns a DataFrame with calculated A and B matrices for each unique entity, providing insights into the system's dynamics.

 **Citation:**
 Proctor, Joshua L., Brunton, Steven L., and Kutz, J. Nathan. "Dynamic mode decomposition with control." SIAM Journal on Applied Dynamical Systems 15.1 (2016): 142
 [Access Paper]([https://doi.org/your_DOI_here](https://doi.org/10.1137/15M1013857)

