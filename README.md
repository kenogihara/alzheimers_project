# Alzheimer's Disease Prediction
Project on Alzheimers Disease

By Ken Ogihara

## Introduction
In this project, I develop a model that can predict whether someone has Alzheimer's Disease with 94% accuracy. This dataset contains extensive information on 2,149 patients, including, demographic details, lifestyle factors, medical history, clinical history, symptoms, cognitive and functional assessments, and a diagnosis of Alzheimer's Disease. This dataset is taken from Kaggle.

A model that can predict diagnosis of Alzheimers is particularly helpful because it provides insight into the features and lifestyle factors that have a signficant influence on the development of the disease. Moreover, early detection of the disease allows for timely intervention, which can slow the progression of the disease. Early
detection also has immense benefits for healthcare allocation because it allows doctors to provide the necessary care and support at the right time; thereby, preventing the need for future intensive treatment. This dataset contains 35 columns:

| Column                     | Description                                                                                     |
|----------------------------|-------------------------------------------------------------------------------------------------|
| PatientID                  | A unique identifier assigned to each patient (4751 to 6900).                                    |
| Age                        | The age of the patients ranges from 60 to 90 years.                                             |
| Gender                     | Gender of the patients, where 0 represents Male and 1 represents Female.                        |
| Ethnicity                  | The ethnicity of the patients, coded as follows: 0: Caucasian, 1: African American, 2: Asian, 3: Other. |
| EducationLevel             | The education level of the patients, coded as follows: 0: None, 1: High School, 2: Bachelor's, 3: Higher. |
| BMI                        | Body Mass Index of the patients, ranging from 15 to 40.                                         |
| Smoking                    | Smoking status, where 0 indicates No and 1 indicates Yes.                                       |
| AlcoholConsumption         | Weekly alcohol consumption in units, ranging from 0 to 20.                                      |
| PhysicalActivity           | Weekly physical activity in hours, ranging from 0 to 10.                                        |
| DietQuality                | Diet quality score, ranging from 0 to 10.                                                       |
| SleepQuality               | Sleep quality score, ranging from 4 to 10.                                                      |
| FamilyHistoryAlzheimers    | Family history of Alzheimer's Disease, where 0 indicates No and 1 indicates Yes.                |
| CardiovascularDisease      | Presence of cardiovascular disease, where 0 indicates No and 1 indicates Yes.                   |
| Diabetes                   | Presence of diabetes, where 0 indicates No and 1 indicates Yes.                                 |
| Depression                 | Presence of depression, where 0 indicates No and 1 indicates Yes.                               |
| HeadInjury                 | History of head injury, where 0 indicates No and 1 indicates Yes.                               |
| Hypertension               | Presence of hypertension, where 0 indicates No and 1 indicates Yes.                             |
| SystolicBP                 | Systolic blood pressure, ranging from 90 to 180 mmHg.                                           |
| DiastolicBP                | Diastolic blood pressure, ranging from 60 to 120 mmHg.                                          |
| CholesterolTotal           | Total cholesterol levels, ranging from 150 to 300 mg/dL.                                        |
| CholesterolLDL             | Low-density lipoprotein cholesterol levels, ranging from 50 to 200 mg/dL.                       |
| CholesterolHDL             | High-density lipoprotein cholesterol levels, ranging from 20 to 100 mg/dL.                      |
| CholesterolTriglycerides   | Triglycerides levels, ranging from 50 to 400 mg/dL.                                             |
| MMSE                       | Mini-Mental State Examination score, ranging from 0 to 30. Lower scores indicate cognitive impairment. |
| FunctionalAssessment       | Functional assessment score, ranging from 0 to 10. Lower scores indicate greater impairment.    |
| MemoryComplaints           | Presence of memory complaints, where 0 indicates No and 1 indicates Yes.                        |
| BehavioralProblems         | Presence of behavioral problems, where 0 indicates No and 1 indicates Yes.                      |
| ADL                        | Activities of Daily Living score, ranging from 0 to 10. Lower scores indicate greater impairment. |
| Confusion                  | Presence of confusion, where 0 indicates No and 1 indicates Yes.                                |
| Disorientation             | Presence of disorientation, where 0 indicates No and 1 indicates Yes.                           |
| PersonalityChanges         | Presence of personality changes, where 0 indicates No and 1 indicates Yes.                      |
| DifficultyCompletingTasks  | Presence of difficulty completing tasks, where 0 indicates No and 1 indicates Yes.              |
| Forgetfulness              | Presence of forgetfulness, where 0 indicates No and 1 indicates Yes.                            |
| Diagnosis                  | Diagnosis status for Alzheimer's Disease, where 0 indicates No and 1 indicates Yes.             |
| DoctorInCharge             | This column contains confidential information about the doctor in charge, with "XXXConfid" as the value for all patients. |


## Data Cleaning and Exploratory Data Analysis

1. **Removing irrelevant columns** I dropped DoctorInCharge because its only value, "XXXConfid", is not helpful in our analysis.

The first five rows of the DataFrame with some of the columns is shown below:

```py
print(alz.head()[["PatientID", "Age", "Gender", "Ethnicity", "BMI", "Smoking", "PhysicalActivity", "Diagnosis"]].to_markdown(index = False))
```

| PatientID | Age | Gender | Ethnicity |   BMI | Smoking | Physical Activity | Diagnosis |
|-----------|-----|--------|-----------|-------|---------|-------------------|-----------|
|      4751 |  73 |      0 |         0 | 22.93 |       0 |              6.33 |         0 |
|      4752 |  89 |      0 |         0 | 26.83 |       0 |              7.62 |         0 |
|      4753 |  73 |      0 |         3 | 17.80 |       0 |              7.84 |         0 |
|      4754 |  74 |      1 |         0 | 33.80 |       1 |              8.43 |         0 |
|      4755 |  89 |      0 |         0 | 20.72 |       0 |              6.31 |         0 |

### EDA: Univariate Analysis

I first created a univariate plot that shows the distribution of patients according to their diagnosis:

<iframe
  src="assets/html.plot1.html"
  width="700"
  height="500"
  frameborder="0"
></iframe>


My second univariate plot shows the prevalence of Alzheimer's Disease across races:

<iframe
  src="assets/html.plot1 copy.html"
  width="700"
  height="500"
  frameborder="0"
></iframe>

My third univariate plot shows the prevalence of Alzheimer's Disease across education level:

<iframe
  src="assets/html.plot1 copy2.html"
  width="700"
  height="500"
  frameborder="0"
></iframe>

### EDA: Bivariate Analysis

In our dataset, the "MemoryComplaints" variable refers to subjective experiences where individuals express dissatisfaction or concern about their memory function. These concerns are self-reported. 

The "Forgetfulness" variable refers to the actual experience of forgetting information or events. It is an observable behavior where indiviudals fail to recall something that they had previously learned or experienced. 

These bivariate plots along with their respective tables show the distribution of diagnosis based on these two variables:

#### Mosaic Plot #1: Relationship Between Forgetfulness and Diagnosis

<img src='data:image/png;base64,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8vb21iOPPKLZs2dfd3Z/48aNatiwoby9vRUaGqp+/frp0qVL9nGTk5P14osv2q8lSUpOTlabNm0UEBAgX19fVa1aVUuXLr1zT9RdhAAEDNCkSRPVqFFD8+fPlyRZlqV27drp7Nmz+u6777Ry5UodPHhQHTt2tPdZvny5OnfurH79+mnv3r2aNm2aZs2apdGjR0uSvvjiC02cOFHTpk1TUlKSFi5cqGrVqt10joMHD2rhwoVasmSJlixZou+++07jxo2z17/88suaN2+eZs+ere+//17h4eGKiorS2bNnFRoaqnnz5km6emYvJSVFb7311m09H926ddP27du1ePFibdq0SZZlqWXLlsrMzLS3SUtL09ixY/Xuu+9qz549CgoKUnR0tH766SetWbNG8+bN0/Tp0/Xzzz/b+1iWpVatWunEiRNaunSp4uLiFBERoaZNm+rs2bPq2LGjBgwYoKpVqyolJUUpKSlOzzlwNzl+/Lhatmyp2rVra9euXZoyZYree+89jRo1ymm72bNny93dXRs2bNC0adN05MgRPfHEE2rXrp127typXr16aciQIU77xMfHKyoqSo8//rh2796tuXPnav369erTp48kaf78+SpVqpRGjhxpv5YkqXfv3kpPT9fatWsVHx+v8ePH3/aZ/3zPApBvdO3a1Wrbtm2u6zp27GhVrlzZsizLWrFiheXm5mYdPXrUXr9nzx5LkrV161bLsizr4YcftsaMGeN0jA8++MAKCQmxLMuyJkyYYFWoUMHKyMi4pdliY2MtHx8f6/z58/aygQMHWnXr1rUsy7IuXrxoeXh4WB999JG9PiMjwypRooT1v//7v5ZlWda3335rSbLOnTt30691bTtfX1+n2+nTp639+/dbkqwNGzbY258+fdry9va2PvvsM8uyLGvmzJmWJGvnzp32NgkJCZYka9u2bfaypKQkS5I1ceJEy7Is65tvvrEKFSpkXblyxWme8uXLW9OmTbOfhxo1atzScwb8HXTt2tVyc3Nzei098cQT1uDBg62KFStaOTk59rb/7//9P8vPz8/Kzs62LMuyGjVqZNWsWdPpeDExMdZ9993ntGzIkCFOr+0uXbpYPXv2dNpm3bp1VoECBazLly9blmVZZcqUsV9711SrVs0aPnx4XjzsfM+ci4EAw1mWZb9NkpCQoNDQUIWGhtrrq1SpoiJFiighIUG1a9dWXFyctm3bZp/xk65eC3flyhWlpaXpySef1KRJk1SuXDk1b95cLVu2VJs2bW56jWFYWJj8/f3t+yEhIfYZtIMHDyozM1MNGjSw13t4eKhOnTpKSEi4rce8bt06p68XEBCgDRs2yN3dXXXr1rWXBwYGqmLFik5fp2DBgqpevbp9PzExUe7u7oqIiLCXhYeHKyAgwL4fFxenixcvKjAw0GmOy5cv6+DBg7f1GIC/g0ceeURTpkyx7/v6+qp3796qV6+e/X1Fkho0aKCLFy/q2LFjKl26tCTpgQcecDpWYmKiateu7bSsTp06Tvfj4uJ04MABffTRR/Yyy7KUk5Ojw4cPq3LlyrnO2a9fPz333HNasWKFIiMj1b59e6fXMX5FAAKGSEhIUNmyZSU5x+Bv/XZ5Tk6ORowYoccff/y67by8vBQaGqrExEStXLlSq1at0vPPP6/XX39d3333nTw8PHKd4ffLHQ6H/elk6//+V8rfz3WjWW9F2bJlVaRIkeuOl5vffx1vb2+n+zfb75qcnByFhIRozZo11233+zmAu4mvr6/Cw8OdluX22sztdezr63vL+12Tk5OjXr165Xpd8bWwzE337t0VFRWlr776SitWrNDYsWM1YcIE9e3b9yaPzkxcAwgYYPXq1YqPj1f79u0lXT3bd/ToUf3444/2Nnv37lVqaqr9L+uIiAglJiYqPDz8utu1T8N6e3vrscce03/+8x+tWbNGmzZtUnx8/G3NGB4eroIFC2r9+vX2sszMTG3fvt2e6dqnB7Ozs2/ra0hXH3tWVpa2bNliLztz5oz2799/w7MKklSpUiVlZWVpx44d9rIDBw44XbQeERGhEydOyN3d/brnrGjRovZj+DPzA38XVapU0caNG53ibePGjfL391fJkiVvuF+lSpXsD3dds337dqf7ERER2rNnT67ff659H7jRayk0NFTPPvus5s+frwEDBmjGjBl/5mHmWwQgkM+kp6frxIkTOn78uL7//nuNGTNGbdu2VevWrRUdHS1JioyMVPXq1dWpUyd9//332rp1q6Kjo9WoUSP77Zphw4Zpzpw5Gj58uPbs2aOEhATNnTvX/ll6s2bN0nvvvacffvhBhw4d0gcffCBvb2+VKVPmtub29fXVc889p4EDB2rZsmXau3evevToobS0ND3zzDOSpDJlysjhcGjJkiU6deqULl68+Ie/zr333qu2bduqR48eWr9+vXbt2qXOnTurZMmSatu27Q33q1SpkiIjI9WzZ09t3bpVO3bsUM+ePZ3OFEZGRqpevXpq166dli9friNHjmjjxo169dVX7b/gwsLCdPjwYe3cuVOnT59Wenr6bTxbgOs9//zz+vHHH9W3b1/t27dPixYtUmxsrF566aWb/sikXr16ad++fYqJidH+/fv12Wef2Z+Gv/ZaiomJ0aZNm9S7d2/t3LlTSUlJWrx4sdOZvLCwMK1du1bHjx/X6dOnJUkvvPCCli9frsOHD+v777/X6tWrb/oPO6O54LpDAH+Rrl27WpIsSZa7u7tVrFgxKzIy0nr//ffti7KvSU5Oth577DHL19fX8vf3t5588knrxIkTTtssW7bMql+/vuXt7W0VKlTIqlOnjjV9+nTLsixrwYIFVt26da1ChQpZvr6+1oMPPmitWrXqhrPl9uGHiRMnWmXKlLHvX7582erbt69VtGhRy9PT02rQoIH9oZRrRo4caQUHB1sOh8Pq2rVrrl/rv31Y5OzZs1aXLl2swoULW97e3lZUVJS1f/9+e/3MmTOtwoULX7ffTz/9ZLVo0cLy9PS0ypQpY3388cdWUFCQNXXqVHub8+fPW3379rVKlChheXh4WKGhoVanTp3sD9xcuXLFat++vVWkSBFLkjVz5swbPmfA38HNPly2Zs0aq3bt2lbBggWt4OBgKyYmxsrMzLTXN2rUyOrfv/91+y1atMgKDw+3PD09rcaNG1tTpkyxJNkf8LAsy9q6davVrFkzy8/Pz/L19bWqV69ujR492l6/adMmq3r16panp6d1LWf69OljlS9f3vL09LSKFStmdenSxTp9+nTePBH5jMOybnBhCwDgpo4dO6bQ0FCtWrVKTZs2dfU4wF1r9OjRmjp1qtNlKfhr8SEQALhFq1ev1sWLF1WtWjWlpKTo5ZdfVlhYmBo2bOjq0YC7yjvvvKPatWsrMDBQGzZs0Ouvv27/jD/cGQQgANyizMxMDR48WIcOHZK/v7/q16+vjz766IafegaQu6SkJI0aNUpnz55V6dKlNWDAAA0aNMjVYxmFt4ABAAAMw6eAAQAADEMAAgAAGIYABAAAMAwBCAAAYBgCEAAAwDAEIAAAgGEIQAAAAMMQgAAAAIYhAAEAAAxDAAIAABiGAAQAADAMAQgAAGAYAhAAAMAwBCAAAIBh/j/LpRX+mzTYkgAAAABJRU5ErkJggg=='>




| Forgetfulness   |   Diagnosis |
|:-------------------|------------:|
| Does not Forget    |    0.353764 |
| Forgets            |    0.353395 |



According to the first mosaic plot, we see that the majority of patients are not considered forgetful. Regardless, in both categories, the proportion of those who are diagnosed are approximately the same. This shows that the presence of forgetfulness is not a good indicator of Alzheimer's Disease.

#### Mosaic Plot #2: Relationship Between MemoryComplaints and Diagnosis


<img src='data:image/png;base64,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wK4d13GvAOD6uCoB2KxZM4WGhmr8+PGXXO6jjz5SpUqV5OPjo8jISE2aNMk5r3Hjxtq3b58ef/xx59m9SwkKClJoaKjKlCmjhg0bavr06Ro2bJiGDx+uzMxMSfkvAR85ckRdunRR6dKl5e/vr8qVK2vWrFku2z158qS6du2qgIAAhYWFacqUKWrcuLEGDhzoXCYyMlLjxo1Tz549FRQUpDJlymj69Oku20lLS1OTJk3k5+enkJAQ9enTR6dOnXLOX7VqlerUqaOAgAAVLlxYDRo00L59+5zzFyxYoJo1a8rX11flypXTqFGjlJOT45y/c+dONWzYUL6+voqLi9Py5csv+XoBNsrNzdXOtG0KrxBzwfmZWzcpvEK083GLrklKXfyxzmZn6Ye932nn/9usSnXqX6/hAsB143U1NuLp6alx48bp/vvv16OPPqrSpUvnW2bz5s3q1KmTRo4cqc6dO2vt2rV65JFHFBISoqSkJM2dO1dVq1ZVnz591Lt37ysax2OPPabk5GR9/PHHevLJJ/PNP3PmjGrWrKkhQ4aoYMGCWrRokbp3765y5crp9ttvlyT985//VGpqqj755BOVKFFCw4cP15YtW1StWjWXbU2aNEnJyckaOnSoPvzwQz388MNq2LChKlasqF9//VUtWrRQ3bp19dVXX+nw4cPq1auX+vfvrxkzZignJ0ft27dX7969NWvWLGVnZ2vjxo3O6F26dKm6deuml156SXfeead2796tPn36SJJGjBihvLw83XPPPSpatKjWr1+vEydOuAQqgHNmvThRIcVDVe2Oxvnm7cn4WoveeUvJ7851ToupXktL3p+p+6tHKS83V537D1JETOx1HDFw7Zw+usvdQ4CkX0/su/xC18FVCUBJ+sc//qFq1appxIgRevPNN/PNnzx5spo2baphw4ZJkqKjo5Wenq7nn39eSUlJKlKkiDw9PZ1n9q5EkSJFVLx4ce3du/eC80uVKqUnnnjC+XjAgAFasmSJ/vOf/+j222/XyZMnNXPmTL3//vtq2rSpJCklJUUlS5bMt61WrVrpkUcekSQNGTJEU6ZM0apVq1SxYkW99957+u233/T2228rICBAkvTKK6+obdu2mjhxory9vXX8+HG1adNG5cuXlyTFxv7vh8zYsWP11FNPKTExUZJUrlw5JScn68knn9SIESO0YsUKZWRkaO/evc7YHjdunFq2bHnR1yYrK0tZWVnOx78/GwncipbOflsbli/W2Fkf57ui8OOB/Rr/cKIeGfuCyvzf2cHc3FyN7dNd/+j1iOK7JOrIoYMa93APhUfFqF6LNu7YBeCqKFy4sHx8/ZTx2UB3DwU3kKv6LuCJEydq5syZSk9PzzcvIyNDDRo0cJnWoEED7dy5U7m5uVdtDMaYi14+zs3N1dixY1WlShWFhIQoMDBQy5Yt0/79+yVJ3333nc6ePas6deo41ylUqJBiYvJfPqpSpYrzzw6HQ6GhoTp8+LCkc/tatWpVZ/xJ5/Y1Ly9PmZmZKlKkiJKSkhQfH6+2bdtq6tSpOnjwoHPZzZs3a/To0QoMDHR+9e7dWwcPHtSvv/6qjIwMlSlTxuVMa7169S75uowfP16FChVyfv1+H4FbTerij/XRv6Zq2L9nqWBwiMu8oz8d1uie9+nehx/X7c3+90vTqePHdPTwIcV3SZSnl5eKlw5XnaYt9PXG1Os9fODqM8bdI8AN5qqdAZSkhg0bKj4+XkOHDlVSUpLLvAuFmbnK/yCPHDmin376SWXLlr3g/EmTJmnKlCl68cUXVblyZQUEBGjgwIHKzs52Gc+fGae3t7fLY4fDoby8POfyF4vQ89NTUlL06KOPasmSJZozZ46effZZLV++XHXr1lVeXp5GjRqle+65J9/6vr6+FxzP5e6ZfPrpp/XPf/7T+TgzM5MIxE0t5+xZ5eXlKs/kKScnR9lZZ+TlXUDb167Wv8c8qxEpc1S8dLjLOqdPnlByr/vVKOFe3d25m8u8QkVCFBJWUsv/857u7txdRw8f0lefLVWLrknXca+Aq+/YsWPKyjqj2KYvKiA4yt3Dsd6R77/Ung0TLr/gNXZVA1CSJkyYoGrVqik6OtplelxcnL788kuXaWvXrlV0dLQ8PT0lnXvX7t85Gzh16lR5eHioffv2F5y/Zs0aJSQkqFu3c9/48/LytHPnTufl1/Lly8vb21sbN25UePi5HxwnTpzQzp071ahRoz89jri4OM2cOVOnT592ngVMTU2Vh4eHy+tSvXp1Va9eXU8//bTq1aun999/X3Xr1lWNGjWUmZmpqKgLH6hxcXHav3+/fvjhB+fl6XXr1l1yTD4+PvLx+d+7JQMDA//0/gA3oteHDdaq+R9IkjI2bdDLQx7VqJkfau70V3T6xHE906Wdc9mGbTuo76iJ2rhiifZlpuvH7/fq4zdfc85/b8u5e6MGT31Db40dpvcmjVMBPz81aNlOzTp2vb47BlwjAcFRCipW2d3DsN5vx7939xAkXYMArFy5srp27aqXX3b9ANVBgwapdu3aSk5OVufOnbVu3Tq98soreu21/30TjoyM1OrVq3XffffJx8dHRYsWvejznDx5UocOHdLZs2e1Z88evfvuu/r3v/+t8ePHXzScoqKi9NFHH2nt2rUKDg7W5MmTdejQIWcABgUFKTExUYMHD3beTzhixAh5eHj8pY+S6dq1q0aMGKHExESNHDlSP/30kwYMGKDu3burRIkS2rNnj6ZPn6527dqpZMmSyszM1I4dO9SjRw9J0vDhw9WmTRuFh4erY8eO8vDw0Pbt25WWlqYxY8aoWbNmiomJUY8ePTRp0iSdOHFCzzzzzJ8eH3ArGDDhRQ2Y8GK+6bfdfvF37d71j0666x+dLjo/qnI1jZu94GoMDwBuaNfkfwJJTk7Od5myRo0a+uCDDzR79mzddtttGj58uEaPHu1yqXj06NHau3evypcvr2LFil3yOYYPH66wsDBFRUWpe/fuOn78uD777DMNGTLkousMGzZMNWrUUHx8vBo3bqzQ0NB8ZwsnT56sevXqqU2bNmrWrJkaNGig2NhY+fr6/un99/f319KlS/XLL7+odu3auvfee9W0aVO98sorzvnffvutOnTooOjoaPXp00f9+/dX3759JUnx8fFauHChli9frtq1a6tu3bqaPHmyIiIiJEkeHh6aN2+esrKyVKdOHfXq1cvl8w8BAAAuxWGu9o14t5jTp0+rVKlSmjRpkh588EF3D+eqycjIUFxcnJ6YOl314nmHIwDcar77ZrsGd2ihd999V926dVOtexdyCfgGcHjXYn2z/GGlp6e7fALI9XbVLwHf7LZu3apvv/1WderU0fHjxzV69Ln/JiohIcHNIwMAALg6CMALeOGFF5SZmakCBQqoZs2aWrNmzSXvRwQAALiZEIB/UL16dW3evNndwwAAALhmrsmbQAAAAHDjIgABAAAsQwACAABYhgAEAACwDAEIAABgGQIQAADAMgQgAACAZQhAAAAAyxCAAAAAliEAAQAALEMAAgAAWIYABAAAsAwBCAAAYBkCEAAAwDIEIAAAgGUIQAAAAMsQgAAAAJYhAAEAACxD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8JLPcTkEIHCTatiwoeLj4zV06NB884wx+b6Jmr/wjtauXbtq/fr1GjlypHr06CEvL698y+Tl5WnUqFHatm2b8ystLU07d+6Ur6+vczlvb2/nn8+P6ULT8vLy8k271P78/pv/eb169XLeMJ+SkqLOnTvL39//gvtYrFgxBQcHXzK2zj/3xab/fky/36fz+3Chab/fz4u52A/A9evX67777lPLli21cOFCbd26Vc8884yys7Mvub0rGUevXr303XffqXv37kpLS1OtWrUue38irp2ePXtqxowZmjlzpnr27Jlv/vm/z0WLFrkck+np6S73AUr5j79L/fu4WJT9mWOyQIEC6t69u1JSUpSdna3333//gmM/Lzo6WpL+1DF5sWPkeh+TkyZN0pQpU/Tkk09q5cqV2rZtm+Lj46/JMZmSkqJ169apfv36mjNnjqKjo7V+/frLjv1iCEDgJjZhwgQtWLBAa9eudZkeFxenL7/80mXa2rVrFR0d7XIm6GKKFCmidu3a6YsvvrjoN+waNWooMzNTUVFR+b5+/1v3XxUbG3vBsV/o42n+qFWrVgoICNDrr7+uTz/99JI/bDw8PNS5c2e99957+uGHH/LNP336tHJychQXF6ecnBxt2LDBOe/IkSPasWPHnxrT5fzxG/j69etVsWLFCy6bmpqqiIgIPfPMM6pVq5YqVKjw924C/z8FChS44Jnh8PBwPfTQQ5o7d64GDRqkN954428/F65MixYtlJ2drezsbMXHx+ebHxcXJx8fH+3fvz/f8RgeHn7FzxsVFaUCBQq4HJNnz57Vpk2b/tS//169emnFihV67bXXdPbsWd1zzz0XXbZatWqKi4vTpEmTLhhD5z97Ly4uTtu2bdPp06ed81JTU+Xh4eGMyL/j98dkTk6ONm/efNFjcs2aNUpISFC3bt1UtWpVlStXzuUNYleiQIECknTBY7J69ep6+umntXbtWt122216//33r/h58v9aD+CmUblyZXXt2jXfmZlBgwapdu3aSk5OVufOnbVu3Tq98soreu211/70tmfMmKHXXnvtoh8pMnz4cLVp00bh4eHq2LGjPDw8tH37dqWlpWnMmDFXvE+DBw9Wp06dVKNGDTVt2lQLFizQ3LlztWLFisuu6+npqaSkJD399NOKiorKd3n1j8aNG6dVq1bp9ttv19ixY1WrVi15e3trzZo1Gj9+vL766itVqFBBCQkJ6t27t6ZNm6agoCA99dRTKlWqlBISEq54P89LTU3Vc889p/bt22v58uX6z3/+o0WLFl1w2aioKO3fv1+zZ89W7dq1tWjRIufltb8jMjJSq1ev1n333ScfHx8VLVpUAwcOVMuWLRUdHa2jR49q5cqVVyV4cWU8PT2dZ8Yu9EtcUFCQnnjiCT3++OPKy8vTHXfcoRMnTmjt2rUKDAxUYmLiFT1vQECAHn74Yec7Z8uUKaPnnntOv/76qx588MHLrh8bG6u6detqyJAh6tmzp/z8/C66rMPhUEpKipo1a6aGDRtq6NChqlixok6dOqUFCxZo2bJl+uKLL9S1a1eNGDFCiYmJGjlypH766ScNGDBA3bt3d95m8ne8+uqrqlChgmJjYzVlyhQdPXr0or9MRkVF6aOPPtLatWsVHBysyZMn69ChQ3/rWClevLj8/Py0ZMkSlS5dWr6+vvrll180ffp0tWvXTiVLllRmZqZ27NihHj16XPHzcAYQuMklJyfnu0xZo0YNffDBB5o9e7Zuu+02DR8+XKNHj/5LHxp7/uMVLiY+Pl4LFy7U8uXLVbt2bdWtW1eTJ09WRETEle6KpHP3DU2dOlXPP/+8KlWqpGnTpiklJcX5UQiX8+CDDyo7O/uSZ//OCw4O1vr169WtWzeNGTNG1atX15133qlZs2bp+eefV6FChSSdu/RSs2ZNtWnTRvXq1ZMxRosXL853GedKDBo0SJs3b1b16tWVnJysSZMmXfAMjyQlJCTo8ccfV//+/VWtWjWtXbtWw4YN+9tjGD16tPbu3avy5curWLFiks6dfejXr59iY2PVokULxcTE/KVfIHD1FSxYUAULFrzo/OTkZA0fPlzjx49XbGys4uPjtWDBAufHilypCRMmqEOHDurevbtq1KihXbt2aenSpQoODv5T6/+VY7JOnTratGmTypcvr969eys2Nlbt2rXTN9984/ywcn9/fy1dulS//PKLateurXvvvVdNmzbVK6+88nd202nChAmaOHGiqlatqjVr1ujjjz/Od8/lecOGDVONGjUUHx+vxo0bKzQ0VO3bt/9bz+/l5aWXXnpJ06ZNU8mSJZWQkCB/f399++236tChg6Kjo9WnTx/1799fffv2veLncZi/cmMQANzgUlNT1bhxYx04cOCqnA24liIjIzVw4MAb8r+JAq6WsWPHavbs2UpLS3P3UC5p7969Klu2rLZu3WrFf6fIJWAAt4SsrCx9//33GjZsmDp16nTDxx9wqzt16pQyMjL08ssv/6X/Cg3XB5eAAdwSZs2apZiYGB0/flzPPfecu4cDWK9///6644471KhRoz91+RfXF5eAAQAALMMZQAAAAMsQgAAAAJYhAAEAACxDAAIAAFiGAAQAALAMAQgAAGAZAhAAAMAyBCAAAIBlCEAAAADLEIAAAACWIQABAAAsQwACAABYhgAEAACwDAEIAABgmf8P9zs/mPoewwIAAAAASUVORK5CYII='>



| Memory Complaints   | Diagnosis   |
|------------------------|-------------|
| Memory Complaints      | 0.639821    |
| No Memory Complaints   | 0.278496    |


According to the second mosaic plots, we see that the majority of patients do not report any memory complaints. Among these patients, approximately 28% are diagnosed with Alzheimer's Disease. On the other hand, among those who report memory complaints, 64% are diagnosed with Alzheimer's Disease. **But how do we know if this is actually true?** In the next section, I will perform permutation testing to see if these differences are due to random chance.

## Hypothesis Testing

**Null hypothesis:** The differences are due to random chance. There isn't actually a relationship between diagnosis and memory complaints.

**Alternative hypothesis:** The differences are not due to random chance. People who report memory complaints are more likely to develop Alzheimer's Disease.

### Steps for Permutation Testing:

**1. Compute the Test Statistic:** I created an appropriate test statistic derived from the sample that quantifies the strength of association between memory complaints and Alzheimer's Disease diagnosis. In this case, I used the difference in proportions between the two groups (patients with memory complaints vs. those without)

**2. Create Shuffled Data:** I shuffled the "MemoryComplaints" column randomly and recomputed the test statistic for each shuffled dataset 1000x.

**3. Compute the p-value:** This determines the probability of observing a test statistic as extreme as the one computed from the actual data, assuming the null hypothesis is true.

I chose a significance level of 0.05. Here are the results:


```py
print(f"p_value: {p_value}")
```

p_value: 0.0

<iframe
  src="assets/html_hypothesis_testing.html"
  width="700"
  height="500"
  frameborder="0"
></iframe>

Our p-value of 0.0 suggests that the alternative hypothesis is true. Therefore, we will reject the null hypothesis. We conclude that there is enough evidence to suggest that the differences are not due to random chance and that those who report
memory complaints are indeed more likely to be diagnosed with Alzheimer's Disease.

## Framing a Prediction Problem

I will predict whether a patient has Alzheimer's Disease using four different models: Logistic Regression, 
Decision Tree Classifier, Random Forest Classifier, and Gradient Boost Classifier. I will use F1-score to calculate the 
models' accuracy since the data is severely imbalanced. I will also compare models' accuracy using recall.

The model should be trained only on features that are relevant to the prediction problem. I filtered out all variables that have little to no correlation with diagnosis. I used a correlation matrix to visualize the association between numerical variables and chi-squared test to find the best categorical variables.


<iframe
  src="assets/heatmap.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>


We see that "MMSE", "FunctionalAssessment", and "ADL" are the top 3 numerical features that are most associated with diagnosis.

I used a chi-squared test to determine the best categorical features:

```py
def is_correlated(x, y):
    cross_table = pd.crosstab(index = alz[x], columns = alz[y])
    chi_sq_result = chi2_contingency(cross_table,)
    p, c = chi_sq_result[1], "correlated" if chi_sq_result[1] < 0.05 else "not correlated"
    return (x, p, c)

chi_sq_results = []
for column in categorical_columns:
    result = is_correlated(column, "Diagnosis")
    chi_sq_results.append(result)
    
chi_sq_results.sort(key=lambda x: x[1])

print(chi_sq_results)

```

#### Top Categorical Features Based On Chi-Squared Test Results:

1. ('MemoryComplaints', 1.5266050985264054e-45, 'correlated')
2. ('BehavioralProblems', 4.731446795211873e-25, 'correlated')
3. ('Ethnicity', 0.09780307184026778, 'not correlated')
4. ('Hypertension', 0.11808887156379336, 'not correlated')
5. ('FamilyHistoryAlzheimers', 0.14069795394928386, 'not correlated')
6. ('Diabetes', 0.16224495200138433, 'not correlated')
7. ('CardiovascularDisease', 0.1628367346921118, 'not correlated')
8. ('EducationLevel', 0.21650771973324673, 'not correlated')
9. ('Disorientation', 0.27978377696750084, 'not correlated')
10. ('Gender', 0.35381831348465786, 'not correlated')
11. ('HeadInjury', 0.3603226855585838, 'not correlated')
12. ('PersonalityChanges', 0.37175710638032144, 'not correlated')
13. ('Confusion', 0.4045413830124688, 'not correlated')
14. ('DifficultyCompletingTasks', 0.7198556855473033, 'not correlated')
15. ('Depression', 0.8283335436917469, 'not correlated')
16. ('Smoking', 0.860493227376371, 'not correlated')
17. ('Forgetfulness', 1.0, 'not correlated')

"MemoryComplaints" and "BehavioralProblems" are most associated with diagnosis but for the sake of this project I used the top 7 categorical features along with the 3 numerical features we established previously.

## Final Model

### Data Preparation
- **Splitting Data**: The data is split into training and test sets using `train_test_split`.

- **Standardizing Data**: The features are standardized to have a mean of 0 and a standard deviation of 1 using `StandardScaler`.

### Model Training and Evaluation
A function `train_and_evaluate` is defined to:
- Train the classifier.
- Make predictions.
- Evaluate the model performance using metrics such as Test Score, Precision, Recall, and F1 Score.
- Plot the ROC curve to visualize the performance of the classifier.

### Model Comparisons
Four different classifiers are trained and evaluated:
- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting

#### Model Performance Metrics

<iframe
  src="assets/roc_curve_LogisticRegression(random_state=42).html"
  width="900"
  height="700"
  frameborder="0"
></iframe>


<iframe
  src="assets/roc_curve_DecisionTreeClassifier(random_state=42).html"
  width="900"
  height="700"
  frameborder="0"
></iframe>

<iframe
  src="assets/roc_curve_RandomForestClassifier(random_state=42).html"
  width="900"
  height="700"
  frameborder="0"
></iframe>

<iframe
  src="assets/roc_curve_GradientBoostingClassifier(random_state=42).html"
  width="900"
  height="700"
  frameborder="0"
></iframe>


|                          | Logistic Regression | Decision Tree Classifier | Random Forest Classifier | Gradient Boosting Classifier |
|:-------------------------|--------------------:|-------------------------:|-------------------------:|-----------------------------:|
| **Test score**           |              0.8253 |                  0.8996  |                  0.9349  |                      0.9498  |
| **Precision score**      |              0.7865 |                  0.8859  |                  0.9399  |                      0.9378  |
| **Recall score**         |              0.7143 |                  0.8316  |                  0.8776  |                      0.9235  |
| **F1 score**             |              0.7487 |                  0.8579  |                  0.9077  |                      0.9306  |





Based on our results, the Gradient Boosting Classifier is the most promising model. It has the highest ROC AUC at 0.94. This means that the model has a 94% chance of correctly distinguishing between patients with and without Alzheimer's Disease across various threshold levels. The ROC AUC score indicates strong overall discriminative power.
Further analysis shows that the true positive rate, also known as, recall score is 92%. This means that the model incorrectly identifies a person as negative 8% of the time. Optimizing a model's recall is especially important in the field of medicine since
false negatives are worse than false positives. 

#### Full Code
For the full code and more details, please refer to [Jupyter Notebook](https://github.com/kenogihara/alzheimers_project/blob/main/alzheimers_disease_project.ipynb).