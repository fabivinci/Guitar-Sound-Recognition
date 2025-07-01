# Guitar Chord Recognition for IoT
A real-time guitar chord recognition system based on Machine Learning for IoT devices

## Project Description
This project implements a real-world use case of Machine Learning applied to the IoT domain, developing an automatic guitar chord recognition system optimized to run on Raspberry Pi. The system can recognize guitar chords in real-time through a microphone connected to the device, using advanced audio signal processing techniques and convolutional neural networks.

## Objectives

Beginners: Automatic chord learning from original song audio
Orchestra Applications: Enhancement of existing applications for automatic sheet music reading
IoT Integration: Implementation of an edge computing system for real-time audio analysis

## Dataset
### Dataset Composition
The dataset was created from scratch for this project, including the 8 most common guitar chords: Am, Bb, Bdim, C, Dm, Em, F, G

### Dataset Characteristics
Instrument Diversity:
- 20 real guitars played by different musicians
- 5 virtual guitars generated with GarageBand
- 25 computational audio samples through plugin filtering

Pattern Variability:
- 4 different strumming patterns
- Electric guitars (various types), classical and acoustic guitars
- Mix of virtual and real samples for maximum heterogeneity

Versioning:
Version 3 (best performance):
Training set: 30 virtual + 15 real guitars
Test set: 5 virtual + 5 real guitars

Different datasets can be found in this link: https://www.kaggle.com/fabianavinci/datasets

## Audio Signal Analysis
### Preprocessing Pipeline
- Normalization: Verification of 44100 kHz frequency and mono-channel
- Zero Padding: Handling of variable-length audio
- STFT (Short-Time Fourier Transform): Transformation from time domain to frequency domain
- MFCC (Mel-Frequency Cepstral Coefficients): Feature extraction that approximates human auditory perception

### Enhancement Techniques
Experimentation with noise reduction (not implemented in final version)
Dataset-specific optimization for future implementations

## Machine Learning Models
### Tested Architectures

1. CNN (Convolutional Neural Network) - Best Performance:
- 2D convolutional layers
- Batch normalization
- ReLU activation function
- Global Average Pooling 2D
Accuracy: 80%

3. DCNN (Deep Convolutional Neural Network):
Accuracy: 74%

4. LSTM (Long Short-Term Memory):
Lower performance compared to CNN models

### Optimizations
- Experimentation with MaxAveragingPooling vs GlobalAveragePooling
- Tuning of filters, batch size, and learning rate
- 50 epochs with batch size 64 for best results

## Communication Protocols
MQTT Implementation
Configuration:
- Broker: Mosquitto
- Topic: "/279918/GuitarPred"
- Purpose: Live communication between Raspberry Pi and local computer

### Features:
- Real-time audio recording from microphone
- Data transmission for prediction
- Results visualization on computer terminal

## System Architecture
- Microphone → Raspberry Pi → [Preprocessing + ML Model] → MQTT → Computer Terminal
- Results and Performance
- Performance Metrics
- ModelEpochsBatch SizeTest AccuracyCNN506480%DCNN506474%

## Error Analysis
### Problematic Chords:
Em (E minor): Higher difficulty in recognition
F (F major): Confusion with similar chords

### Environmental Factors:
- Testing environment significantly influences audio input quality
- Need for calibration in different acoustic contexts

## Technologies Used
- Hardware: Raspberry Pi, USB Microphone
- ML Framework: TensorFlow/Keras
- Preprocessing: librosa, numpy
- Communication: MQTT (Mosquitto broker)
- Language: Python
- Audio Processing: STFT, MFCC

## Limitations and Future Developments
- Dataset expansion with more complex chords
- Implementation of adaptive noise reduction
- Optimization for different acoustic environments
- Integration with music learning applications

## Installation and Usage
### Prerequisites:
- Raspberry Pi 3B+ or higher
- USB Microphone
- Python 3.7+
- MQTT Broker (Mosquitto)

### Dependencies
bashpip install tensorflow librosa numpy scipy paho-mqtt

### Running the System
- Start MQTT broker on Raspberry Pi
- Run the chord recognition script
- Connect to the specified MQTT topic for real-time predictions

Authors: Fabiana Vinci, Joana da Orada Gonçalves
