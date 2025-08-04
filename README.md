# Kannada Automatic Speech Recognition System

[![Kaldi](https://img.shields.io/badge/Kaldi-ASR-blue.svg)](https://kaldi-asr.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

An automatic speech recognition system for the Kannada language using acoustic-phonetic modeling with Hidden Markov Models and neural networks.

## Overview

This project implements a complete ASR pipeline for Kannada speech recognition using the Kaldi toolkit. The system converts spoken Kannada utterances to text using MFCC feature extraction, HMM-based acoustic modeling, and n-gram language modeling. Both monophone and triphone acoustic models are implemented and compared.

## Technical Architecture

### Feature Extraction
- **MFCC (Mel-Frequency Cepstral Coefficients)** extraction with 25ms window size and 10ms frame shift
- 13-dimensional feature vectors with delta and delta-delta coefficients
- Audio preprocessing: downsampling from 48kHz to 16kHz, 8-bit quantization

### Acoustic Models
- **Monophone Model**: Context-independent phone modeling
- **Triphone Model**: Context-dependent modeling considering previous and next phonemes
- Hidden Markov Model (HMM) parameter estimation using Gaussian Mixture Models

### Language Model
- N-gram statistical language model for phoneme sequence prediction
- Dictionary-based phonetic transcription following ILSL v3.1 guidelines
- Automated phonetic labeling leveraging Kannada's phonetic script properties

### Phoneme Set
- 50 non-silence phones representing Kannada phonology
- 12 vowels, 2 diphthongs, 2 yogavahakas, 25 vargiya vyanjana, 11 avargiya vyanjana
- ILSL-compliant phonetic representation

## Dataset

**Source**: Google Research Datasets (CC BY-SA 4.0)
- 4,400 high-quality transcribed sentences
- Balanced male and female speaker distribution
- Training set: 4,003 sentences
- Test set: 200 sentences
- Vocabulary: 10,451 unique words

## Performance Results

| Model | Word Error Rate (WER) | Sentence Error Rate (SER) |
|-------|----------------------|---------------------------|
| Monophone | 28.58% | 72.0% |
| Triphone | 15.73% | 55.5% |

The triphone model demonstrates superior performance due to enhanced context-dependent phoneme prediction capabilities.

## Implementation

### Requirements
- Kaldi ASR Toolkit
- Audio processing capabilities for format conversion and feature extraction

### Setup
```bash
git clone https://github.com/Adithya-Jayan/nnet2-simple.git
cd nnet2-simple
```

### Training Workflow
The system follows standard Kaldi ASR training procedures:
1. Audio feature extraction using MFCC coefficients
2. Monophone model training with context-independent phonemes
3. Triphone model training incorporating phonetic context
4. Language model integration for improved recognition accuracy
5. Decoding and performance evaluation on test data

## System Architecture

```
Audio Input → MFCC Extraction → Acoustic Model (HMM) → Language Model → Text Output
                                      ↓
                              Monophone/Triphone
                              Context Modeling
```

The system follows the fundamental equation of statistical speech processing:
```
W* = argmax P(X|W)P(W)
```
where W* is the optimal word sequence, P(X|W) is the acoustic model probability, and P(W) is the language model probability.

## Future Enhancements

- Deep neural network acoustic models
- Recurrent neural network language models
- Dialect-specific model adaptation
- Real-time recognition capabilities
- Integration with larger vocabulary datasets

## Academic Context

**Institution**: National Institute of Technology Karnataka, Surathkal  
**Department**: Electronics and Communication Engineering  
**Authors**: Mahesh Kumar T N, Adithya Jayan, Shreenidhi Bhat, Anvith M  
**Supervisor**: Prof. A V Narasimhadhan  

**Publication**: [Monophone and Triphone Acoustic Phonetic Model for Kannada Speech Recognition System | IEEE Conference Publication | IEEE Xplore](https://ieeexplore.ieee.org/document/9754636)  

## References

1. Kaldi Speech Recognition Toolkit. "The Kaldi Speech Recognition Toolkit." 2011.
2. Samudravijaya, K. "Indian Language Speech Label (ILSL): A De Facto National Standard." 2021.
3. He, F., et al. "Open-source Multi-speaker Speech Corpora for Building Gujarati, Kannada, Malayalam, Marathi, Tamil and Telugu Speech Synthesis Systems." LREC 2020.

## Acknowledgments

Special thanks to Sathvik Bhat and Thilak Shetty for their contributions to the project development.

## License

This project is licensed under the MIT License.

## Contact

**Adithya Jayan** - [GitHub Profile](https://github.com/Adithya-Jayan)  
**Project Repository** - [https://github.com/Adithya-Jayan/nnet2-simple](https://github.com/Adithya-Jayan/nnet2-simple)
