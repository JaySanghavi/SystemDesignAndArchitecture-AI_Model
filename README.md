# AI System Architecture Generator

## Overview

AI System Architecture Generator is a research-style project that demonstrates how deep learning can assist in generating system architecture insights from natural language prompts. The system takes a textual description of a software system and predicts architectural characteristics such as the number of components (nodes) and the number of connections (edges). These predictions can then be used to generate a visual architecture diagram automatically.

The project combines **deep learning models and graph rendering techniques** to build a simple prototype of an AI-powered system design assistant.

---

## Key Features

* Generates a **synthetic dataset of system design examples**
* Uses a **hybrid neural architecture (CNN + Transformer + Residual layers)**
* Learns relationships between **system descriptions and architecture complexity**
* Predicts **number of architecture nodes and edges**
* Automatically generates **architecture diagrams using Graphviz**
* Fully **Python and PyTorch based**
* Compatible with **Google Colab and local environments**

---

## Project Structure

```
architecture_ai/
│
├── generate_data.py   # Generates training dataset (300+ examples)
├── input.json         # Generated dataset containing system architecture samples
├── model.py           # Hybrid CNN + Transformer + Residual architecture model
├── train.py           # Training pipeline
├── test.py            # Inference and architecture diagram generation
├── vocab.json         # Vocabulary saved during training
└── model.pth          # Trained model weights
```

---

## How It Works

### 1. Dataset Generation

The script `generate_data.py` creates synthetic training examples of system architectures.
Each sample includes:

* Natural language prompt
* List of architecture components (nodes)
* List of connections between components (edges)

Example training sample:

```json
{
  "input": "Design architecture for chat application",
  "nodes": ["User","Gateway","Chat Service","Message Queue","Database"],
  "edges": [
    ["User","Gateway"],
    ["Gateway","Chat Service"],
    ["Chat Service","Message Queue"],
    ["Message Queue","Database"]
  ]
}
```

---

### 2. Model Architecture

The model is built using a hybrid neural architecture:

**Embedding Layer**

* Converts words into vector representations

**CNN Encoder**

* Captures local contextual features from text

**Transformer Attention Layer**

* Learns relationships between words using self-attention

**Residual Block**

* Stabilizes deep network training and improves representation learning

**Output Heads**

* Predict number of nodes
* Predict number of edges

This allows the model to learn patterns between system descriptions and architectural structures.

---

### 3. Training Process

Training is performed using PyTorch.

Steps:

1. Load dataset (`input.json`)
2. Build vocabulary from training prompts
3. Encode text prompts as token sequences
4. Train model using **Mean Squared Error (MSE) loss**
5. Save trained model and vocabulary

Run training:

```
python generate_data.py
python train.py
```

---

### 4. Inference and Diagram Generation

During inference, the user provides a new system description.

Example:

```
Design architecture for chat application
```

The model predicts the expected number of nodes and edges.
A diagram generator then uses Graphviz to create a visual architecture graph.

Run inference:

```
python test.py
```

This generates:

```
architecture_output.png
```

Example architecture structure:

```
User → Gateway → Chat Service → Queue → Database
```

---

## Installation

### Install dependencies

```
pip install torch graphviz
```

For Linux / Colab:

```
apt-get install graphviz
```

---

## Example Output

Input prompt:

```
Design architecture for video streaming platform
```

Model prediction:

```
Predicted nodes ≈ 5
Predicted edges ≈ 4
```

Generated architecture diagram:

```
User → Gateway → Video Service → CDN → Storage
```

Saved as:

```
architecture_output.png
```

---

## Future Improvements

This prototype can be extended significantly. Possible enhancements include:

* Predicting **actual architecture components instead of counts**
* Generating **complete architecture graphs**
* Adding **Graph Neural Network decoders**
* Training on **real system design datasets**
* Supporting **microservices and cloud architectures**
* Generating **multiple diagrams (deployment, sequence, data flow)**

---

## Potential Applications

* AI-assisted **system design tools**
* **Architecture documentation generation**
* **System design interview preparation**
* **Software architecture prototyping**
* AI-powered **developer productivity tools**

---

## License

This project is intended for research and educational purposes.
