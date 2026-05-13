# Local LLM Deployment with Ollama

**Author:** Sehajjot Singh Sawhney | sehajjot20@gmail.com  


## Introducing Today's Project!

This project demonstrates the setup of a fully local AI environment using Ollama. The primary objective is to build a privacy-centric infrastructure that allows for the execution of Large Language Models (LLMs) without transmitting data to third-party cloud providers.

This setup ensures 100% data sovereignty, making it an ideal foundation for workplace environments that handle sensitive information.

### Key tools and concepts

- **Ollama**: A streamlined tool for local LLM orchestration.

- **Qwen2.5 (0.5B)**: A lightweight model optimized for local performance.

- **Custom Personas**: Using Modelfiles to define system prompts and specific AI behaviors.

- **Privacy-First AI**: Running models locally to bypass cloud API dependencies.

---

## Installing Ollama for Local AI

### Verification of Ollama Service

Once Ollama is installed and running, we verify the local server is listening on port 11434 using PowerShell:
```bash
curl.exe http://localhost:11434
```

Output: `Ollama is running`

![Image](http://learn.nextwork.org/calm_blue_festive_marian_plum/uploads/ai-ollama-setup_h4n8k2m6)

### Pulling the Model

We use the `qwen2.5:0.5b model`. The 0.5B signifies 500 million parameters. In LLM terms, parameters represent the patterns the model learned during training; fewer parameters result in a faster, more resource-efficient model suitable for local machines.
```bash
ollama pull qwen2.5:0.5b
```

![Image](http://learn.nextwork.org/calm_blue_festive_marian_plum/uploads/ai-ollama-setup_b5c9d3f7)

---

## Usage
### Basic Interaction
To launch the model in an interactive terminal session:

```bash
ollama run qwen2.5:0.5b
```

---

## Chatting with My Local AI

I chatted with my local AI by first running the model locally. To run the model I used the command `ollama run qwen2.5:0.5b` and then to test I passed `What is the capital of France?`
It responded with `The capital of France is Paris.`.
This is different from cloud AI because we are not making any API calls to the cloud AI providers server to answer our question rather we are running the model locally and in this way no data is passed outside our system.

![Image](http://learn.nextwork.org/calm_blue_festive_marian_plum/uploads/ai-ollama-setup_n1p5r9t3)

---

## Exploring Local AI Limitations

In this step, I'm going to discover what Local AI models can and can't.

![Image](http://learn.nextwork.org/calm_blue_festive_marian_plum/uploads/ai-ollama-setup_d8r4t6w1)

### Custom Persona: "Nova"
I extended this project by creating a custom AI persona named Nova. Nova is configured as a friendly coding tutor. This was achieved by creating a Modelfile to inject a specific system prompt into the model architecture.

To recreate the Nova persona, create a file named Nova.modelfile with the following content:
```dockerfile
FROM qwen2.5:0.5b

SYSTEM """
You are Nova, a friendly and patient coding tutor. 
Your goal is to help users understand backend concepts 
by explaining them simply and providing clean code examples.
"""
```

Then, build and run the model:

```bash
ollama create nova -f Nova.modelfile
ollama run nova
```

---

## Technical Learnings
### Local AI vs. Cloud AI

Standard cloud AI services rely on API calls to external servers. By running models locally, we eliminate external data transit, ensuring that files, emails, and private prompts remain on the local hardware.

### The Role of RAG
While local models are powerful, they are trained on general knowledge. `Retrieval-Augmented Generation (RAG)` is the next step for this project, which will involve giving the AI access to specific local documents to provide context-aware answers without needing to retrain the entire model.

---
