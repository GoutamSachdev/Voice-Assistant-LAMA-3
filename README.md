# Goti: Next-Gen Voice Assistant with LLaMA 3

Welcome to the Goti project! This repository hosts the code and resources for Goti, a cutting-edge voice assistant built on the powerful open-source LLaMA 3 model. Goti is designed to deliver an engaging and accurate voice interaction experience with real-time voice-to-text conversion and custom fine-tuning.

## Features

- **Real-Time Voice-to-Text Conversion:** Utilizes advanced speech recognition for instant and precise transcription.
- **Custom Fine-Tuning:** Enhanced responses through fine-tuning with a unique dataset, ensuring relevance and engagement.
- **Trendy Yet Professional:** Delivers interactions with a combination of a trendy, swaggy tone and a professional touch.

## Technical Achievements

- **Open-Source Power:** Built on the LLaMA 3 model, known for its robust and versatile language understanding.
- **Tailored Dataset:** Fine-tuned with a bespoke dataset for improved response accuracy.
- **Seamless Integration:** Real-time voice recognition for a smooth and dynamic user experience.

## Installation

To get started with Goti, you need to install the necessary dependencies. Follow these steps:

1. **Clone the Repository:**
    ```bash
    git clone https://github.com/yourusername/goti.git
    cd goti
    ```

2. **Install Dependencies:**
    ```bash
    pip install "unsloth[colab-new] @ git+https://github.com/unslothai/unsloth.git"
    pip install --no-deps "xformers<0.0.27" "trl<0.9.0" peft accelerate bitsandbytes
    pip install SpeechRecognition pydub
    apt-get install -y ffmpeg
    pip install unidecode
    pip install SpeechRecognition
    ```

3. **Install Real-Time Voice Cloning Dependencies:**
    ```bash
    git_repo_url='https://github.com/CorentinJ/Real-Time-Voice-Cloning.git'
    project_name=$(basename ${git_repo_url} .git)
    if [ ! -d "${project_name}" ]; then
      git clone --recursive ${git_repo_url}
      cd ${project_name}
      pip install -r requirements.txt
      pip install --upgrade gdown
      apt-get install -y libportaudio2
      pip install https://github.com/tugstugi/dl-colab-notebooks/archive/colab_utils.zip
      mkdir -p saved_models/default/
      cd saved_models/default/
      gdown https://drive.google.com/uc?id=1q8mEGwCkFy23KZsinbuvdKAQLqNKbYf1
      gdown https://drive.google.com/uc?id=1EqFMIbvxffxtjiVrtykroF6_mUh-5Z3s
      gdown https://drive.google.com/uc?id=1cf2NO6FtI0jDuy8AV3Xgn6leO6dHjIgu
    fi
    ```

## Usage

To use Goti, you can follow these steps:

1. **Load the Models:**
    ```python
    import sys
    from pathlib import Path
    sys.path.append('Real-Time-Voice-Cloning')

    from synthesizer.inference import Synthesizer
    from encoder import inference as encoder
    from vocoder import inference as vocoder

    encoder.load_model('Real-Time-Voice-Cloning/saved_models/default/encoder.pt')
    synthesizer = Synthesizer('Real-Time-Voice-Cloning/saved_models/default/synthesizer.pt')
    vocoder.load_model('Real-Time-Voice-Cloning/saved_models/default/vocoder.pt')
    ```

2. **Record and Synthesize Audio:**
    ```python
    from dl_colab_notebooks.audio import record_audio, upload_audio
    from IPython.display import display, Audio, clear_output
    import ipywidgets as widgets

    # Code for recording and synthesizing audio will go here
    ```

## Contributing

We welcome contributions to Goti! If you have suggestions, improvements, or bug fixes, please fork the repository and submit a pull request.

## License

This project is licensed under the @gksachdev46@gmail.com  Goutam Sachdev.

## Acknowledgements

- **LLaMA 3 Model:** Thanks to the team behind the LLaMA 3 model for their incredible work.
- **Real-Time Voice Cloning:** Special thanks to the creators of the Real-Time Voice Cloning repository for their valuable resources.
