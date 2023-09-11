# Development of digital voice biomarkers and associations with cognition, cerebrospinal biomarkers, and neural representation in early Alzheimer's disease

> https://doi.org/10.1002/dad2.12393

## Key features

- This experiment uses audio recordings with machine learning approach to assess cognitive status.
- **Simplified Process**: let patients describe certain pictures --> record their voices as audio files --> use ML to obtain Digital Voice Biomarkers --> Use Digital Voice Biomarkers to differentiate cognitively unimpaired and mild cognitive impaired patients

## How is the test conducted

### Device

An Apple recording device (iPod), a picture used to describe.

### Form

Let the patient to describe selected picture and record the audio including the conversation. 

### Duration

1 - 2 mins.

## Digital Voice Biomarkers

### What are Digital Voice Biomarkers

- Acoustic Scores
    - Derived using Acoustic Analysis.
- Lexical-Semantic Scores
    - Derived using NLP Analysis.

### Why should we use Digital Voice Biomarkers

- They have significant associations between the derived digital biomarkers and functional network connectivity of the brain.
- They can differ cognitive status.
- They can detect AD biomarker status.

## How to process the audio file

### 1\. Use openSMILE to derive acoustic features

#### Webpage

- https://audeering.github.io/opensmile/
- It is an open source program, okay for non-commercial research use but needs acknowledge.
- Commercial use should contact at [info@audeering.com](mailto:info@audeering.com)

#### Programming Language

- C/C++
- It can be used in our Swift project by using Objective-C wrapper for C++ source code.
- openSMILE also officially supports iOS platform.

### 2\. Use Correction Based Feature Selection (CFS) to derive Acoustic Scores and Lexical-Semantic Scores

#### Objective

To obtain features that provided the most information differentiating CU (Cognitively Unimpaired) versus MCI (Mild Cognitive Impairment). 

#### Methodology

Two ML approaches (Acoustic & NLP) were implemented because of the differences in acoustic data and nature of NLP. 

#### Acoustic Analysis

- Compare three feature selection approaches and choose the one with the highest accuracy.
- Use the selected approach to derive model-based digital **Acoustic Scores**.

#### NLP Analysis

- Use classification predication ML model with logistic regression, neural network, and ensemble model to perform perform NLP analysis.
- Find the approaches of best accuracy and use it to derive **Lexical-Semantic Scores**.

### 3\. Results

- The MCI group had significantly higher Acoustic Scores compared to the CU group.
-  In contrast, Lexical-Semantic Scores were lower in the MCI versus CU group.
- In the whole sample, there was no significant difference in Acoustic Scores between Aβ-positive (Aβ+) and negative (Aβ-).
    - However, in the MCI subgroup, Acoustic Scores were significantly higher in participants who were Aβ+ compared to those who were Aβ-.
    - Lexical-Semantic scores were significantly different between Aβ+ versus Aβ- participants in the full sample and MCI subgroup.

## Strengths

- Digital biomarkers significant map to functional connectivity of certain brain regions while also help detect cognitive impairment and predict Alzheimer's disease.
- It saves time from a few hours (a traditional neuropsychological battery for MCI categorization and longitudinal monitoring) to 6 - 8 minutes (voice recording).
- It warrants further development and validation. 

## Limitations

- ML model may overfit the data.
- Misclassification of MCI versus CU may happen especially with a 50% African American sample. 
- The existing cutoff score for MoCA (<=26) might be unreliable, and the number should be lower.
- Only 15-item Boston Naming Test were used in this experiment instead of the 60-item one, so the sensitivity to cognitive impairment should be lower. 
- Pictures used in the test may be dated or cultural dependent.
- Privacy issues for audio recording and analysis.

## Future directions

- Use a detailed scene available in the public domain that has actions, colors, and objects which captured the richness of connected speech.
- Future pictures should span multiple racial, ethic, and socioeconomic backgrounds.
- The sensitivity examination of digital biomarkers should consider sociocultural and demographic mediators.
