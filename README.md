# 2345031
{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 3,
   "id": "899964de",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "First 5 rows of the dataset:\n",
      "  InvoiceNo StockCode                          Description  Quantity  \\\n",
      "0    536365    85123A   WHITE HANGING HEART T-LIGHT HOLDER         6   \n",
      "1    536365     71053                  WHITE METAL LANTERN         6   \n",
      "2    536365    84406B       CREAM CUPID HEARTS COAT HANGER         8   \n",
      "3    536365    84029G  KNITTED UNION FLAG HOT WATER BOTTLE         6   \n",
      "4    536365    84029E       RED WOOLLY HOTTIE WHITE HEART.         6   \n",
      "\n",
      "        InvoiceDate  UnitPrice  CustomerID         Country  \n",
      "0  01-12-2010 08:26       2.55     17850.0  United Kingdom  \n",
      "1  01-12-2010 08:26       3.39     17850.0  United Kingdom  \n",
      "2  01-12-2010 08:26       2.75     17850.0  United Kingdom  \n",
      "3  01-12-2010 08:26       3.39     17850.0  United Kingdom  \n",
      "4  01-12-2010 08:26       3.39     17850.0  United Kingdom  \n",
      "\n",
      "Data types of each column:\n",
      "InvoiceNo       object\n",
      "StockCode       object\n",
      "Description     object\n",
      "Quantity         int64\n",
      "InvoiceDate     object\n",
      "UnitPrice      float64\n",
      "CustomerID     float64\n",
      "Country         object\n",
      "dtype: object\n",
      "\n",
      "Dataset shape: (541909, 8)\n",
      "\n",
      "Missing values per column:\n",
      "InvoiceNo           0\n",
      "StockCode           0\n",
      "Description      1454\n",
      "Quantity            0\n",
      "InvoiceDate         0\n",
      "UnitPrice           0\n",
      "CustomerID     135080\n",
      "Country             0\n",
      "dtype: int64\n",
      "\n",
      "Descriptive statistics:\n",
      "            Quantity      UnitPrice     CustomerID\n",
      "count  541909.000000  541909.000000  406829.000000\n",
      "mean        9.552250       4.611114   15287.690570\n",
      "std       218.081158      96.759853    1713.600303\n",
      "min    -80995.000000  -11062.060000   12346.000000\n",
      "25%         1.000000       1.250000   13953.000000\n",
      "50%         3.000000       2.080000   15152.000000\n",
      "75%        10.000000       4.130000   16791.000000\n",
      "max     80995.000000   38970.000000   18287.000000\n",
      "\n",
      "Potential outliers in Quantity: 346\n",
      "\n",
      "Potential outliers in UnitPrice: 374\n",
      "\n",
      "Initial Observations: Check for negative Quantity, missing CustomerID, and inconsistent Description.\n",
      "\n",
      "Missing values after handling:\n",
      "InvoiceNo         0\n",
      "StockCode         0\n",
      "Description    1454\n",
      "Quantity          0\n",
      "InvoiceDate       0\n",
      "UnitPrice         0\n",
      "CustomerID        0\n",
      "Country           0\n",
      "dtype: int64\n",
      "\n",
      "Updated data types:\n",
      "InvoiceNo              object\n",
      "StockCode              object\n",
      "Description            object\n",
      "Quantity                int64\n",
      "InvoiceDate    datetime64[ns]\n",
      "UnitPrice             float64\n",
      "CustomerID              int32\n",
      "Country              category\n",
      "dtype: object\n",
      "\n",
      "Shape after removing duplicates: (25900, 8)\n",
      "\n",
      "Unique countries after standardization: ['United Kingdom' 'France' 'Australia' 'Netherlands' 'Germany' 'Norway'\n",
      " 'Eire' 'Switzerland' 'Spain' 'Poland' 'Portugal' 'Italy' 'Belgium'\n",
      " 'Lithuania' 'Japan' 'Iceland' 'Channel Islands' 'Denmark' 'Cyprus'\n",
      " 'Sweden' 'Austria' 'Israel' 'Finland' 'Bahrain' 'Greece' 'Hong Kong'\n",
      " 'Singapore' 'Lebanon' 'United Arab Emirates' 'Saudi Arabia'\n",
      " 'Czech Republic' 'Canada' 'Unspecified' 'Brazil' 'Usa'\n",
      " 'European Community' 'Malta' 'Rsa']\n",
      "\n",
      "Max Quantity after capping: 336\n",
      "Max UnitPrice after capping: 125.0\n",
      "\n",
      "Sample of new features:\n",
      "    TotalPurchase  PurchaseMonth\n",
      "0           15.30            1.0\n",
      "7           11.10            1.0\n",
      "9           54.08            1.0\n",
      "21          25.50            1.0\n",
      "25          17.85            1.0\n",
      "\n",
      "Country summary:\n",
      "                            mean  count\n",
      "Country                                \n",
      "Australia             105.695797     69\n",
      "Austria                43.512632     19\n",
      "Bahrain                12.475000      4\n",
      "Belgium                18.702185    119\n",
      "Brazil                175.200000      1\n",
      "Canada                 92.693333      6\n",
      "Channel Islands        38.137879     33\n",
      "Cyprus                 27.055000     20\n",
      "Czech Republic         -1.106000      5\n",
      "Denmark                56.600476     21\n",
      "Eire                   35.266722    360\n",
      "European Community     16.350000      5\n",
      "Finland                61.629583     48\n",
      "France                 25.863905    461\n",
      "Germany                23.213980    603\n",
      "Greece                 31.016667      6\n",
      "Hong Kong              30.898000     15\n",
      "Iceland                23.308571      7\n",
      "Israel                 10.523333      9\n",
      "Italy                  16.388727     55\n",
      "Japan                  72.427857     28\n",
      "Lebanon                17.400000      1\n",
      "Lithuania              42.000000      4\n",
      "Malta                  37.100000     10\n",
      "Netherlands           126.959109    101\n",
      "Norway                 22.494500     40\n",
      "Poland                 20.595417     24\n",
      "Portugal               15.627183     71\n",
      "Rsa                     6.800000      1\n",
      "Saudi Arabia           -4.855000      2\n",
      "Singapore              28.446000     10\n",
      "Spain                  32.291619    105\n",
      "Sweden                 49.591522     46\n",
      "Switzerland            24.467027     74\n",
      "United Arab Emirates   29.000000      3\n",
      "United Kingdom         17.801835  23494\n",
      "Unspecified            18.495385     13\n",
      "Usa                    12.647143      7\n",
      "\n",
      "Pivot table (TotalPurchase by Country and Month):\n",
      "PurchaseMonth               1.0         2.0        3.0         4.0   \\\n",
      "Country                                                               \n",
      "Australia             299.600000  148.380000  70.486667  154.413333   \n",
      "Austria                19.500000    7.560000  39.600000         NaN   \n",
      "Bahrain                      NaN         NaN        NaN         NaN   \n",
      "Belgium                 8.130000    7.230000  33.333333   17.225000   \n",
      "Canada                       NaN         NaN        NaN  356.160000   \n",
      "Channel Islands        35.400000   40.800000        NaN         NaN   \n",
      "Cyprus                       NaN  -33.900000  20.800000    0.000000   \n",
      "Czech Republic        -21.750000         NaN        NaN         NaN   \n",
      "Denmark                      NaN         NaN        NaN         NaN   \n",
      "Eire                   47.870000   26.200000  18.857143    9.754286   \n",
      "European Community           NaN         NaN        NaN         NaN   \n",
      "Finland               137.800000   46.640000        NaN  121.346000   \n",
      "France                 45.262667   19.929167  34.541176   24.732667   \n",
      "Germany                 6.030556    6.623333  17.410714   13.753333   \n",
      "Greece                       NaN         NaN        NaN    9.900000   \n",
      "Hong Kong                    NaN         NaN        NaN  -10.950000   \n",
      "Iceland                      NaN   13.200000        NaN         NaN   \n",
      "Israel                 17.000000         NaN        NaN    6.950000   \n",
      "Italy                 120.000000   85.920000  15.000000    3.937500   \n",
      "Japan                        NaN   -7.650000        NaN -528.000000   \n",
      "Lithuania                    NaN         NaN        NaN         NaN   \n",
      "Malta                 -19.900000         NaN        NaN         NaN   \n",
      "Netherlands           120.550000  211.076667  -2.400000         NaN   \n",
      "Norway                 -8.566667   25.200000  19.800000         NaN   \n",
      "Poland                -39.800000   16.500000  24.150000   56.100000   \n",
      "Portugal                     NaN   18.600000   6.100000         NaN   \n",
      "Saudi Arabia                 NaN         NaN -14.750000         NaN   \n",
      "Singapore                    NaN         NaN        NaN    0.000000   \n",
      "Spain                  10.500000         NaN  35.210000   23.587500   \n",
      "Sweden                114.450000   25.500000  -8.500000   13.555000   \n",
      "Switzerland            19.800000   -1.250000  14.250000   17.000000   \n",
      "United Arab Emirates   19.800000         NaN        NaN         NaN   \n",
      "United Kingdom         31.379287   35.441179  38.529759   31.438760   \n",
      "Unspecified                  NaN    2.950000        NaN         NaN   \n",
      "Usa                          NaN    5.040000        NaN         NaN   \n",
      "\n",
      "PurchaseMonth               5.0         6.0         7.0        8.0   \\\n",
      "Country                                                               \n",
      "Australia             338.780000   92.550000   17.025000  22.500000   \n",
      "Austria                      NaN   39.600000         NaN  74.720000   \n",
      "Bahrain              -205.740000         NaN         NaN        NaN   \n",
      "Belgium                12.487500   17.750000    5.091429  14.387500   \n",
      "Canada                       NaN         NaN         NaN        NaN   \n",
      "Channel Islands        35.575000   25.350000         NaN  -4.250000   \n",
      "Cyprus                       NaN         NaN   14.190000        NaN   \n",
      "Czech Republic               NaN         NaN   10.080000        NaN   \n",
      "Denmark                10.200000         NaN  132.800000        NaN   \n",
      "Eire                   22.326364   38.161111   40.346000  14.217692   \n",
      "European Community     10.200000   45.000000         NaN        NaN   \n",
      "Finland                67.000000         NaN  -21.040000        NaN   \n",
      "France                 28.179583    9.955455   18.738571  11.945000   \n",
      "Germany                27.074348    9.695185   30.698929   6.620435   \n",
      "Greece                       NaN  135.000000         NaN  24.960000   \n",
      "Hong Kong                    NaN         NaN         NaN        NaN   \n",
      "Iceland                      NaN         NaN   19.866667        NaN   \n",
      "Israel                       NaN         NaN         NaN        NaN   \n",
      "Italy                   3.675000   -3.066667   23.850000        NaN   \n",
      "Japan                 160.050000   -2.925000  -18.980000        NaN   \n",
      "Lithuania              35.000000         NaN         NaN  63.000000   \n",
      "Malta                        NaN         NaN         NaN  14.850000   \n",
      "Netherlands           149.916667   32.127500   62.400000  71.824000   \n",
      "Norway                 29.700000   15.000000         NaN  10.080000   \n",
      "Poland                 17.282500         NaN         NaN  15.000000   \n",
      "Portugal                9.530000   15.187500    6.730000  26.865000   \n",
      "Saudi Arabia                 NaN         NaN         NaN        NaN   \n",
      "Singapore             202.500000         NaN         NaN        NaN   \n",
      "Spain                 175.200000    8.750000   28.012000  18.750000   \n",
      "Sweden                  0.000000   97.080000         NaN  32.216667   \n",
      "Switzerland            14.750000  109.900000         NaN  67.960000   \n",
      "United Arab Emirates         NaN         NaN         NaN        NaN   \n",
      "United Kingdom         36.639474   26.044808   38.910975  23.942295   \n",
      "Unspecified                  NaN         NaN         NaN   9.360000   \n",
      "Usa                    27.040000         NaN         NaN -20.800000   \n",
      "\n",
      "PurchaseMonth               9.0         10.0        11.0        12.0  \n",
      "Country                                                               \n",
      "Australia              17.700000   81.600000   13.500000   17.550000  \n",
      "Austria                      NaN         NaN         NaN   15.000000  \n",
      "Bahrain                30.000000         NaN         NaN         NaN  \n",
      "Belgium                36.337500    8.190000   16.893333   13.812000  \n",
      "Canada                       NaN         NaN   23.400000         NaN  \n",
      "Channel Islands        18.150000   50.850000         NaN         NaN  \n",
      "Cyprus                       NaN   60.480000         NaN   10.000000  \n",
      "Czech Republic               NaN         NaN         NaN         NaN  \n",
      "Denmark                46.683333   34.800000   33.300000         NaN  \n",
      "Eire                    6.930000  104.288125   32.877857   38.444444  \n",
      "European Community           NaN   -8.500000         NaN         NaN  \n",
      "Finland                      NaN         NaN   29.500000   65.350000  \n",
      "France                 14.961667   35.313125   42.540000   33.652941  \n",
      "Germany                19.468421   34.405789   14.007826   35.508889  \n",
      "Greece                       NaN         NaN  -22.480000         NaN  \n",
      "Hong Kong                    NaN         NaN         NaN   16.500000  \n",
      "Iceland                24.960000         NaN         NaN         NaN  \n",
      "Israel                 14.850000   15.000000         NaN         NaN  \n",
      "Italy                  42.960000   33.000000   -4.125000         NaN  \n",
      "Japan                 458.100000         NaN         NaN   87.000000  \n",
      "Lithuania                    NaN         NaN         NaN         NaN  \n",
      "Malta                        NaN         NaN         NaN         NaN  \n",
      "Netherlands            47.383333  150.586667  162.533333  128.820000  \n",
      "Norway                 29.960000   51.000000    6.000000   16.453333  \n",
      "Poland                       NaN         NaN         NaN         NaN  \n",
      "Portugal               22.600000   16.500000   34.600000    1.983333  \n",
      "Saudi Arabia                 NaN         NaN         NaN         NaN  \n",
      "Singapore                    NaN         NaN         NaN         NaN  \n",
      "Spain                  18.316667   20.175000  137.690000         NaN  \n",
      "Sweden                 42.960000  -28.800000   11.675000  132.000000  \n",
      "Switzerland            55.350000   43.700000   -3.390000   10.475000  \n",
      "United Arab Emirates         NaN         NaN         NaN         NaN  \n",
      "United Kingdom       -169.435631   26.657030   29.090242  -11.158619  \n",
      "Unspecified                  NaN   30.000000   15.900000         NaN  \n",
      "Usa                          NaN   19.800000         NaN  -10.000000  \n",
      "\n",
      "Normalized TotalPurchase sample:\n",
      "0     0.957466\n",
      "7     0.957442\n",
      "9     0.957686\n",
      "21    0.957524\n",
      "25    0.957480\n",
      "Name: TotalPurchase_normalized, dtype: float64\n",
      "\n",
      "Quantity category distribution:\n",
      "QuantityCategory\n",
      "Low          10679\n",
      "Medium        8114\n",
      "Very High     1121\n",
      "High           814\n",
      "Name: count, dtype: int64\n",
      "\n",
      "--- Data Wrangling Report ---\n",
      "Initial Findings: Missing CustomerID (25% rows), negative Quantity values, inconsistent Description.\n",
      "Cleaning Decisions: Dropped missing UnitPrice rows; tagged missing CustomerID as -1; capped outliers.\n",
      "Transformations: Added TotalPurchase and PurchaseMonth; binned Quantity for segmentation.\n",
      "Assumptions: Negative Quantity treated as returns, capped at 0 if needed; missing CustomerID valid for analysis.\n",
      "Summary: Final dataset has 25900 rows, no missing UnitPrice, and enhanced features.\n"
     ]
    }
   ],
   "source": [
    "import pandas as pd\n",
    "import numpy as np\n",
    "\n",
    "# --- Phase 1: Data Loading and Initial Inspection ---\n",
    "\n",
    "# Load dataset\n",
    "df = pd.read_csv(r\"C:\\Users\\Aqeel\\OneDrive\\Desktop\\Copy of Online Retail.csv\")\n",
    "\n",
    "# Display first few rows\n",
    "print(\"First 5 rows of the dataset:\")\n",
    "print(df.head())\n",
    "\n",
    "# Print data types\n",
    "print(\"\\nData types of each column:\")\n",
    "print(df.dtypes)\n",
    "\n",
    "# Number of rows and columns\n",
    "print(\"\\nDataset shape:\", df.shape)\n",
    "\n",
    "# Initial Data Exploration\n",
    "print(\"\\nMissing values per column:\")\n",
    "print(df.isnull().sum())\n",
    "\n",
    "# Descriptive statistics for numerical columns\n",
    "print(\"\\nDescriptive statistics:\")\n",
    "print(df.describe())\n",
    "\n",
    "# Identify potential outliers in Quantity and UnitPrice\n",
    "for col in ['Quantity', 'UnitPrice']:\n",
    "    mean = df[col].mean()\n",
    "    std = df[col].std()\n",
    "    outliers = df[(df[col] > mean + 3 * std) | (df[col] < mean - 3 * std)][col]\n",
    "    print(f\"\\nPotential outliers in {col}:\", outliers.count())\n",
    "\n",
    "# Observations\n",
    "print(\"\\nInitial Observations: Check for negative Quantity, missing CustomerID, and inconsistent Description.\")\n",
    "\n",
    "# --- Phase 2: Data Cleaning ---\n",
    "\n",
    "# 1. Handling Missing Values\n",
    "# Drop rows with missing UnitPrice (critical for analysis)\n",
    "df['UnitPrice'] = pd.to_numeric(df['UnitPrice'], errors='coerce')  # Ensure numeric\n",
    "df.dropna(subset=['UnitPrice'], inplace=True)\n",
    "\n",
    "# For CustomerID, assign a placeholder (-1) for missing values\n",
    "df['CustomerID'] = df['CustomerID'].fillna(-1)  # Placeholder for unidentified customers\n",
    "print(\"\\nMissing values after handling:\")\n",
    "print(df.isnull().sum())\n",
    "\n",
    "# Justification: UnitPrice is essential; missing CustomerID can be tagged for analysis.\n",
    "\n",
    "# 2. Data Type Conversion\n",
    "df['InvoiceDate'] = pd.to_datetime(df['InvoiceDate'], errors='coerce')  # Convert to datetime\n",
    "df['CustomerID'] = df['CustomerID'].astype(int)  # Convert to integer\n",
    "df['Country'] = df['Country'].astype('category')  # Convert to categorical\n",
    "print(\"\\nUpdated data types:\")\n",
    "print(df.dtypes)\n",
    "\n",
    "# 3. Handling Duplicates\n",
    "# Remove duplicate rows based on InvoiceNo and CustomerID\n",
    "df = df.drop_duplicates(subset=['InvoiceNo', 'CustomerID'], keep='first')\n",
    "print(\"\\nShape after removing duplicates:\", df.shape)\n",
    "\n",
    "# 4. Addressing Inconsistencies\n",
    "# Standardize Country names (title case)\n",
    "df['Country'] = df['Country'].str.title()\n",
    "\n",
    "# Clean Description (remove extra spaces, uppercase)\n",
    "df['Description'] = df['Description'].str.strip().str.upper()\n",
    "print(\"\\nUnique countries after standardization:\", df['Country'].unique())\n",
    "\n",
    "# 5. Outlier Handling\n",
    "# Cap Quantity and UnitPrice at 99th percentile\n",
    "for col in ['Quantity', 'UnitPrice']:\n",
    "    cap_value = df[col].quantile(0.99)\n",
    "    df[col] = df[col].clip(upper=cap_value)\n",
    "print(\"\\nMax Quantity after capping:\", df['Quantity'].max())\n",
    "print(\"Max UnitPrice after capping:\", df['UnitPrice'].max())\n",
    "\n",
    "# Justification: Capping preserves data while mitigating extreme outliers.\n",
    "\n",
    "# --- Phase 3: Data Transformation ---\n",
    "\n",
    "# 1. Feature Engineering\n",
    "# Calculate total purchase value (Quantity * UnitPrice)\n",
    "df['TotalPurchase'] = df['Quantity'] * df['UnitPrice']\n",
    "\n",
    "# Extract month from InvoiceDate\n",
    "df['PurchaseMonth'] = df['InvoiceDate'].dt.month\n",
    "print(\"\\nSample of new features:\")\n",
    "print(df[['TotalPurchase', 'PurchaseMonth']].head())\n",
    "\n",
    "# Rationale: TotalPurchase reflects customer spending; PurchaseMonth aids temporal analysis.\n",
    "\n",
    "# 2. Data Aggregation and Summarization\n",
    "# Average TotalPurchase per Country\n",
    "country_summary = df.groupby('Country')['TotalPurchase'].agg(['mean', 'count'])\n",
    "print(\"\\nCountry summary:\")\n",
    "print(country_summary)\n",
    "\n",
    "# Pivot table: TotalPurchase by Country and PurchaseMonth\n",
    "pivot = df.pivot_table(values='TotalPurchase', index='Country', columns='PurchaseMonth', aggfunc='mean')\n",
    "print(\"\\nPivot table (TotalPurchase by Country and Month):\")\n",
    "print(pivot)\n",
    "\n",
    "# 3. Data Standardization/Normalization\n",
    "# Normalize TotalPurchase (min-max scaling)\n",
    "df['TotalPurchase_normalized'] = (df['TotalPurchase'] - df['TotalPurchase'].min()) / \\\n",
    "                                 (df['TotalPurchase'].max() - df['TotalPurchase'].min())\n",
    "print(\"\\nNormalized TotalPurchase sample:\")\n",
    "print(df['TotalPurchase_normalized'].head())\n",
    "\n",
    "# When needed: For models requiring comparable scales.\n",
    "\n",
    "# 4. Data Binning\n",
    "# Bin Quantity into categories\n",
    "quantity_bins = [0, 10, 50, 100, float('inf')]\n",
    "quantity_labels = ['Low', 'Medium', 'High', 'Very High']\n",
    "df['QuantityCategory'] = pd.cut(df['Quantity'], bins=quantity_bins, labels=quantity_labels, right=False)\n",
    "print(\"\\nQuantity category distribution:\")\n",
    "print(df['QuantityCategory'].value_counts())\n",
    "\n",
    "# --- Phase 4: Reporting and Documentation ---\n",
    "\n",
    "# 2. Data Wrangling Report (Printed Summary)\n",
    "print(\"\\n--- Data Wrangling Report ---\")\n",
    "print(\"Initial Findings: Missing CustomerID (25% rows), negative Quantity values, inconsistent Description.\")\n",
    "print(\"Cleaning Decisions: Dropped missing UnitPrice rows; tagged missing CustomerID as -1; capped outliers.\")\n",
    "print(\"Transformations: Added TotalPurchase and PurchaseMonth; binned Quantity for segmentation.\")\n",
    "print(\"Assumptions: Negative Quantity treated as returns, capped at 0 if needed; missing CustomerID valid for analysis.\")\n",
    "print(\"Summary: Final dataset has\", df.shape[0], \"rows, no missing UnitPrice, and enhanced features.\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "2b55ab84",
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3 (ipykernel)",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.11.5"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}

