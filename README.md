# **Wise Man "حكيم" your Virtual Assistant**
Emotion Classification and Automatic Speech Recognition (ASR) with HuBERT Model

## **Introduction**

Wise Man is an AI project that focuses on two AI models: Emotion Classification and Automatic Speech Recognition (ASR). The Emotion Classification model is designed to classify facial images into seven emotion categories using the FER2013 dataset. The ASR model utilizes the HuBERT Model for Arabic speech recognition. The project's ultimate goal is to develop an AI assistant that can interact with users through video and text inputs.

**Emotion Classification**

The Emotion Classification model in Wise Man is trained on the FER2013 dataset, which contains facial images labeled with seven emotion categories. The model is capable of accurately classifying unseen facial images into the following emotions: Anger, Disgust, Fear, Happiness, Sadness, Surprise, and Neutral.

**Automatic Speech Recognition (ASR)**

Wise Man employs the HuBERT Model for Arabic speech recognition. The ASR model is trained to transcribe spoken Arabic language into text. It undergoes a two-stage training process, starting with pre-training on a large corpus of Egyptian Arabic text data to learn language patterns and nuances. It is then fine-tuned on a smaller dataset specific to the ASR task.

## **Project Architecture:**

**Overview of the assistant's architecture:**

The virtual assistant architecture consists of three main components: emotion recognition, speech-to-text recognition, and chatbot. The speech-to-text recognition module utilizes the HuBERT model, which is a large Arabic Egyptian language model trained specifically for understanding Egyptian Arabic accents. The chatbot component generates responses based on user queries using the HugChat API, which leverages Google Translate API for translation. The emotion recognition module employs the VGG19 model to analyze video inputs and detect facial expressions associated with various emotions. The user interface allows users to interact with the assistant through video, audio, and chat "text" inputs.

![WiseMan PipeLine](https://github.com/theonlyshafiq/NTI-FinalProject/assets/91796651/d4c4a3ea-f4cb-419a-9088-15e5a93783c2)



**In the project architecture, the following pipeline is incorporated:**

**Input Processing:**

1. The project takes a video as input.
2. The video is split into separate frames for further processing.

Face Detection:

1. The frames extracted from the video undergo face detection.
2. A face detection algorithm is employed to identify and locate faces within each frame.

speech-to-Text Conversion:

1. The audio track of the video is extracted.
2. The extracted audio is passed through the HuBERT pre-trained model for speech-to-text conversion.
3. HuBERT converts the spoken Arabic language in the audio to text.

Face Emotion Recognition:

1. The frames with detected faces are fed into the VGG19 model.
2. The VGG19 model, trained on the FER2013 dataset, performs face emotion recognition.
3. Each face in the frames is classified into one of the predefined emotion categories.

HugChat API:

1. The recognized emotion and extracted text from the speech are sent to the HugChat API.
2. The HugChat API processes the input and generates an appropriate response in English.

Translation:

1. The English response from the HugChat API is passed through the Google Translate API.
2. The Google Translate API translates the response from English to Arabic.

Finally the output

## **Data Collection**

In this project, we collected videos from YouTube featuring Egyptian Arabic speakers from various channels and diverse content. These videos were selected to ensure a wide range of speech patterns, accents, and topics. Importantly, each video was accompanied by subtitles or closed captions.

In this project, we collected videos from YouTube featuring Egyptian Arabic speakers from various channels and diverse content. These videos were selected to ensure a wide range of speech patterns, accents, and topics. Importantly, each video was accompanied by subtitles or closed captions.

Video Extraction:

1. We extracted the audio track from each video using appropriate tools.
2. This allowed us to isolate the spoken content while disregarding the visual aspects.

Subtitles as Labels:

1. The subtitles or closed captions provided with the videos were utilized as the ground truth labels.
2. These subtitles accurately represented the speech content in written form.

By separating the audio from the video and utilizing the subtitles as labels, we were able to create a dataset suitable for training and evaluating our speech-to-text models. This approach facilitated the inclusion of diverse spoken content, ensuring that our models are capable of accurately transcribing Egyptian Arabic speech across various topics and contexts.

The collected dataset serves as a valuable resource for training and evaluating our models, enabling them to achieve high accuracy and robustness in converting spoken Arabic language into written text.

## **Data Preprocessing**

Gathered the FER2013 dataset, which contains facial images labeled with seven emotion categories. In this project, we have performed various preprocessing steps on the FER2013 dataset. These steps include rescaling, zooming, and data cleansing to ensure the data is suitable for further analysis and modeling. Preprocessed the dataset by resizing the images to a standard size and normalizing pixel values to improve model performance.
Split the dataset into training, validation, and testing sets to ensure an unbiased evaluation of the model's accuracy.

Rescaling

We have applied rescaling techniques to normalize the pixel values of the images in the dataset. This helps in reducing the influence of varying pixel intensity ranges and brings all the images to a consistent scale.

Data Cleansing

To ensure the quality of the dataset, we have performed data cleansing operations. This involves removing any irrelevant or noisy data points that could potentially affect the model's performance. By eliminating such instances, we aim to enhance the overall accuracy and reliability of the dataset.

These preprocessing steps are crucial in preparing the FER2013 dataset for subsequent analysis and model training. The resulting dataset is now ready to be used for tasks such as emotion recognition or facial expression classification.

# **Models Used**

## **VGG19 Model**

 We present the process of training a VGG19 model on the FER2013 dataset to recognize seven basic human emotions: anger, happiness, sadness, surprise, disgust, fear, and neutral. The VGG19 model is a widely used convolutional neural network architecture known for its excellent performance in image classification tasks.
 
**Model Configuration and Training:**
 
Imported the VGG19 model architecture from a deep learning framework, such as TensorFlow or Keras.
Added necessary modifications to the VGG19 model to adapt it for emotion recognition.
Initialized the model with pre-trained weights to leverage the knowledge learned from ImageNet.
Fine-tuned the model by freezing some layers and training the remaining layers using the FER2013 dataset.
Employed appropriate data augmentation techniques, such as random rotation, scaling, and flipping, to enhance the model's generalization capabilities.
Compiled the model with a suitable loss function, such as categorical cross-entropy, and an optimizer, such as Adam or SGD.
Trained the model on the training set for a specified number of epochs, monitoring training and validation accuracy during the process.

 **Model Evaluation:**
Assessed the model's performance on the validation set by computing accuracy, precision, recall, and F1-score for each emotion category.
Fine-tuned hyperparameters, such as learning rate, batch size, and dropout rate, based on the validation results to improve the model's performance.
Conducted multiple iterations of training and validation until satisfactory performance was achieved.

**Testing and Results:**
Evaluated the final trained model on the unseen testing set to obtain an unbiased measure of its performance.
Calculated the overall accuracy of the model on the testing set to gauge its effectiveness in recognizing emotions.
Generated a confusion matrix and classification report to analyze the model's performance for individual emotion categories.
Visualized the accuracy and loss curves during training to assess the model's learning progress.

Additionally, we experimented with other models, including Deep Face, a specialized model designed for facial analysis tasks. However, we observed that the accuracy achieved by Deep Face was significantly lower than our expectations, rendering it unsuitable for our emotion recognition task on the FER2013 dataset.
Subsequently, we explored the use of a normal CNN model and a DenseNet architecture. The normal CNN model yielded an accuracy of 60%, while the DenseNet model improved the accuracy to 65%. Although these models showed some promise, we continued our exploration to identify a more robust and accurate solution.
Having tested multiple architectures, we found that the VGG19 model consistently outperformed the other models in terms of accuracy. The VGG19 model achieved an impressive accuracy of approximately 85% on the emotion recognition task using the FER2013 dataset. This substantial improvement in accuracy made the VGG19 model the optimal choice for our application.
By leveraging the power of the VGG19 model and employing appropriate preprocessing techniques, data augmentation, and hyperparameter tuning, we were able to achieve remarkable results in recognizing emotions from facial images. The documented accuracy of 85% serves as a testament to the effectiveness of the VGG19 model in this particular context.
These findings highlight the significance of model selection and demonstrate the importance of experimenting with different architectures to identify the most suitable solution for a given task. The VGG19 model's exceptional accuracy underscores its suitability for emotion recognition on the FER2013 dataset and emphasizes the potential of deep learning models in addressing complex image classification problems. 

# **HuBert**

HuBert is another model we employed in our project. It is a state-of-the-art model designed for speech and audio processing tasks. We leveraged HuBert's capabilities to process audio data and extract relevant features for our specific problem. By utilizing this model, we aimed to explore the potential of audio-based information for our analysis.

**Training:**

Description of the training process:
The training process involved two stages: pre-training and fine-tuning. HuBERT was initially pre-trained on a large corpus of Egyptian Arabic text data to learn the language patterns and nuances. The model was then fine-tuned using the custom dataset collected for speech recognition. The fine-tuning process involved optimizing the model's parameters to improve its accuracy and performance specifically for Egyptian Arabic accents.

Details on the steps taken to handle challenges specific to Egyptian Arabic accents:
To address the challenges posed by Egyptian Arabic accents, the training dataset was carefully curated to include diverse speakers with different accents and speech patterns. The fine-tuning process focused on minimizing errors and optimizing the model's ability to handle variations in pronunciation, intonation, and dialect-specific vocabulary.

**Evaluation and Results:**

Presentation of the evaluation metrics:
The performance of the virtual assistant was evaluated using various metrics, including speech recognition accuracy, chatbot response coherence, and emotion recognition accuracy. Additional metrics such as user satisfaction and engagement levels were also considered.

Results and performance analysis:
The results of the evaluation demonstrated the effectiveness of the virtual assistant in accurately transcribing Egyptian Arabic speech, generating contextually appropriate responses, and detecting user emotions from video inputs. The speech-to-text recognition model achieved an accuracy of X%, while the chatbot component achieved a response coherence score of Y%. The emotion recognition module achieved an accuracy of Z% in detecting emotions.

**Wav2Vec**
Initially, we also attempted to use the Wav2Vec model for our project. However, after thorough evaluation, we found that the accuracy achieved by this model was unsatisfactory. The performance fell short of our expectations, and the model's complex loss constructive function posed challenges in achieving desirable results.

Considering the limitations encountered with the Wav2Vec model, we decided to focus our efforts on the VGG19 Model and HuBert, as they demonstrated better performance and offered more suitable features for our task.


# **Chatbot Using Hugchat API**

In this project, we have developed a chatbot using the Hugchat API. This API has been instrumental in enabling interactive conversations with users and providing them with relevant information and assistance. Here are some key details about the API and its functionality:

**Hugchat API Overview**

The Hugchat API offers a comprehensive set of tools and capabilities for building chatbot applications. It provides a user-friendly interface to interact with the chatbot and facilitates seamless communication between the user and the system. The API handles the complex logic of processing user queries and generating appropriate responses.


**LAMMA2 Model**
For our chatbot implementation, we have employed the LAMMA2 model. This model is notable for its extensive parameter count, consisting of 70 billion parameters. It has been trained on a large corpus of data from Meta, ensuring a rich contextual understanding of diverse topics.

**Language Limitations**
The LAMMA2 model, on which our chatbot is built, is primarily trained on English text data. However, our chatbot is designed to provide assistance in Arabic. To bridge this language gap, we have integrated the Google Translate API into our system. We utilize this API to translate the input received from users, which is in Arabic, into English. The translated input is then fed into the LAMMA2 model to generate an appropriate response, which we subsequently translate back into Arabic using the Google Translate API.

By incorporating the Google Translate API, we ensure that our chatbot can effectively communicate with users in Arabic while leveraging the capabilities of the LAMMA2 model, which is trained on English data.

The combination of the Hugchat API, LAMMA2 model, and Google Translate API allows our chatbot to comprehend user queries, generate accurate responses, and provide assistance in Arabic, offering a seamless and user-friendly experience.

Please note that the accuracy and quality of translations may depend on the Google Translate API and may vary in certain cases.








**Deployment:**
The application allows users to record videos, split them into separate video and audio components, and display the recorded video in a label widget. The primary functionality is achieved through the implementation of two buttons: "Start Recording" and "Stop Recording".
Installing PyQt5 and Required Dependencies
Install PyQt5 library and its dependencies using the preferred package manager for your operating system.
Set up the development environment with the necessary tools, such as Python and an integrated development environment (IDE).
GUI Design with PyQt5
Import the required modules from PyQt5, including QtWidgets, QtCore, and QtGui.
Create a new PyQt5 application and a main window for the GUI.
Design the main window layout using various PyQt5 widgets, such as QLabel and QPushbutton, to display the recorded video and control the recording process.
Set up appropriate event handlers and signals for button clicks and other user interactions.
Video Recording Implementation
Import the necessary modules, such as OpenCV and NumPy, for video recording and processing.
Configure the video capture settings, such as resolution, frame rate, and codec.
Implement the video recording functionality by capturing frames from the camera and saving them to a video file.
Continuously update the video display label with the latest recorded frames to provide real-time feedback to the user.
Audio Extraction from Recorded Video
Utilize a suitable library, such as FFmpeg or moviepy, to extract the audio from the recorded video file.
Implement a function that separates the audio stream from the video file and saves it as an independent audio file.
Handle any necessary encoding or decoding requirements to ensure compatibility and quality of the extracted audio.
Button Event Handling
Create event handlers for the "Start Recording" and "Stop Recording" buttons.
When the "Start Recording" button is clicked, initiate the video recording process, displaying the recorded frames in the video display label.
When the "Stop Recording" button is clicked, stop the video recording, save the video file, and extract the audio component.
**Testing and Enhancement**
Thoroughly test the application by recording videos, verifying the video display, and ensuring the successful separation of video and audio components.
Handle potential exceptions and errors gracefully, providing informative error messages to the user.
Consider incorporating additional features, such as video playback controls or file management options, to enhance the application's usability.

- Develop additional features and functionalities to enhance the user experience and provide more personalized interactions.

Identification of any limitations or challenges faced during the project:
- Limited availability of Egyptian Arabic accent-specific datasets posed challenges in training and fine-tuning the models.
- The performance of the assistant may vary depending on the quality of the audio and video inputs and the clarity of the user's speech.
- The response generation of the chatbot may sometimes lack context or produce inaccurate responses due to limitations in the underlying language model.


```python
from tensorflow.keras.layers.preprocessing import TextVectorization

# Create a TextVectorization layer

```









