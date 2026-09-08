# 🧠 Teaching a Computer to See — From Absolute Zero

> *No TensorFlow. No PyTorch. No magic black boxes. Just Python, NumPy, and the raw mathematics that powers modern AI.*

---

## What Is This?

Imagine you've seen the digit **"3"** written thousands of times in your life — on receipts, textbooks, clocks. Without thinking, your brain just *knows* what a 3 looks like.

But how would you teach that to a computer that only understands numbers?

That's exactly what this project does. We built a **neural network from absolute scratch** — no deep learning frameworks, no shortcuts — that learns to read handwritten digits with **~98% accuracy**. Every single mathematical operation is written by hand in pure Python and NumPy.

This is not a tutorial on how to *use* AI. This is a dissection of how AI *actually works*.

---

## The Challenge: MNIST

We used the **MNIST dataset** — 70,000 handwritten digit images (0–9), each one a 28×28 pixel grid. It's the "Hello World" of machine learning, and it's the perfect proving ground.

```
Training images:   55,000
Validation images:  5,000
Test images:       10,000
Final Accuracy:     ~98.3%
```

Every pixel is just a number between 0 and 255. Our network's job: look at 784 numbers, and figure out which digit they represent.

---

## How Does a Neural Network Actually Learn?

Think of it like this.

You hire a new employee who has never seen numbers before. On day one, they're just guessing. They see a handwritten "7" and say "I think that's a 4." Wrong. You tell them. They adjust their thinking slightly.

You show them another image. Wrong again. They adjust again.

After seeing tens of thousands of examples — and being corrected each time — they get remarkably good. That's *literally* what's happening inside this code. The "adjustments" are calculated using something called **backpropagation**, and the "getting better" is called **gradient descent**.

---

## What's Built From Scratch

Every component below was written by hand — no library did the heavy lifting:

| Component | What it does |
|-----------|-------------|
| **Forward Propagation** | Passes data through the network to make a prediction |
| **Backpropagation** | Figures out who's to blame for a wrong answer |
| **Gradient Descent (Adam)** | Adjusts the network so it does better next time |
| **ReLU & Softmax** | Activation functions that add intelligence to each layer |
| **Batch Normalization** | Keeps the network stable during training |
| **Dropout** | Randomly disables neurons so the network doesn't cheat |
| **L1 & L2 Regularization** | Prevents the network from memorizing instead of learning |
| **He Initialization** | Smart weight setup so training doesn't collapse on day one |
| **Cross-Entropy Loss** | Measures exactly how wrong each prediction is |

---

## The Architecture

```
Input Layer        Hidden Layer 1     Hidden Layer 2     Output Layer
784 neurons   →   256 neurons    →   128 neurons    →   10 neurons
(pixels)          (ReLU + BN)        (ReLU + BN)        (Softmax)
                  (Dropout 20%)      (Dropout 20%)      (one per digit)
```

The output layer has 10 neurons — one for each digit 0–9. Whichever neuron fires strongest is the network's prediction. The final output is a **probability distribution**: the network doesn't just say "that's a 3" — it says "I'm 94.7% sure that's a 3, 3.1% sure it's an 8, 1.2% sure it's..."

---

## Results

After 20 epochs of training on 55,000 images:

```
Train Accuracy:       99.41%
Validation Accuracy:  98.26%
```

The gap between train and validation accuracy is only ~1.1% — a sign that the network is genuinely *learning* patterns, not just memorizing the training data.

---

## Why Build It From Scratch?

Because using TensorFlow is like driving a car without knowing how an engine works. You can get places, but you don't *understand* anything.

Building from scratch means:
- You know exactly why the network learns
- You know what breaks when it doesn't
- You understand what every hyperparameter actually does
- You can debug anything because there's no black box

This project covers every concept that makes modern deep learning work — the same fundamentals that power GPT, image recognition systems, and self-driving cars.

---

## Topics Covered

This project was built as a capstone covering:

- ✅ Vanishing & Exploding Gradient Problems
- ✅ Gradient Descent — Batch, Stochastic, Mini-Batch
- ✅ Activation Functions — Sigmoid, Tanh, ReLU, Leaky ReLU, ELU, SELU
- ✅ Weight Initialization — Xavier/Glorot & He
- ✅ Batch Normalization
- ✅ Dropout Regularization
- ✅ L1 & L2 Regularization
- ✅ Adam Optimizer

---

## Getting Started

**1. Clone the repo**
```bash
git clone https://github.com/YOUR_USERNAME/ann-from-scratch.git
cd ann-from-scratch
```

**2. Install dependencies**
```bash
pip install numpy matplotlib scikit-learn
```

**3. Launch the notebook**
```bash
jupyter notebook ANN_from_scratch.ipynb
```

Run the cells top to bottom. Training takes a few minutes depending on your machine.

---

## Project Structure

```
ann-from-scratch/
│
└── ANN_from_scratch.ipynb    # Complete notebook — all code and explanations
```

---

## Dependencies

| Library | Version | Purpose |
|---------|---------|---------|
| `numpy` | ≥ 1.21 | All matrix operations |
| `matplotlib` | ≥ 3.4 | Plotting curves and predictions |
| `scikit-learn` | ≥ 0.24 | Fetching the MNIST dataset |

No TensorFlow. No PyTorch. No Keras. That's the whole point.

---

## A Note on What "From Scratch" Means

Some people build "from scratch" and then import a `Dense` layer from Keras. That's not what happened here.

Every matrix multiplication, every gradient calculation, every parameter update — written explicitly. If you open this notebook and search for `import`, you'll find exactly three lines. That's it.

---

*Built with NumPy and stubbornness.*
