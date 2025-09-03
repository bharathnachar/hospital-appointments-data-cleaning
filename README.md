# Hospital Appointments Data Cleaning

This project demonstrates step-by-step **data cleaning** using Python and Pandas on the KaggleV2-May-2016 hospital appointment dataset.

---

## 📌 Steps Performed

### 1. Identify and Handle Missing Values
```python
df.isnull().sum() ###

### 2. Remove Duplicate Rows
```python
df = df.dropna()   # or fillna()
df = df.drop_duplicates() ###

### 3. Standardize Text Values (e.g., Gender)
```python
df["Gender"] = df["Gender"].str.strip().str.lower()
df["Gender"] = df["Gender"].replace({
    "male": "Male",
    "m": "Male",
    "female": "Female",
    "f": "Female"
}) ###

### 4. Convert Date Formats
```python
df["AppointmentDay"] = pd.to_datetime(df["AppointmentDay"])
df["ScheduledDay"] = pd.to_datetime(df["ScheduledDay"])
df["AppointmentDay"] = df["AppointmentDay"].dt.strftime("%d-%m-%Y")
df["ScheduledDay"] = df["ScheduledDay"].dt.strftime("%d-%m-%Y") ###

### 5. Rename Column Headers
```python
df.columns = df.columns.str.strip().str.lower().str.replace(" ", "_") ###

### 6. Check and Fix Data Types
```python
df["age"] = df["age"].astype(int)
df["appointmentday"] = pd.to_datetime(df["appointmentday"], format="%d-%m-%Y") ###
