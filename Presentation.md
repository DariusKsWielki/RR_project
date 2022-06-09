# Reproducible Research project - Menthal Health in Tech 

## Dataset used in our resarch 

The data we used can be found here https://www.kaggle.com/code/andradaolteanu/model-and-visualize-mental-health-in-tech/notebook?fbclid=IwAR1HAGSxsHbl5Z9WGW-NQ9zSNXM0wMM7rRzexQd3QoJ4FmeYct3QoJ4F. We worked on the 2016 OSMI Mental Health in Tech Survey. It had 1433 rows and 63 columns, lot's of missing data, lot's of not integrated data (gender for example was left an open question), lot's of countries but not consistent in number of respondents etc.


```python
import pandas as pd
survey_2016 = pd.read_csv('dane_RR.csv')
survey_2016
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Are you self-employed?</th>
      <th>How many employees does your company or organization have?</th>
      <th>Is your employer primarily a tech company/organization?</th>
      <th>Is your primary role within your company related to tech/IT?</th>
      <th>Does your employer provide mental health benefits as part of healthcare coverage?</th>
      <th>Do you know the options for mental health care available under your employer-provided coverage?</th>
      <th>Has your employer ever formally discussed mental health (for example, as part of a wellness campaign or other official communication)?</th>
      <th>Does your employer offer resources to learn more about mental health concerns and options for seeking help?</th>
      <th>Is your anonymity protected if you choose to take advantage of mental health or substance abuse treatment resources provided by your employer?</th>
      <th>If a mental health issue prompted you to request a medical leave from work, asking for that leave would be:</th>
      <th>...</th>
      <th>If you have a mental health issue, do you feel that it interferes with your work when being treated effectively?</th>
      <th>If you have a mental health issue, do you feel that it interferes with your work when NOT being treated effectively?</th>
      <th>What is your age?</th>
      <th>What is your gender?</th>
      <th>What country do you live in?</th>
      <th>What US state or territory do you live in?</th>
      <th>What country do you work in?</th>
      <th>What US state or territory do you work in?</th>
      <th>Which of the following best describes your work position?</th>
      <th>Do you work remotely?</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>0</td>
      <td>26-100</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>Not eligible for coverage / N/A</td>
      <td>NaN</td>
      <td>No</td>
      <td>No</td>
      <td>I don't know</td>
      <td>Very easy</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>39</td>
      <td>Male</td>
      <td>United Kingdom</td>
      <td>NaN</td>
      <td>United Kingdom</td>
      <td>NaN</td>
      <td>Back-end Developer</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>1</td>
      <td>0</td>
      <td>6-25</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>No</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Somewhat easy</td>
      <td>...</td>
      <td>Rarely</td>
      <td>Sometimes</td>
      <td>29</td>
      <td>male</td>
      <td>United States of America</td>
      <td>Illinois</td>
      <td>United States of America</td>
      <td>Illinois</td>
      <td>Back-end Developer|Front-end Developer</td>
      <td>Never</td>
    </tr>
    <tr>
      <td>2</td>
      <td>0</td>
      <td>6-25</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>No</td>
      <td>NaN</td>
      <td>No</td>
      <td>No</td>
      <td>I don't know</td>
      <td>Neither easy nor difficult</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>38</td>
      <td>Male</td>
      <td>United Kingdom</td>
      <td>NaN</td>
      <td>United Kingdom</td>
      <td>NaN</td>
      <td>Back-end Developer</td>
      <td>Always</td>
    </tr>
    <tr>
      <td>3</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Sometimes</td>
      <td>Sometimes</td>
      <td>43</td>
      <td>male</td>
      <td>United Kingdom</td>
      <td>NaN</td>
      <td>United Kingdom</td>
      <td>NaN</td>
      <td>Supervisor/Team Lead</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>4</td>
      <td>0</td>
      <td>6-25</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>Neither easy nor difficult</td>
      <td>...</td>
      <td>Sometimes</td>
      <td>Sometimes</td>
      <td>43</td>
      <td>Female</td>
      <td>United States of America</td>
      <td>Illinois</td>
      <td>United States of America</td>
      <td>Illinois</td>
      <td>Executive Leadership|Supervisor/Team Lead|Dev ...</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <td>1428</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>34</td>
      <td>Female</td>
      <td>United States of America</td>
      <td>New York</td>
      <td>United States of America</td>
      <td>New York</td>
      <td>Other</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>1429</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Sometimes</td>
      <td>Often</td>
      <td>56</td>
      <td>MALE</td>
      <td>United States of America</td>
      <td>California</td>
      <td>Afghanistan</td>
      <td>NaN</td>
      <td>Support</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>1430</td>
      <td>0</td>
      <td>100-500</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>I don't know</td>
      <td>Somewhat difficult</td>
      <td>...</td>
      <td>Rarely</td>
      <td>Sometimes</td>
      <td>52</td>
      <td>Male</td>
      <td>United States of America</td>
      <td>Georgia</td>
      <td>United States of America</td>
      <td>Georgia</td>
      <td>Back-end Developer</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>1431</td>
      <td>0</td>
      <td>100-500</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>I don't know</td>
      <td>I am not sure</td>
      <td>No</td>
      <td>Yes</td>
      <td>I don't know</td>
      <td>Somewhat difficult</td>
      <td>...</td>
      <td>Sometimes</td>
      <td>Often</td>
      <td>30</td>
      <td>Female</td>
      <td>United States of America</td>
      <td>Nebraska</td>
      <td>United States of America</td>
      <td>Nebraska</td>
      <td>DevOps/SysAdmin</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>1432</td>
      <td>0</td>
      <td>100-500</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>I don't know</td>
      <td>Very difficult</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Often</td>
      <td>25</td>
      <td>non-binary</td>
      <td>Canada</td>
      <td>NaN</td>
      <td>Canada</td>
      <td>NaN</td>
      <td>Other</td>
      <td>Sometimes</td>
    </tr>
  </tbody>
</table>
<p>1433 rows × 63 columns</p>
</div>



## New observations

Using our network of contacts, we asked the same questions to 50 people working in IT. We then added these observations to the existing dataset and watched the results change.


```python
new_observations = pd.read_excel('new_observations.xlsx')
new_observations
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Are you self-employed?</th>
      <th>How many employees does your company or organization have?</th>
      <th>Is your employer primarily a tech company/organization?</th>
      <th>Is your primary role within your company related to tech/IT?</th>
      <th>Does your employer provide mental health benefits as part of healthcare coverage?</th>
      <th>Do you know the options for mental health care available under your employer-provided coverage?</th>
      <th>Has your employer ever formally discussed mental health (for example, as part of a wellness campaign or other official communication)?</th>
      <th>Does your employer offer resources to learn more about mental health concerns and options for seeking help?</th>
      <th>Is your anonymity protected if you choose to take advantage of mental health or substance abuse treatment resources provided by your employer?</th>
      <th>If a mental health issue prompted you to request a medical leave from work, asking for that leave would be:</th>
      <th>...</th>
      <th>If you have a mental health issue, do you feel that it interferes with your work when being treated effectively?</th>
      <th>If you have a mental health issue, do you feel that it interferes with your work when NOT being treated effectively?</th>
      <th>What is your age?</th>
      <th>What is your gender?</th>
      <th>What country do you live in?</th>
      <th>What US state or territory do you live in?</th>
      <th>What country do you work in?</th>
      <th>What US state or territory do you work in?</th>
      <th>Which of the following best describes your work position?</th>
      <th>Do you work remotely?</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>0</td>
      <td>500-1000</td>
      <td>0</td>
      <td>1</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>I don't know</td>
      <td>I don't know</td>
      <td>...</td>
      <td>Sometimes</td>
      <td>Sometimes</td>
      <td>27</td>
      <td>Female</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>DevOps</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>1</td>
      <td>0</td>
      <td>More than 1000</td>
      <td>1</td>
      <td>0</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>I don't know</td>
      <td>Somewhat easy</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>24</td>
      <td>Female</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Dev</td>
      <td>Never</td>
    </tr>
    <tr>
      <td>2</td>
      <td>0</td>
      <td>500-1000</td>
      <td>1</td>
      <td>0</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>I don't know</td>
      <td>Very easy</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>35</td>
      <td>Female</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>DevOps</td>
      <td>Always</td>
    </tr>
    <tr>
      <td>3</td>
      <td>1</td>
      <td>26-100</td>
      <td>1</td>
      <td>1</td>
      <td>Yes</td>
      <td>I am not sure</td>
      <td>No</td>
      <td>No</td>
      <td>I don't know</td>
      <td>Somewhat easy</td>
      <td>...</td>
      <td>Rarely</td>
      <td>Rarely</td>
      <td>38</td>
      <td>Female</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Dev</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>4</td>
      <td>1</td>
      <td>100-500</td>
      <td>0</td>
      <td>1</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>I don't know</td>
      <td>Yes</td>
      <td>Somewhat difficult</td>
      <td>...</td>
      <td>Sometimes</td>
      <td>Often</td>
      <td>36</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Front-end</td>
      <td>Always</td>
    </tr>
    <tr>
      <td>5</td>
      <td>1</td>
      <td>26-100</td>
      <td>0</td>
      <td>1</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>I don't know</td>
      <td>Very easy</td>
      <td>...</td>
      <td>Rarely</td>
      <td>Rarely</td>
      <td>34</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Back-end</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>6</td>
      <td>1</td>
      <td>500-1000</td>
      <td>0</td>
      <td>0</td>
      <td>Yes</td>
      <td>I am not sure</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>I don't know</td>
      <td>Very easy</td>
      <td>...</td>
      <td>Rarely</td>
      <td>Sometimes</td>
      <td>35</td>
      <td>Female</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Front-end</td>
      <td>Never</td>
    </tr>
    <tr>
      <td>7</td>
      <td>1</td>
      <td>500-1000</td>
      <td>0</td>
      <td>0</td>
      <td>I don't know</td>
      <td>No</td>
      <td>No</td>
      <td>I don't know</td>
      <td>Yes</td>
      <td>Somewhat difficult</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>25</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Dev</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>8</td>
      <td>0</td>
      <td>More than 1000</td>
      <td>0</td>
      <td>1</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>I don't know</td>
      <td>...</td>
      <td>Sometimes</td>
      <td>Often</td>
      <td>32</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Back-end</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>9</td>
      <td>1</td>
      <td>26-100</td>
      <td>0</td>
      <td>1</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>I don't know</td>
      <td>...</td>
      <td>Rarely</td>
      <td>Sometimes</td>
      <td>32</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Back-end</td>
      <td>Always</td>
    </tr>
    <tr>
      <td>10</td>
      <td>0</td>
      <td>More than 1000</td>
      <td>1</td>
      <td>0</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>I don't know</td>
      <td>Somewhat easy</td>
      <td>...</td>
      <td>Rarely</td>
      <td>Sometimes</td>
      <td>37</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Front-end</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>11</td>
      <td>0</td>
      <td>More than 1000</td>
      <td>0</td>
      <td>0</td>
      <td>I don't know</td>
      <td>No</td>
      <td>No</td>
      <td>I don't know</td>
      <td>Yes</td>
      <td>Somewhat difficult</td>
      <td>...</td>
      <td>Never</td>
      <td>Sometimes</td>
      <td>28</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Back-end</td>
      <td>Always</td>
    </tr>
    <tr>
      <td>12</td>
      <td>0</td>
      <td>More than 1000</td>
      <td>1</td>
      <td>0</td>
      <td>No</td>
      <td>I am not sure</td>
      <td>No</td>
      <td>No</td>
      <td>Yes</td>
      <td>I don't know</td>
      <td>...</td>
      <td>Never</td>
      <td>Sometimes</td>
      <td>34</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Back-end</td>
      <td>Never</td>
    </tr>
    <tr>
      <td>13</td>
      <td>0</td>
      <td>100-500</td>
      <td>1</td>
      <td>0</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>I don't know</td>
      <td>Neither easy nor difficult</td>
      <td>...</td>
      <td>Sometimes</td>
      <td>Sometimes</td>
      <td>40</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Back-end</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>14</td>
      <td>0</td>
      <td>26-100</td>
      <td>1</td>
      <td>0</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Neither easy nor difficult</td>
      <td>...</td>
      <td>Rarely</td>
      <td>Often</td>
      <td>45</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Dev</td>
      <td>Never</td>
    </tr>
    <tr>
      <td>15</td>
      <td>1</td>
      <td>26-100</td>
      <td>0</td>
      <td>0</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>I don't know</td>
      <td>No</td>
      <td>Yes</td>
      <td>Neither easy nor difficult</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>31</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Back-end</td>
      <td>Never</td>
    </tr>
    <tr>
      <td>16</td>
      <td>0</td>
      <td>100-500</td>
      <td>1</td>
      <td>1</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>Yes</td>
      <td>Neither easy nor difficult</td>
      <td>...</td>
      <td>Rarely</td>
      <td>Often</td>
      <td>30</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>DevOps</td>
      <td>Always</td>
    </tr>
    <tr>
      <td>17</td>
      <td>1</td>
      <td>More than 1000</td>
      <td>0</td>
      <td>0</td>
      <td>Yes</td>
      <td>I am not sure</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Very difficult</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>47</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Dev</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>18</td>
      <td>0</td>
      <td>500-1000</td>
      <td>0</td>
      <td>1</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>Yes</td>
      <td>Very difficult</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>48</td>
      <td>Female</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Front-end</td>
      <td>Never</td>
    </tr>
    <tr>
      <td>19</td>
      <td>0</td>
      <td>100-500</td>
      <td>1</td>
      <td>0</td>
      <td>No</td>
      <td>I am not sure</td>
      <td>No</td>
      <td>No</td>
      <td>I don't know</td>
      <td>Very difficult</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Often</td>
      <td>44</td>
      <td>Female</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Dev</td>
      <td>Always</td>
    </tr>
    <tr>
      <td>20</td>
      <td>0</td>
      <td>500-1000</td>
      <td>1</td>
      <td>1</td>
      <td>Yes</td>
      <td>I am not sure</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>I don't know</td>
      <td>...</td>
      <td>Sometimes</td>
      <td>Sometimes</td>
      <td>29</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Front-end</td>
      <td>Always</td>
    </tr>
    <tr>
      <td>21</td>
      <td>0</td>
      <td>100-500</td>
      <td>1</td>
      <td>1</td>
      <td>No</td>
      <td>I am not sure</td>
      <td>No</td>
      <td>I don't know</td>
      <td>Yes</td>
      <td>I don't know</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>52</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Dev</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>22</td>
      <td>1</td>
      <td>More than 1000</td>
      <td>1</td>
      <td>0</td>
      <td>No</td>
      <td>I am not sure</td>
      <td>No</td>
      <td>No</td>
      <td>I don't know</td>
      <td>Somewhat difficult</td>
      <td>...</td>
      <td>Sometimes</td>
      <td>Sometimes</td>
      <td>34</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Front-end</td>
      <td>Never</td>
    </tr>
    <tr>
      <td>23</td>
      <td>1</td>
      <td>26-100</td>
      <td>1</td>
      <td>1</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>I don't know</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Somewhat easy</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>34</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>DevOps</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>24</td>
      <td>0</td>
      <td>100-500</td>
      <td>0</td>
      <td>1</td>
      <td>I don't know</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Somewhat difficult</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>27</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Front-end</td>
      <td>Never</td>
    </tr>
    <tr>
      <td>25</td>
      <td>0</td>
      <td>500-1000</td>
      <td>0</td>
      <td>1</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>I don't know</td>
      <td>I don't know</td>
      <td>Very difficult</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Sometimes</td>
      <td>30</td>
      <td>Female</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Back-end</td>
      <td>Always</td>
    </tr>
    <tr>
      <td>26</td>
      <td>1</td>
      <td>26-100</td>
      <td>1</td>
      <td>1</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>Yes</td>
      <td>I don't know</td>
      <td>...</td>
      <td>Sometimes</td>
      <td>Sometimes</td>
      <td>40</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Back-end</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>27</td>
      <td>0</td>
      <td>100-500</td>
      <td>0</td>
      <td>0</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>I don't know</td>
      <td>I don't know</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Sometimes</td>
      <td>26</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Dev</td>
      <td>Always</td>
    </tr>
    <tr>
      <td>28</td>
      <td>1</td>
      <td>500-1000</td>
      <td>0</td>
      <td>0</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>I don't know</td>
      <td>...</td>
      <td>Sometimes</td>
      <td>Sometimes</td>
      <td>36</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>DevOps</td>
      <td>Always</td>
    </tr>
    <tr>
      <td>29</td>
      <td>1</td>
      <td>26-100</td>
      <td>0</td>
      <td>1</td>
      <td>I don't know</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Somewhat easy</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Often</td>
      <td>35</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>DevOps</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>30</td>
      <td>1</td>
      <td>100-500</td>
      <td>0</td>
      <td>0</td>
      <td>No</td>
      <td>No</td>
      <td>I don't know</td>
      <td>I don't know</td>
      <td>Yes</td>
      <td>Neither easy nor difficult</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>43</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Front-end</td>
      <td>Never</td>
    </tr>
    <tr>
      <td>31</td>
      <td>1</td>
      <td>500-1000</td>
      <td>1</td>
      <td>0</td>
      <td>I don't know</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Somewhat easy</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Often</td>
      <td>36</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Back-end</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>32</td>
      <td>0</td>
      <td>26-100</td>
      <td>1</td>
      <td>1</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>Yes</td>
      <td>Somewhat easy</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>32</td>
      <td>Nonbinary</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Dev</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>33</td>
      <td>0</td>
      <td>100-500</td>
      <td>1</td>
      <td>0</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>Yes</td>
      <td>Very easy</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>36</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>DevOps</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>34</td>
      <td>1</td>
      <td>26-100</td>
      <td>1</td>
      <td>1</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>I don't know</td>
      <td>Very easy</td>
      <td>...</td>
      <td>Sometimes</td>
      <td>Often</td>
      <td>38</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Back-end</td>
      <td>Always</td>
    </tr>
    <tr>
      <td>35</td>
      <td>0</td>
      <td>100-500</td>
      <td>1</td>
      <td>0</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>I don't know</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Sometimes</td>
      <td>35</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Front-end</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>36</td>
      <td>1</td>
      <td>More than 1000</td>
      <td>1</td>
      <td>1</td>
      <td>Yes</td>
      <td>I am not sure</td>
      <td>Yes</td>
      <td>I don't know</td>
      <td>Yes</td>
      <td>Somewhat easy</td>
      <td>...</td>
      <td>Rarely</td>
      <td>Sometimes</td>
      <td>35</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Front-end</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>37</td>
      <td>0</td>
      <td>500-1000</td>
      <td>0</td>
      <td>0</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Somewhat easy</td>
      <td>...</td>
      <td>Often</td>
      <td>Often</td>
      <td>45</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Back-end</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>38</td>
      <td>0</td>
      <td>500-1000</td>
      <td>1</td>
      <td>0</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>I don't know</td>
      <td>Somewhat difficult</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>47</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Dev</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>39</td>
      <td>0</td>
      <td>100-500</td>
      <td>1</td>
      <td>0</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Neither easy nor difficult</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>27</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Front-end</td>
      <td>Always</td>
    </tr>
    <tr>
      <td>40</td>
      <td>0</td>
      <td>More than 1000</td>
      <td>0</td>
      <td>1</td>
      <td>I don't know</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>I don't know</td>
      <td>Neither easy nor difficult</td>
      <td>...</td>
      <td>Sometimes</td>
      <td>Often</td>
      <td>26</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>DevOps</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>41</td>
      <td>0</td>
      <td>100-500</td>
      <td>0</td>
      <td>1</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>I don't know</td>
      <td>Yes</td>
      <td>Somewhat easy</td>
      <td>...</td>
      <td>Rarely</td>
      <td>Rarely</td>
      <td>51</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Back-end</td>
      <td>Never</td>
    </tr>
    <tr>
      <td>42</td>
      <td>0</td>
      <td>100-500</td>
      <td>1</td>
      <td>1</td>
      <td>No</td>
      <td>I am not sure</td>
      <td>I don't know</td>
      <td>No</td>
      <td>I don't know</td>
      <td>Neither easy nor difficult</td>
      <td>...</td>
      <td>Often</td>
      <td>Rarely</td>
      <td>25</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Dev</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>43</td>
      <td>0</td>
      <td>26-100</td>
      <td>1</td>
      <td>0</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>I don't know</td>
      <td>Neither easy nor difficult</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>41</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>DevOps</td>
      <td>Always</td>
    </tr>
    <tr>
      <td>44</td>
      <td>0</td>
      <td>26-100</td>
      <td>1</td>
      <td>1</td>
      <td>I don't know</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>Yes</td>
      <td>Somewhat difficult</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>34</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Front-end</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>45</td>
      <td>1</td>
      <td>100-500</td>
      <td>0</td>
      <td>0</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Somewhat difficult</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>43</td>
      <td>Female</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Back-end</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>46</td>
      <td>1</td>
      <td>26-100</td>
      <td>0</td>
      <td>0</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>I don't know</td>
      <td>I don't know</td>
      <td>Neither easy nor difficult</td>
      <td>...</td>
      <td>Rarely</td>
      <td>Often</td>
      <td>33</td>
      <td>Male</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Dev</td>
      <td>Always</td>
    </tr>
    <tr>
      <td>47</td>
      <td>1</td>
      <td>More than 1000</td>
      <td>0</td>
      <td>1</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>I don't know</td>
      <td>Somewhat difficult</td>
      <td>...</td>
      <td>Not applicable to me</td>
      <td>Not applicable to me</td>
      <td>37</td>
      <td>Female</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Back-end</td>
      <td>Sometimes</td>
    </tr>
    <tr>
      <td>48</td>
      <td>1</td>
      <td>100-500</td>
      <td>1</td>
      <td>1</td>
      <td>I don't know</td>
      <td>No</td>
      <td>I don't know</td>
      <td>No</td>
      <td>I don't know</td>
      <td>Very easy</td>
      <td>...</td>
      <td>Rarely</td>
      <td>Often</td>
      <td>27</td>
      <td>Female</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>Poland</td>
      <td>NaN</td>
      <td>DevOps</td>
      <td>Sometimes</td>
    </tr>
  </tbody>
</table>
<p>49 rows × 63 columns</p>
</div>



## Data Cleaning 

##### Since many questions were open, it was necessary to clean the data. Therefore, the following changes were made:

* rename columns
* sex columns & company size recoded
* removed outliers from age
* missing value listwise deletion (for variables where missing observations were more than half) and simple imputation
* column encoding
* country filtering (remained only with the ones with more than 30 responses)
* create tech column with flag 1/0

## Data Analyst 

Part of the data analysis was divided into three stages. First, the analysis was repeated on the original data. Then the same analysis was carried out on the new data to see what distributions of variables we are dealing with. The final part was to repeat the analysis on the combined original data and our observations to see if the new data significantly changed the distributions of the variables. The results are shown below.

#### Missing data analyst 

#### Orginal data

![output_6_0.png](attachment:output_6_0.png)

#### New observations 

![output_6_0.png](attachment:output_6_0.png)

#### Full data

![output_8_0.png](attachment:output_8_0.png)

### Number of observations by country and company size 

#### Orginal data

![output_11_0.png](attachment:output_11_0.png)

#### Full data 

![output_13_0.png](attachment:output_13_0.png)

In original data, we had only 4 participant from Poland. Now with added new observations, it already started to show up on results as for Poland, we already have more than 30 results.

#### Mental Tech discorder in Tech (in the present)

##### Orginal data

![output_13_1.png](attachment:output_13_1.png)

#### New observations 

![output_12_1.png](attachment:output_12_1.png)

#### Full data

![output_16_1.png](attachment:output_16_1.png)

It seems that majority number of males among participants is also the same for Poland as well. But because of number of new observations compared to original data is too small, it does't affect to result much, but on average 0.4% more for each.

#### Mental Health Disorder in Tech (in the past)

##### Orginal data

![output_14_1.png](attachment:output_14_1.png)

##### New observations

![output_13_1.png](attachment:output_13_1.png)

##### Full data 

![output_18_1.png](attachment:output_18_1.png)

#### Are the comapnies take seoriusly menthal health?

##### Orginal data

![output_15_0.png](attachment:output_15_0.png)

##### New observations

![output_14_0.png](attachment:output_14_0.png)

##### Full data

![output_19_0.png](attachment:output_19_0.png)

Actually the same follows for these as we can notice slight changes on results either more or less.

### Discussing mental health at work

##### Orginal data

![output_16_0.png](attachment:output_16_0.png)

##### New observations 

![output_15_0.png](attachment:output_15_0.png)

##### Full data 

![output_21_0.png](attachment:output_21_0.png)

#### Is MH had bad consequences on career?

##### Orginal data

![output_17_0.png](attachment:output_17_0.png)

##### New observations

![output_16_0.png](attachment:output_16_0.png)

##### Full data

![output_22_0.png](attachment:output_22_0.png)

##### Willingness to share with frinds or family problem w Mental Health

##### Orginal data 

![output_18_0.png](attachment:output_18_0.png)

##### New observations

![output_17_0.png](attachment:output_17_0.png)

##### Full data 

![output_23_0.png](attachment:output_23_0.png)

## Modeling methal health 

#### Ten machine learning models were used to model the mh_disorder_current variable:

* Naive Bayes
* Stochastic Gradient Descent
* KNN
* Decission trees
* Random Forest
* Support Vector Machine
* Logistic Regression
* Neural Nets
* Cross Gradient Booster 
* Cross Gradient Booster (Random Forest)

#### Two best models that on orginal dataset:

![Best%20models%20orginal%20data.png](attachment:Best%20models%20orginal%20data.png)

#### Models after hyperparamters tuning: 

##### Random Forest

![RF%20greedy%20search.png](attachment:RF%20greedy%20search.png)

##### SVC

![SVC%20greedy%20search.png](attachment:SVC%20greedy%20search.png)

##### Best model after removing non-significant variables

![feature%20importance%20Orginal%20dataset.png](attachment:feature%20importance%20Orginal%20dataset.png)

##### Two best models on new dataset:

![XGB%20RF%20new%20dataset.png](attachment:XGB%20RF%20new%20dataset.png)

![random%20forest%20new%20dataset.png](attachment:random%20forest%20new%20dataset.png)

#### Models after hyperparamters tuning: 

##### XGBRFClassifier

![XGB%20RF%20greedy%20search%20new%20dataset.png](attachment:XGB%20RF%20greedy%20search%20new%20dataset.png)

#####  Random forest

![RF%20greedy%20search%20new%20dataset.png](attachment:RF%20greedy%20search%20new%20dataset.png)

##### Best model after removing non- significat variables

![Feature%20importance%20new%20dataset.png](attachment:Feature%20importance%20new%20dataset.png)

## Conclusions 

 * The best model for the original data turned out to be the regular Random Forest with a score of 0.75 followed by the SVM with a score of 0.74194. This result was different from that obtained in the original work.
 * By greedy search on the model's hyperparameters it was possible to improve the SVM result to the level of 0.747. It was, however, not enough to beat Random Forest score.
 * The results changed with the addition of observations. It is noticeable that most of the models obtained worse results.
 * This time the best was XGBRFClassifier with an accuracy score of 0.749, and the second was the regular Random Forest with a score of 0.73902. Tuning on hyperparameters failed to improve this result.
 * In both cases, the same variables turned out to be the most important and the limitation of the variables brought about an improvement in the results.
