---
title: "LLM_Model using Ollama"
date: 2025-01-31 00:00:00 +0800
categories: [LLM_Model, DeepSeek, ChatGPT]
tages: [Projects]
---


> This app is a dummy of Big available LLM model using models like ollama deepseek-r1:1.5b
{: .prompt-info}

# LLM_model
 This app is a dummy of the Big available LLM model using models like Ollama deepseek-r1:1.5b 


# 🧠 DeepSeek Code Companion

[![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?logo=streamlit&logoColor=white)](https://streamlit.io/)
[![LangChain](https://img.shields.io/badge/LangChain-00ADD8?logo=langchain&logoColor=white)](https://python.langchain.com/)
[![Ollama](https://img.shields.io/badge/Ollama-FFFFFF?logo=ollama&logoColor=black)](https://ollama.ai/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Your AI-powered pair programmer with advanced debugging capabilities and code optimization features.

![Demo Screenshot](https://github.com/AnuragSharma5893/LLM_model/blob/main/ui%20(2).png?raw=true)
## Features

- 🚀 Multi-model support (DeepSeek, LLaVA, Llama3)
- 🔥 Real-time code debugging assistance
- 📝 Automatic code documentation generation
- 💡 Intelligent solution design suggestions
- 🎨 Streamlit-powered chat interface with dark theme
- ⚙️ Customizable model parameters (temperature, model size)
- 📚 Context-aware conversation history
- 🖥️ Local LLM deployment via Ollama

## Installation

1. **Prerequisites**:
   - [Ollama](https://ollama.ai/) installed and running
   - Python 3.9+ environment

2. Clone the repository:
bash
git clone https://github.com/yourusername/deepseek-code-companion.git
cd deepseek-code-companion


3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Pull desired models (example for DeepSeek 1.5B):
```bash
ollama pull deepseek-r1:1.5b
```

## Usage

1. Start the Streamlit app:
```bash
streamlit run app.py
```

2. Configure settings in the sidebar:
   - Select model variant (1.5B, 3B, 32B)
   - Adjust temperature for creativity control
   - View model capabilities

3. Interact with the chat interface:
   - Type coding questions or paste error messages
   - Get AI-powered solutions with debugging support
   - Clear chat history as needed

## Configuration


### Available Models
## LLM Models

<div style="display: flex; flex-wrap: wrap; gap: 20px;">

  <div style="flex: 1; min-width: 200px; border: 1px solid #ddd; padding: 10px; border-radius: 5px;">
    <strong>Model Name:</strong> `deepseek-r1:1.5b`<br>
    <strong>Size:</strong> 1.5B<br>
    <strong>Best For:</strong> Quick answers, basic code
  </div>

  <div style="flex: 1; min-width: 200px; border: 1px solid #ddd; padding: 10px; border-radius: 5px;">
    <strong>Model Name:</strong> `deepseek-r1:3b`<br>
    <strong>Size:</strong> 3B<br>
    <strong>Best For:</strong> Balanced performance
  </div>

  <div style="flex: 1; min-width: 200px; border: 1px solid #ddd; padding: 10px; border-radius: 5px;">
    <strong>Model Name:</strong> `deepseek-r1:32b`<br>
    <strong>Size:</strong> 32B<br>
    <strong>Best For:</strong> Complex problem solving
  </div>

  <div style="flex: 1; min-width: 200px; border: 1px solid #ddd; padding: 10px; border-radius: 5px;">
    <strong>Model Name:</strong> `llava:latest`<br>
    <strong>Size:</strong> 7B<br>
    <strong>Best For:</strong> Multimodal tasks
  </div>

  <div style="flex: 1; min-width: 200px; border: 1px solid #ddd; padding: 10px; border-radius: 5px;">
    <strong>Model Name:</strong> `llama3.2:latest`<br>
    <strong>Size:</strong> 70B<br>
    <strong>Best For:</strong> Advanced reasoning
  </div>
</div>

### Temperature Guide
- **Low (0.0-0.3)**: Factual, deterministic responses
- **Medium (0.4-0.6)**: Balanced creativity
- **High (0.7-1.0)**: Creative solutions, experimental code

## Technologies Used

- **Streamlit**: Web interface and chat management
- **LangChain**: LLM pipeline orchestration
- **Ollama**: Local LLM deployment and management
- **DeepSeek Models**: Specialized coding AI models
- **Custom CSS**: Styled chat interface and components

## Contributing

Contributions are welcome! Please follow these steps:
1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

Distributed under the MIT License. See `LICENSE` for more information.

## Acknowledgements

- Ollama team for seamless local LLM management
- LangChain for LLM orchestration framework
- DeepSeek for their specialized coding models
- Streamlit for rapid UI development

---

**Note**: Ensure Ollama server is running at `http://localhost:11434` before starting the app. Custom CSS styling can be modified in the app.py header section.




