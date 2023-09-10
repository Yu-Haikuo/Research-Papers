> https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7929495/pdf/nihms-1671376.pdf

## Short Summary

### Objective

To Identify voice biomarkers that can predict dementia.

### Method

Recruit participants --> Record voice response --> Extract acoustic features using openSMILE toolkit --> Assess the association Cox proportional hazards models.

### Results

- All participants were all asymptomatic during the examination.
- **Patients who developed dementia later tended to have shorter segments than other normal people.**
- **14 acoustic features showed significant association with dementia.**
- The most important acoustic feature is `jitterDDP_sma_de`, which represents the **differential frame-to-frame Jitter**.
- A voice based linear classifier was built to predict incident dementia.

### Conclusion

Multiple acoustic and linguistic features are identified that are associated with incident dementia among asymptomatic participants, which could be used to build better prediction models for passive cognitive health monitoring.

## Why we needs to identify digital voice biomarkers

- The actual impairment in verbal fluency and lexico-semantic processing caused by dementia usually happens **a few years earlier** than the cognitive impairment.
- It is important to detect speech alterations early and find voice biomarkers in spoken language.
- The prior studies have many limitations:
    - They are **case-control studies** with small number of selected participants, which limit their application to general public.
    - The effect of acoustic features on incidental dementia were not characterized well.

## Methodology

### Participants

- Participants were from Framingham Heart Study (FHS), a community-based cohort with longitudinal collection of voice and other phenotype data in neuropsychological (NP) tests which happened periodically on all members.
- Participants have also been rigorously followed for incident neurologic outcomes.
- Dementia subtypes were not separated by the examination team.

### Audio Recordings

- Since 2005, all spoken interactions between the testers and participants in NP tests were recorded as audio recordings.

### Diarization

- It is a process of determining who is speaking (whether it is tester or participant).
- This process was achieved by using an algorithm that was trained on 92 samples that were manually transcribed to provide timestamp to indicate who is speaking for what.
- The algorithm is effective because the test procedure is quite similar and predictable (<ins>limitation*</ins>).

### Feature Extraction

- **openSMILE** software was used to extract acoustic features of each audio recording.
- Acoustic features were used to assess the severity of Parkinson’s disease.
- The current study restricts acoustic features to 48.
- Output data is in CSV format, each column represents an acoustic feature and each row represents a calculated score for a 20-millisecond period.
- The scores were then averaged across the entire voice recording, and normalized by rank-based inverse normalization.

### Statistical Analyses

- The association of each acoustic feature with incident dementia was assessed using **Cox proportional hazards models** with robust sandwich estimators.
- Participants who had developed dementia before the examination were excluded.
- A voice score representing weighted combination of all acoustic features that has significant association with dementia was defined by the author.
- Acoustic scores were combined together with age and sex to investigate the relation with incident dementia.

### Process Diagram

<img src=":/599e9b30555b42e4852eabbe78de3239" alt="Xnip2023-08-28_17-01-23.png" width="322" height="500" class="jop-noMdConv">

## Results

- The median of the voice recordings was 57 min. 49.1% of the recordings was marked as tester speech and 50.9% was marked as participant speech.
    
- Participants who developed dementia after the test **had more segments in their voice recordings** than those who did not. In addition, **each segment tended to be shorter**.
    
- 14 out of 48 acoustic features from OpenSMILE were significantly associated with incident dementia.
    
- The most significant acoustic feature was `jitterDDP_sma_de`, which represents the differential frame-to-frame Jitter (the -“Jitter of the Jitter”); where `jitter` is the variation in frequency from period to period.
    
    - > In the context of acoustic analysis, particularly related to speech, `jitter` refers to a measure of the variability or irregularity in the time between consecutive glottal closure instants (GCIs). GCIs mark the points in time where the vocal folds come together during speech production. Jitter quantifies the differences in the time intervals between these glottal closure events, essentially measuring the variation in pitch or frequency from one vocal fold vibration cycle to the next.
        
    - > `jitter` is often used as an acoustic measure to assess the stability and regularity of vocal fold vibrations during speech. It can provide insights into the quality of a person's voice and potential vocal pathologies. <ins>If `jitter` is high, it might indicate some irregularities in vocal fold vibration, which could be associated with voice disorders.</ins>
        
    - > `jitterDDP_sma_de`is a specific acoustic feature that quantifies the differential frame-to-frame jitter using the differential distribution phase analysis and a simple moving average. This analysis likely aims to capture finer details about the variations in vocal fold vibration irregularities, providing more insight into the characteristics of speech patterns.
        
- A weighted acoustic score was built from 14 acoustic features.
    
- Three models were built and the accuracy was increasing.
    
    - Model 1 - low accuracy: 0.773
        - age
        - sex
    - Model 2 - medium accuracy: 0.788
        - age
        - sex
        - segment length
        - number of segments
    - Model 3 - high accuracy: 0.812
        - age
        - sex
        - segment length
        - number of segments
        - weighted acoustic score from 14 acoustic features

## Discussion

### Findings

- Participants who were later diagnosed with dementia tended to have more pauses and hesitations in their speech.
- Differences in acoustic features might be a sign of converting to dementia.

### Strength

- In Experiment
    - A large volume of voice data was provided as a rich resource for the research.
    - Participants were from a well-operated community where all professional medical examinations were performed and recorded properly.
- In Application
    - The method has a potential to become an efficient tool to assess future dementia risk from voice recordings before cognitive symptoms appear.
    - Voice recording is low-cost and it is easy to broadcast this method to the public.
    - Other screening methods might be expansive/invasive, which limits their applications to the general population.

### Limitations

- In Experiment:
    - The quality of audio recordings could be affected by many factors.
    - The voice recording was performed for the entire session of the neuropsychological tests instead of each individual subtests.
    - Not all voice segments are equally important.
    - The author did not separate different subtypes of dementia nor build cognitive profiles for different brain functions.
    - Some participants might be too young for the examination to develop dementia at a later stage.
    - The author did not perform a comprehensive assessment of neuropsychiatric symptoms for participants, so the implication to speech ability was not clear.
    - The majority of participants were European and English-speaking.
- In Application:
    - The neuropsychological tests were performed in a controlled environment that only two people (tester and participant) were involved, which made it relatively easy to perform diarization.

### Future Work

- Extend the method application scenario to cover habitual environment where voice can be easily captured in addition to specialized environment.
- Make the whole process automated.
- Extend the language support to cover more races of people.
