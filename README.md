# 🎭 Real-Time Emotion Detection

A powerful real-time emotion detection application that uses YOLO for face detection and RepVGG for emotion classification. The application can detect 8 different emotions in real-time using your webcam or from images/videos.

## ✨ Features

- **Real-time emotion detection** using webcam
- **8 emotion categories**: anger, contempt, disgust, fear, happy, neutral, sad, surprise
- **High accuracy** using state-of-the-art YOLO and RepVGG models
- **Multiple input sources**: webcam, images, videos
- **Easy to use** with simple command-line interface
- **Cross-platform** support (Windows, macOS, Linux)

## 🎯 Detected Emotions

| Emotion | Description |
|---------|-------------|
| 😠 Anger | Facial expressions showing anger or frustration |
| 😏 Contempt | Disdainful or scornful expressions |
| 🤢 Disgust | Expressions of revulsion or strong dislike |
| 😨 Fear | Anxious or frightened expressions |
| 😊 Happy | Joyful, cheerful, or pleased expressions |
| 😐 Neutral | Calm, expressionless, or balanced state |
| 😢 Sad | Sorrowful, dejected, or melancholy expressions |
| 😲 Surprise | Startled, amazed, or astonished expressions |

## 🚀 Quick Start

### Prerequisites

- Python 3.7 or higher
- Webcam (for real-time detection)
- At least 4GB RAM (8GB recommended)
- GPU support (optional, for better performance)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/mahidher/emotion-detection.git
   cd emotion-detection
   ```

2. **Create a virtual environment** (recommended)
   ```bash
   # Windows
   python -m venv venv
   venv\Scripts\activate

   # macOS/Linux
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Download model weights** (if not already present)
   - The required model weights should be in the `weights/` folder
   - `repvgg.pth` - Emotion classification model
   - `yolov7-tiny.pt` - Face detection model

### 🎮 Usage

#### Real-time Webcam Detection (Default)
```bash
python main.py
```

#### Different Camera
```bash
python main.py --source 1  # Use camera 1
```

#### Image Detection
```bash
python main.py --source path/to/image.jpg
```

#### Video Detection
```bash
python main.py --source path/to/video.mp4
```

#### Save Output
```bash
python main.py --output-path output.mp4
```

#### Show FPS
```bash
python main.py --show-fps
```

### 🎛️ Command Line Options

| Option | Description | Default |
|--------|-------------|---------|
| `--source` | Input source (0 for webcam, path for files) | `0` |
| `--img-size` | Image size for processing (pixels) | `512` |
| `--conf-thres` | Confidence threshold for face detection | `0.5` |
| `--iou-thres` | IOU threshold for NMS | `0.45` |
| `--device` | Device to use (cpu, 0, 1, 2, 3) | `''` (auto) |
| `--output-path` | Save location for output | `output.mp4` |
| `--no-save` | Don't save images/videos | `False` |
| `--hide-img` | Hide the display window | `False` |
| `--hide-conf` | Hide confidence scores | `False` |
| `--show-fps` | Display FPS counter | `False` |
| `--line-thickness` | Bounding box thickness | `2` |

### 🎮 Controls

While the application is running:
- **Press 'q'** - Quit the application
- **Press ESC** - Quit the application
- **Close window** - Quit the application (X button)

## 📁 Project Structure

```
emotion-detection/
├── main.py                 # Main application file
├── emotion.py             # Emotion detection module
├── repvgg.py              # RepVGG model implementation
├── requirements.txt       # Python dependencies
├── README.md             # This file
├── models/               # YOLO model files
│   ├── experimental.py   # Model loading utilities
│   ├── common.py         # Common model components
│   └── ...
├── utils/                # Utility functions
│   ├── general.py        # General utilities
│   ├── datasets.py       # Data loading utilities
│   └── ...
└── weights/              # Model weights
    ├── repvgg.pth        # Emotion classification model
    ├── yolov7-tiny.pt    # Face detection model
    └── ...
```

## 🔧 Troubleshooting

### Common Issues

1. **"ModuleNotFoundError: No module named 'cv2'"**
   ```bash
   pip install opencv-python
   ```

2. **"ModuleNotFoundError: No module named 'torch'"**
   ```bash
   pip install torch torchvision
   ```

3. **"Weights only load failed"**
   - This is fixed in the current version with `weights_only=False`

4. **Camera not detected**
   - Make sure your webcam is connected and not being used by another application
   - Try different camera indices: `--source 0`, `--source 1`, etc.

5. **Low FPS performance**
   - Use GPU if available: `--device 0`
   - Reduce image size: `--img-size 320`
   - Close other applications

### Performance Tips

- **Use GPU**: Set `--device 0` for NVIDIA GPU acceleration
- **Reduce image size**: Use `--img-size 320` for faster processing
- **Close other apps**: Free up system resources
- **Good lighting**: Ensure adequate lighting for better face detection

## 🛠️ Development

### Adding New Emotions

To add new emotion categories:

1. Modify the `emotions` list in `emotion.py`
2. Retrain the RepVGG model with new data
3. Update the model weights

### Customizing the UI

- Modify colors in `main.py` (line 52)
- Adjust bounding box thickness with `--line-thickness`
- Change display size in the `cv2.resize()` call

## 📊 Model Information

- **Face Detection**: YOLOv7-tiny (fast and accurate)
- **Emotion Classification**: RepVGG-A0 (efficient architecture)
- **Input Size**: 224x224 pixels for emotion classification
- **Output**: 8 emotion probabilities

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🙏 Acknowledgments

- [YOLOv7](https://github.com/WongKinYiu/yolov7) for face detection
- [RepVGG](https://github.com/DingXiaoH/RepVGG) for emotion classification
- [OpenCV](https://opencv.org/) for computer vision utilities
- [PyTorch](https://pytorch.org/) for deep learning framework

## 📞 Support

If you encounter any issues or have questions:

1. Check the [Troubleshooting](#-troubleshooting) section
2. Search existing [Issues](https://github.com/mahidher/emotion-detection/issues)
3. Create a new issue with detailed information

---

**Made with ❤️ by [mahidher](https://github.com/mahidher)**