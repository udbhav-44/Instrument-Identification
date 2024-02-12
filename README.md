# Instrument-Identification

***This project aims to build a basic CNN model to classify the instrument being played in a given audio file.***

## DataSet
- TinySOL contains 2913 audio clips as WAV files, sampled at 44.1 kHz, with a single channel (mono), at a bit depth of 16. 
- Every file name is of the format </br>
     ```FAMILY>/<INSTRUMENT>/ordinario/<INSTR>-ord-<PITCH>-<DYN>-<INSTANCE>-<MISC>.wav```
- The Dataset consists of Single audio notes from 14 different instruments.

    1. Bass Tuba            
    2. French Horn
    3. Trombone
    4. Trumpet in C
    5. Accordion
    6. Contrabass
    7. Violin
    8. Viola
    9. Violoncello
    10. Bassoon
    11. Clarinet in B-flat
    12. Flute
    13. Oboe
    14. Alto Saxophone
   
 ## Data Preprocessing
 1. Load the data using the `Librosa` library (which loads and decodes the audio as a tuple of a time series, represented as a one-dimensional NumPy floating point array, and its sampling rate. ) 
 2. Calculating the **bitlength** of each audio sample, to identify the minimum bitlength of any audio
 3. **Generating Synthetic Audio Samples** -  Randomly selecting a starting index for the audio waveform. and ensuring that the selected range is within the available bit lengths of the chosen file then extracting a portion of the audio waveform from the chosen file based on the randomly selected starting index. and similarily extracting the labels for the generated audio sample (Instruments).
 4. **LabelEncoding -** Using the Label encoding to change the categorical target into a numerical data,i.e, converting the names of the 14 instruments to a mapped integers (0-13), following this performing **one hot encoding.** to remove any unnecesaary bias.
 5. **Generating Mel-Frequency Cepstral Coefficients (MFCC) features**  - Using the customised hyperparameters.

## Data Augmentation - CutMix 
