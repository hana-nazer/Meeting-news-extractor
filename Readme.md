🎙️ Meeting Notes & Action Item Extractor
In today’s workplace, meetings generate a lot of spoken content which is time-consuming to transcribe, summarize, and extract action items from. Manually creating meeting notes and identifying follow-up tasks can be inefficient and prone to errors.
 There is a need for an automated solution that can transcribe meeting audio, summarize discussions, and highlight actionable items.

💡 Solution Architecture
The solution is a Streamlit-based web application that allows users to upload an audio file of a meeting. The app transcribes the audio using OpenAI’s Whisper model, summarizes the transcript using Hugging Face transformer models, and extracts possible action items automatically.
Components
Frontend (Streamlit UI):
File uploader for audio files (.mp3, .wav, .m4a).


Displays the uploaded audio player.


Shows transcript, summary, and extracted action items.


Backend (app.py):
Loads and caches Whisper model for transcription.


Loads and caches Hugging Face summarization pipeline.


Transcribes uploaded audio into text.


Summarizes the transcript into concise meeting notes.


Extracts sentences containing potential action items.


Models:
Whisper (base): Speech-to-text transcription model.


DistilBART (sshleifer/distilbart-cnn-12-6): Lightweight summarization model from Hugging Face.


Action Item Extraction:
Simple keyword-based detection of action items (e.g., “will”, “need to”, “should”, “action”, “task”).



🔗 Code Repository
The complete source code is available on GitHub:
 GitHub Link

🗂️ Project Structure
meeting-notes-extractor/
├── app.py                # Main Streamlit application
├── requirements.txt      # Required Python packages
└── README.md             # Project documentation/introduction


⚙️ Features
Upload audio files in .mp3, .wav, or .m4a format.


Transcribes audio to text using Whisper model.


Summarizes the transcript using Hugging Face DistilBART model.


Extracts potential action items from transcript automatically.


User-friendly Streamlit interface with progress spinners.


Displays audio player, transcript, summary, and action items in one page.


Uses caching to avoid reloading models on every run.



🧠 Model Options
Model
Description
whisper (base)
Local speech-to-text model for transcription
sshleifer/distilbart-cnn-12-6
Fast, lightweight summarizer for meeting notes

(Other summarization models from Hugging Face can be swapped in the code if needed.)

🧱 Backend (app.py)
Uses st.cache_resource to cache model loading for performance.


Transcribes uploaded audio file to text using Whisper.


Summarizes the transcript using Hugging Face summarization pipeline.


Extracts action items with a simple keyword-based filter.


Presents output in three sections:


Transcript


Meeting Notes (Summary)


Action Items



🖼️ Frontend (Streamlit UI)
Built with Streamlit’s declarative UI.


Allows file upload and playback of uploaded audio.


Displays a progress spinner during transcription and summarization.


Presents transcript, summarized meeting notes, and extracted action items.


Lists action items in numbered format or shows a “No explicit action items detected” message.



📦 requirements.txt
streamlit
openai
whisper
pandas
transformers
torch

(Note: transformers and torch should be added for summarization model; not explicitly listed in your code but required.)

🧪 Example User Flow
User opens the app via streamlit run app.py.


User uploads a meeting audio file (.mp3, .wav, .m4a).


App plays uploaded audio and transcribes it to text with Whisper.


Transcript appears under “📝 Transcript”.


The app summarizes the transcript into “📋 Meeting Notes”.


Action items are automatically extracted and displayed under “✅ Action Items”.



⚡ Future Enhancements
Allow selection between different Whisper models (tiny, base, large).


Provide multiple summarization models (BART, T5) with a dropdown.


Use advanced NLP to extract action items with higher accuracy (e.g., spaCy or fine-tuned models).


Add download button for transcript and summary as text or PDF.


Integrate speaker diarization to attribute text to different speakers

