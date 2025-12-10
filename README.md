# EmpathAI: Emotion-Aware Chatbot

> An intelligent conversational AI system that understands and responds to user emotions in real-time using camera-based emotion detection and LLM integration.
demo video link:https://www.linkedin.com/posts/akhil-p-216829235_artificialintelligence-empathyinai-innovation-activity-7283370709093904384-MZ__?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAAEKBsb8BOzBiMtI-owcqYI7C7HQtFKKgByw

[![GitHub stars](https://img.shields.io/github/stars/manikandanshibu/EmpathAI-Emotion-aware-chatbot?style=social)](https://github.com/manikandanshibu/EmpathAI-Emotion-aware-chatbot)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Python](https://img.shields.io/badge/python-3.8%2B-blue)](https://www.python.org/downloads/)

## Overview

EmpathAI is an emotion-aware conversational AI system that combines real-time facial emotion recognition with large language models (LLMs) to deliver context-aware and emotionally intelligent responses. The system detects user emotions through webcam input and adjusts its conversational tone and content accordingly.

## Features

- **Real-time Emotion Detection**: Uses camera feed to detect facial emotions (happy, sad, angry, neutral, surprised, etc.)
- **Emotion-Aware Responses**: LLM generates responses tailored to the detected emotional state
- **Multi-modal Integration**: Combines computer vision and NLP for holistic understanding
- **Low-Latency Processing**: Efficient emotion detection and response generation
- **Easy-to-Use Interface**: Simple CLI and optional GUI for interaction

## Tech Stack

### Core Dependencies
- **Deep Learning Framework**: TensorFlow / PyTorch
- **Emotion Detection**: OpenCV + Pre-trained CNN models (FER2013 dataset-based)
- **Large Language Model**: LLM integration (GPT-based or open-source alternatives)
- **Camera Input**: OpenCV (cv2)
- **Language**: Python 3.8+

### Key Libraries
```
tensorflow/torch
opencv-python
requests
numpy
pandas
python-dotenv
```

## Installation

### Prerequisites
- Python 3.8 or higher
- Webcam (for real-time emotion detection)
- 4GB+ RAM recommended

### Setup

1. **Clone the repository**
```bash
git clone https://github.com/manikandanshibu/EmpathAI-Emotion-aware-chatbot.git
cd EmpathAI-Emotion-aware-chatbot
```

2. **Create virtual environment**
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\\Scripts\\activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Configure API keys** (if using external LLM)
```bash
cp .env.example .env
# Edit .env and add your LLM API keys
```

## Usage

### Basic Usage
```bash
python main.py
```

The system will:
1. Access your webcam
2. Display real-time emotion detection
3. Process your text input or speech
4. Generate emotion-aware responses
5. Display conversations with detected emotions

### Example Interaction
```
[Webcam Active] Detected Emotion: Happy (Confidence: 0.89)

User: Tell me something interesting about machine learning
AI: Since you're in a great mood, here's something exciting about AI!
    Machine learning models can now detect patterns in data...
```

## Architecture

```
┌─────────────────┐
│   Webcam Input  │
└────────┬────────┘
         │
         ▼
┌─────────────────────────┐
│ Emotion Detection (CNN) │
└────────┬────────────────┘
         │
         ▼
┌─────────────────────────┐      ┌──────────────┐
│ Emotion Classification  │────▶ │  User Input  │
└────────┬────────────────┘      └──────┬───────┘
         │                              │
         └──────────────┬───────────────┘
                        ▼
              ┌──────────────────┐
              │ LLM Prompt Ctx   │
              └────────┬─────────┘
                       ▼
              ┌──────────────────┐
              │  Generate Reply  │
              └────────┬─────────┘
                       ▼
              ┌──────────────────┐
              │ Display Response │
              └──────────────────┘
```

## Project Structure

```
EmpathAI-Emotion-aware-chatbot/
├── src/
│   ├── emotion_detection.py      # Emotion detection model
│   ├── llm_integration.py        # LLM API integration
│   ├── chatbot.py               # Main chatbot logic
│   └── utils.py                 # Utility functions
├── models/
│   └── emotion_model.h5         # Pre-trained emotion detection model
├── main.py                      # Entry point
├── requirements.txt             # Project dependencies
├── .env.example                 # Environment variables template
├── README.md                    # Documentation
└── LICENSE                      # MIT License
```

## Model Details

### Emotion Detection Model
- **Architecture**: Convolutional Neural Network (CNN)
- **Training Data**: FER2013 dataset (~35,000 images)
- **Emotion Classes**: 7 categories
  - Angry
  - Disgusted
  - Fearful
  - Happy
  - Neutral
  - Sad
  - Surprised

### Performance Metrics
- **Accuracy**: ~65-70% on test set
- **Inference Time**: ~50-100ms per frame
- **Model Size**: ~5-10MB

## Configuration

Edit `.env` for customization:
```env
# LLM Configuration
LLM_API_KEY=your_api_key_here
LLM_MODEL=gpt-3.5-turbo
EMOTION_THRESHOLD=0.7

# Camera Settings
CAMERA_ID=0
FPS=30

# Display Settings
DISPLAY_CONFIDENCE=true
DISPLAY_FPS=true
```

## Results & Performance

- Real-time emotion detection with 70%+ accuracy
- ~100ms latency for emotion-aware response generation
- Supports continuous conversation with emotion context
- Tested on RTX 3050 GPU and CPU mode

## Future Enhancements

- [ ] Multi-face emotion detection
- [ ] Speech emotion recognition integration
- [ ] Emotion history and trend analysis
- [ ] Fine-tuned emotion-specific LLM models
- [ ] Web interface for easier deployment
- [ ] Support for multiple languages
- [ ] Edge deployment optimization

## Limitations

- Emotion detection accuracy varies with lighting conditions
- Works best with frontal face orientation
- Requires stable webcam input
- LLM quality depends on selected model

## Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Citation

If you use EmpathAI in your research or project, please cite:

```bibtex
@software{empathai2024,
  author = {Manikandan Shibu},
  title = {EmpathAI: Emotion-Aware Chatbot with Camera Integration},
  year = {2024},
  url = {https://github.com/manikandanshibu/EmpathAI-Emotion-aware-chatbot}
}
```

## Troubleshooting

### Webcam not detected
- Ensure webcam is connected and accessible
- Check camera permissions in system settings
- Try: `python -c "import cv2; print(cv2.VideoCapture(0).isOpened())"`

### Low emotion detection accuracy
- Ensure adequate lighting
- Position face directly toward camera
- Consider retraining model on custom dataset

### API rate limiting
- Implement request queueing
- Check LLM service quotas
- Consider caching responses

## License

This project is licensed under the MIT License - see [LICENSE](LICENSE) file for details.

## Author

**Manikandan Shibu**
- GitHub: [@manikandanshibu](https://github.com/manikandanshibu)
- Email: Contact via GitHub profile

## Acknowledgments

- FER2013 dataset for emotion recognition training
- OpenCV community for computer vision tools
- LLM providers for API integration capabilities
- Contributors and users for feedback and improvements

---

**Star this repo if you find it helpful!** ⭐
