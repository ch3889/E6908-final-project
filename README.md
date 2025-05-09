Run the Jupyter notebook on the cloud or with a GPU T4, follow the cells, and run the last setup.
It will use FastLanguageModel from unsloth to fine-tune ollama with precision 8 bits and shrink it to 4 bits.
You can change the number to according bit precision depending on need.

Data: We were able to find this 2000+ patient dataset “disease_diagnosis.csv” on Kaggle, which contains information like age, gender, symptoms, heart rate, temperature, blood pressure, oxygen level, their diagnosis, and treatments. We will be extracting the three main parameters —heart rate, temperature, and oxygen level for fine-tuning our LLM.

Fine-tuning: We are using a pre-trained Meta–LLaMA–3.1–8 B instruct model loaded by sloth, applying LoRA adapters to enable parameter-efficient fine-tuning. Leveraging the trl library inside SFTTrainer from Hugging Face for fine-tuning the LLM with our dataset. After training the model, we save the model in gguf format and quantize it to Q4_0 for deployability on Raspberry Pi 5.

Hardware setup: We connected the sensor MAX30102, which can read us the heart rate and SpO2 values, to the Raspberry Pi through GPIO pins. The way we get data from the user is by reading sensor data from the user for 10 seconds, then filtering out the extreme values where it jumps or goes below 0, indicating a wrong input signal, saving all the validated data into a CSV file, and averaging all the recorded values for inference.

Software: We created this simple GUI with tkinter, which allows us to invoke the sensor reading and the OLLMA LLM when needed. Users can have a normal conversation with the medical agent, or click the “take vital” button to get their vital information and send it to the agent for inference, and get advice and a treatment plan suggested.

Then copy the model file and the gguf file into the Raspberry Pi, and run the python code medicalgui3.py, it will work fine.
