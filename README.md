# Alzheimer's Disease Prediction
Project on Alzheimers Disease

By Ken Ogihara

## Introduction
In this project, I develop a model that can predict whether someone has Alzheimer's Disease with 94% accuracy. This dataset contains extensive information on 2,149 patients, including, demographic details, lifestyle factors, medical history, clinical history, symptoms, cognitive and functional assessments, and a diagnosis of Alzheimer's Disease. This dataset is taken from Kaggle.

A model that can predict diagnosis of Alzheimers is particularly helpful because it provides insight into the features and lifestyle factors that have a signficant influence on the development of the disease. Moreover, early detection of the disease allows for timely intervention, which can slow the progression of the disease. Early
detection also has immense benefits for healthcare allocation because it allows doctors to provide the necessary care and support at the right time; thereby, preventing the need for future intensive treatment. This dataset contains 35 columns:

### Alzheimer's Dataset Columns

#### General Information
| Column         | Description                                      |
|----------------|--------------------------------------------------|
| PatientID      | A unique identifier assigned to each patient (4751 to 6900). |
| DoctorInCharge | This column contains confidential information about the doctor in charge, with "XXXConfid" as the value for all patients. |

#### Demographic Details
| Column          | Description                                      |
|-----------------|--------------------------------------------------|
| Age             | The age of the patients ranges from 60 to 90 years. |
| Gender          | Gender of the patients, where 0 represents Male and 1 represents Female. |
| Ethnicity       | The ethnicity of the patients, coded as follows: 0: Caucasian, 1: African American, 2: Asian, 3: Other. |
| EducationLevel  | The education level of the patients, coded as follows: 0: None, 1: High School, 2: Bachelor's, 3: Higher. |

#### Lifestyle Factors
| Column             | Description                                        |
|--------------------|----------------------------------------------------|
| BMI                | Body Mass Index of the patients, ranging from 15 to 40. |
| Smoking            | Smoking status, where 0 indicates No and 1 indicates Yes. |
| AlcoholConsumption | Weekly alcohol consumption in units, ranging from 0 to 20. |
| PhysicalActivity   | Weekly physical activity in hours, ranging from 0 to 10. |
| DietQuality        | Diet quality score, ranging from 0 to 10.          |
| SleepQuality       | Sleep quality score, ranging from 4 to 10.         |

#### Medical History
| Column               | Description                                        |
|----------------------|----------------------------------------------------|
| FamilyHistoryAlzheimers | Family history of Alzheimer's Disease, where 0 indicates No and 1 indicates Yes. |
| CardiovascularDisease  | Presence of cardiovascular disease, where 0 indicates No and 1 indicates Yes. |
| Diabetes              | Presence of diabetes, where 0 indicates No and 1 indicates Yes. |
| Depression            | Presence of depression, where 0 indicates No and 1 indicates Yes. |
| HeadInjury            | History of head injury, where 0 indicates No and 1 indicates Yes. |
| Hypertension          | Presence of hypertension, where 0 indicates No and 1 indicates Yes. |

#### Clinical Measurements
| Column               | Description                                        |
|----------------------|----------------------------------------------------|
| SystolicBP           | Systolic blood pressure, ranging from 90 to 180 mmHg. |
| DiastolicBP          | Diastolic blood pressure, ranging from 60 to 120 mmHg. |
| CholesterolTotal     | Total cholesterol levels, ranging from 150 to 300 mg/dL. |
| CholesterolLDL       | Low-density lipoprotein cholesterol levels, ranging from 50 to 200 mg/dL. |
| CholesterolHDL       | High-density lipoprotein cholesterol levels, ranging from 20 to 100 mg/dL. |
| CholesterolTriglycerides | Triglycerides levels, ranging from 50 to 400 mg/dL. |

#### Cognitive and Functional Assessments
| Column               | Description                                        |
|----------------------|----------------------------------------------------|
| MMSE                 | Mini-Mental State Examination score, ranging from 0 to 30. Lower scores indicate cognitive impairment. |
| FunctionalAssessment | Functional assessment score, ranging from 0 to 10. Lower scores indicate greater impairment. |
| MemoryComplaints     | Presence of memory complaints, where 0 indicates No and 1 indicates Yes. |
| BehavioralProblems   | Presence of behavioral problems, where 0 indicates No and 1 indicates Yes. |
| ADL                  | Activities of Daily Living score, ranging from 0 to 10. Lower scores indicate greater impairment. |

#### Symptoms
| Column                    | Description                                        |
|---------------------------|----------------------------------------------------|
| Confusion                 | Presence of confusion, where 0 indicates No and 1 indicates Yes. |
| Disorientation            | Presence of disorientation, where 0 indicates No and 1 indicates Yes. |
| PersonalityChanges        | Presence of personality changes, where 0 indicates No and 1 indicates Yes. |
| DifficultyCompletingTasks | Presence of difficulty completing tasks, where 0 indicates No and 1 indicates Yes. |
| Forgetfulness             | Presence of forgetfulness, where 0 indicates No and 1 indicates Yes. |

#### Diagnosis Information
| Column                   | Description                                      |
|--------------------------|--------------------------------------------------|
| Diagnosis                | Diagnosis status for Alzheimer's Disease, where 0 indicates No and 1 indicates Yes. |

## Data Cleaning and Exploratory Data Analysis

1. **Removing irrelevant columns** I dropped DoctorInCharge because its only value, "XXXConfid", is not helpful in our analysis.

The first five rows of the DataFrame with some of the columns is shown below:

```py
print(alz.head()[["Age", "Gender", "Ethnicity", "BMI", "Smoking", "PhysicalActivity", "Diagnosis"]].to_markdown(index = False))
```

| Age | Gender | Ethnicity |   BMI | Smoking | Physical Activity | Diagnosis |
|----:|-------:|----------:|------:|--------:|------------------:|----------:|
|  73 |      0 |         0 | 22.93 |       0 |              6.33 |         0 |
|  89 |      0 |         0 | 26.83 |       0 |              7.62 |         0 |
|  73 |      0 |         3 | 17.80 |       0 |              7.84 |         0 |
|  74 |      1 |         0 | 33.80 |       1 |              8.43 |         0 |
|  89 |      0 |         0 | 20.72 |       0 |              6.31 |         0 |

### EDA

I first created a univariate plot that shows the distribution of patients according to their diagnosis.

<iframe
  src="assets/html.plot1.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>



