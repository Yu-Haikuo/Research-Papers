# Cognitive Digital Biomarkers from Automated Transcription of Spoken Language

> http://dx.doi.org/10.14283/jpad.2022.66

## Abstract

### Background

Alzheimer's disease and other cognitive-related neurodegenerative disorders can be predicted at an early stage via usage of digital voice recording technologies.

### Objective

To determine whether cognitive status might be predicted from voice recordings of neuropsychological testing.

### Design

Compare acoustic and linguistic variables from **low quality automated transcriptions** of neuropsychological testing with **high quality manual transcriptions** to train a logistic regression classifier to predict cognitive status.

### Result

The use of voice-based digital biomarkers derived from automated processing methods, combined with standard patient screening, might constitute a scalable way to enable early detection of dementia.

## Introduction

- Dementia cannot be diagnosed by one single cognitive test. Instead, a combination of cognitive tests are required.
- Dementia is an insidious disease, and early detection & intervention could help improve the quality of life.
- Smartphones with voice recording functions could be used with voice biomarkers to detect dementia for general publics.

## Methodology

### Participants

- Participants were from Framingham Heart Study (FHS), a community-based cohort with longitudinal collection of voice and other phenotype data in neuropsychological (NP) tests which happened periodically on all members.
- The study analyzed a subset of digital voice recordings from 146 participants, all of whom had consensus-confirmed normal cognition, mild cognitive impairment, or dementia diagnoses.

### Demographic and Clinical Variables

- Standard demographic information like age, sex, marital status and occupation were collected.
- Clinical data were also collected through separate medical examinations.

### Neuropsychological Exams and Consensus Determination of Dementia Labels

- Testing included the Wechsler Memory Scale Logical Memory, Verbal Paired Associates, and the Wechsler Adult Intelligence Scale Digit Span tests (forward and backward).
- The Logical Memory test is a narrative recall task in which the proctor reads a story aloud and then asks the subject to recall the components of the story back to the examiner.
- Dementia determinations classified patients with severity on a scale of none (0) to severe (3).

### Audio Recordings of Neuropsychology Exams

- Audio recordings consisted a structured conversation between the participant and tester.
- All personally identifiable information was removed in the recordings.

### Acoustic Analysis

- Acoustic analysis, speech transcription, and language processing were used to automatically reduce voice segments from recordings into a set of candidate digital biomarkers.
- Speech-to-text tool: **IBM Watson API (automated) + manual transcriptions**.
- Diarization was manually performed to distinguish between speakers by a company.

### Acoustic Variable Extraction

- Tool: MIT's featurization algorithm and **openSMILE toolkit**.
- The following variables were computed and used:
    - MFCCs
    - fundamental frequency (F0)
    - voicing probability
    - **local jitter**
    - **difference of differences jitter**
    - local shimmer
    - harmonics to noise ratio (HNR)
    - power spectrum (audspec)
    - relative spectral transform (RASTA)
    - zero crossing rate
    - RMS

### Paralinguistic Variable Extraction (Automated Transcriptions via IBM Watson API)

- To featurize these data, we considered word use, speech time, word certainty, and Bristol-norm variables.
- Speech time variables included:
    - the total speaking time
    - mean and standard deviation of word and pause lengths (in seconds)
    - fraction of time spent pausing
    - total section time
    - fraction of that section the participant was speaking.

### Linguistic Variables Extraction (Manual Transcriptions)

- NLP techniques to extract information from grammar of the sentences to evaluate the complexity of the responses via two trained ML models.
- Linguistic variables were generated based on the whole interview, as opposite to the paralinguistic variables, which were generated based on different sections of the interviews as well as the whole sessions.
- Analyze the use of production rules:
    - used the Charniak-Johnson parser trained on the Wall Street Journal
    - computed the frequency of the top 50 most common production rules over all transcriptions
    - Bristol norm variables were computed using natural language toolkit (NLTK) Python module to improve lemmatization.
    - Several qualitative measures such as nonverbal breaks (laughs, crosstalk, etc.) were calculated.
    - Finally, additional measures of syntactic complexity using the L2 syntactic complexity analyzer were computed.

### Predictive Model Development

- Two ML classifiers were trained to predict cognitive status:
    - one used demographic, clinical, acoustic, and paralinguistic variables for those with **automated** transcriptions
    - the other one used demographic, clinical, acoustic, and linguistic variables for participants with **hand-transcribed** recordings

## Results

- Models based on paralinguistic variables derived from automated transcription performed better than those only based on simple acoustic variables.
- In addition, a high quality manual transcription could help improve NLP efficiency and achieve a better predictive accuracy.

## Discussion

### Strength

- Digital biomarkers can be measured in real time and are generally less expensive to compute:
    - automated transcription costs ~$1 per 15-minute, which is **~$4** per hour
    - manual transcription costs ~$2 per minute, which is **~$120** per hour

### Limitations

- A larger digital datasets of medicals and audio samples in more racially and culturally diverse populations would be preferred.
- Audio quality would result in more accurate diarization and transcriptions, and thus has impacts on the final results.

### Future Works

- Supplementing dataset with other health-related data sources such as heart rate is also recommended.
