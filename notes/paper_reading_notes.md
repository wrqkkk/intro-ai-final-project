# Paper Reading Notes

This file records the representative papers to be read for the academic-track final project.

The notes are intentionally simple. For each topic, the goal is to answer three questions:

1. What is the paper about?
2. What is my understanding of the method?
3. How does this paper support the PCA → AE variants → CNN project?

The final PPT will not become a paper-by-paper literature review. These notes are used as reading anchors behind the method slides.

---

## 1. Representation learning

Paper: **Representation Learning: A Review and New Perspectives**

What the paper is about:

This paper reviews why representation learning matters in machine learning. A good representation can make downstream learning easier by exposing useful explanatory factors in the data.

My understanding:

The key idea is that model performance depends not only on the classifier, but also on how the input data are represented. For high-dimensional exposure data, the original 168-dimensional matrix may contain redundant, correlated, or noisy information. Representation learning tries to transform this matrix into a more useful form.

Connection to this project:

This paper supports the overall framing of the project. The main project question is not only whether a classifier can predict sleep disturbance, but whether PCA and AE-based methods can learn meaningful low-dimensional exposure representations.

---

## 2. PCA

Paper: **Principal Component Analysis review or Jolliffe-style PCA reference**

What the paper is about:

PCA is a classical linear dimensionality-reduction method. It projects high-dimensional data onto orthogonal directions that explain the largest amount of variance.

My understanding:

PCA is useful because it provides a stable and interpretable baseline. However, PCA optimizes variance explanation in the input X, not prediction of the outcome Y. Therefore, high explained variance does not necessarily imply strong sleep disturbance classification.

Connection to this project:

PCA is used as the linear baseline for the 168-dimensional exposure matrix. It answers whether the exposure matrix contains a strong low-dimensional linear structure. It also provides a comparison point for nonlinear AE-based reconstruction.

---

## 3. Autoencoder

Paper: **Reducing the Dimensionality of Data with Neural Networks**

What the paper is about:

This paper shows that neural networks can be used for nonlinear dimensionality reduction. An autoencoder learns an encoder that compresses the input into a low-dimensional code and a decoder that reconstructs the original input.

My understanding:

Autoencoder can be seen as a nonlinear alternative to PCA. The encoder learns a latent representation, and the decoder forces this representation to retain enough information to reconstruct the input. However, the reconstruction objective is not the same as the classification objective.

Connection to this project:

Ordinary AE is used to test whether nonlinear representation learning can preserve the exposure matrix better than PCA. Previous experiments suggest that AE can reduce reconstruction error substantially, but stronger reconstruction does not automatically lead to stronger sleep disturbance prediction.

---

## 4. Variational Autoencoder

Paper: **Auto-Encoding Variational Bayes**

What the paper is about:

This paper introduces Variational Autoencoder, which extends the autoencoder idea by learning a probabilistic latent representation. Instead of mapping each sample to a fixed latent vector, VAE maps it to a latent distribution.

My understanding:

VAE adds a probabilistic structure to representation learning. Its loss contains a reconstruction term and a regularization term that encourages the latent distribution to stay close to a prior distribution. This makes VAE useful for thinking about uncertainty in latent representation.

Connection to this project:

VAE is treated as an AE-family extension rather than the main project line. It helps explain how representation learning can move from deterministic compression to probabilistic latent modeling. In the current project, the main experimental discussion remains PCA, AE variants, and CNN.

---

## 5. CNN / Deep learning

Paper: **Deep Learning** or a representative CNN review

What the paper is about:

Deep learning methods learn hierarchical representations from data. CNNs use convolutional filters to capture local patterns in structured inputs.

My understanding:

CNNs are powerful when the input has meaningful local structure. In images, nearby pixels have natural spatial relationships. In this project, the exposure matrix is organized as 21 exposure markers by 8 exposure windows. This gives a possible matrix structure, but the local-neighborhood assumption is not as automatic as in image data.

Connection to this project:

CNN is used to test whether the 21 × 8 exposure matrix structure contains classification-relevant local patterns. The previous CNN results are important because they show that exposure-only CNN classification is weak, while covariates provide stronger prediction signal.

---

## 6. Optional: Transformer / Attention

Paper: **Attention Is All You Need**

What the paper is about:

This paper introduces the Transformer architecture based on self-attention. Instead of relying on recurrence or convolution, self-attention allows each token to attend to other tokens directly.

My understanding:

Attention can be understood as a learnable information-retrieval mechanism. Query and key determine how strongly one position should attend to another, while value carries the information being aggregated.

Connection to this project:

Transformer is only an optional future extension. If there is more time, the exposure-window matrix could be converted into tokens, and self-attention could be used to learn global dependencies across exposure markers and time windows. This does not replace the current PCA → AE variants → CNN main line.

---

## 7. Optional: AI-assisted research reflection

Paper: **Intention Is All You Need**

What the paper is about:

This paper discusses the role of human intention in the age of generative AI and AI-assisted programming. It questions the idea that natural-language intention can be directly converted into reliable software without human judgment.

My understanding:

AI can help generate code, organize notes, and explain methods, but it cannot replace the human responsibility of defining the problem, checking the output, and deciding whether a result is meaningful.

Connection to this project:

This supports the final reflection slide. In this project, AI is used to assist paper reading, project organization, and method explanation. However, the key decisions about data confidentiality, model interpretation, and final conclusions remain human judgments.
