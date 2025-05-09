Run the Jupyter notebook on the cloud or with a GPU T4, follow the cells, and run the last setup.
It will use FastLanguageModel from unsloth to fine-tune ollama with precision 8 bits and shrink it to 4 bits.
You can change the number to according bit precision depending on need.

Then copy the model file and the gguf file into the Raspberry Pi, and run the python code medicalgui3.py, it will work fine.
