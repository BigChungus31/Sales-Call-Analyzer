# Sales Call Quality Analyzer

A high-performance AI system that analyzes sales call recordings to provide actionable insights for sales teams.

## Features

- **Talk-time Analysis**: Calculates speaking percentage for each participant
- **Question Tracking**: Counts and analyzes questions asked during the call
- **Monologue Detection**: Identifies longest continuous speech segments
- **Sentiment Analysis**: Determines overall call sentiment (positive/negative/neutral)
- **Sales Rep Identification**: Automatically distinguishes sales rep from customer
- **Actionable Insights**: Provides specific recommendations for improvement

## Technical Approach (Under 200 words)

This Call Quality Analyzer uses a multi-stage AI pipeline optimized for Google Colab's free tier:

**Audio Processing**: yt-dlp downloads YouTube audio, pydub normalizes and converts to 16kHz mono WAV for optimal transcription.

**Transcription**: OpenAI Whisper "tiny" model with GPU acceleration provides fast, accurate speech-to-text with timestamps while staying under memory limits.

**Speaker Diarization**: Custom algorithm uses voice activity detection, silence gaps, and speech pattern changes to identify speaker transitions without expensive external APIs.

**Sales Rep Identification**: Multi-signal analysis examining question ratios, business terminology, formal language patterns, and average segment length to distinguish sales rep from customer.

**Metrics Calculation**: Parallel processing computes talk-time ratios from timestamps, counts questions via regex, finds longest continuous speech segments, and performs transformer-based sentiment analysis.

**Optimization**: GPU acceleration with CPU fallback, model caching, concurrent processing, and comprehensive error handling ensure reliability on free Colab tier.

The system prioritizes speed and accuracy while remaining cost-free, making it production-ready for startup environments.

## Requirements

- Google Colab (Free tier supported)
- Internet connection for package installation
- YouTube URL with audio content

## Usage

1. Open the notebook in Google Colab
2. Run all cells to install dependencies and load models
3. The system will automatically analyze the test video
4. Results display processing time, talk ratios, questions, sentiment, and actionable insights

## Performance

- Guaranteed processing under 30 seconds
- GPU-accelerated when available with CPU fallback
- Handles poor audio quality with robust preprocessing
- Memory optimized for free Colab tier

## Sample Output

See `test_results.txt` for complete analysis results on the provided test video.

## Repository Structure

```
├── VoiceCallAnalysis.ipynb    # Main Colab notebook
├── README.md                       # This file
├── requirements.txt               # Python dependencies
└── test_results.txt              # Sample analysis output
```
