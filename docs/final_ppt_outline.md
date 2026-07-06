# Final PPT Outline

Project title: **High-dimensional environmental exposure representation learning and health prediction: PCA, Autoencoder variants, and CNN-based classification**

中文题目：**高维环境暴露数据的表征学习与健康预测：PCA、AE 变体与 CNN 分类比较**

Project type: **Academic track**

The final presentation will focus on the PCA → AE variants → CNN line. VAE, Transformer, and AI-intention discussions are optional or reflective extensions, not the main experimental line.

---

## Slide 1. Title

Introduce the project title, course, student information, and academic-track positioning.

Core message: this is a method-centered AI project, not a commercial application demo.

---

## Slide 2. Background: high-dimensional environmental exposure matrix

Explain the data structure used in the previous experiments:

- 21 environmental exposure markers;
- 8 exposure windows;
- 168 exposure features in total;
- binary sleep disturbance outcome used for downstream validation.

Core message: the 21 × 8 exposure matrix creates a representation learning problem.

---

## Slide 3. Core question: representation vs classification

Separate two questions:

**Representation validation:** Can low-dimensional models preserve or recover the exposure matrix structure?

**Classification validation:** Can the learned exposure representation help predict sleep disturbance?

Core message: learning exposure structure and predicting sleep disturbance are related but not identical tasks.

---

## Slide 4. Overall pipeline: PCA → AE variants → CNN

Show the project workflow:

Exposure matrix X → PCA / Ordinary AE / Sparse AE / Masked AE → low-dimensional representation or reconstructed exposure matrix → CNN / classifier → classification metrics.

Also mention the covariate branch as an important comparison:

Exposure-only model vs covariate-only model vs fusion model.

---

## Slide 5. PCA method: linear dimensionality-reduction baseline

Explain PCA as the linear baseline.

Key points:

- PCA searches for orthogonal directions that explain the largest variance in X;
- it is stable and interpretable;
- it tests whether the exposure matrix has a low-dimensional linear structure;
- it does not directly optimize sleep disturbance prediction.

Reading anchor: PCA review or Jolliffe-style PCA reference.

---

## Slide 6. PCA experimental evidence

Use the previous PCA results.

Suggested content:

- PCA z4 / z8 / z16 explained variance;
- PCA reconstruction MSE;
- PCA as a strong but limited linear baseline.

Interpretation:

PCA demonstrates that the exposure matrix contains a strong low-dimensional linear component, but PCA scores alone are not sufficient for strong sleep disturbance discrimination.

---

## Slide 7. Autoencoder method: nonlinear reconstruction-based representation learning

Explain ordinary Autoencoder.

Key points:

- encoder maps X to a low-dimensional latent representation z;
- decoder reconstructs X from z;
- reconstruction loss encourages z to preserve exposure structure;
- AE is a nonlinear extension of dimensionality reduction;
- good reconstruction does not necessarily imply good outcome prediction.

Reading anchor: Hinton & Salakhutdinov, *Reducing the Dimensionality of Data with Neural Networks*.

---

## Slide 8. Ordinary AE and Sparse AE experimental evidence

Use previous AE and Sparse AE results.

Suggested content:

- AE / Sparse AE reconstruction MSE compared with PCA;
- sparse penalty effect on latent magnitude;
- caution that current Sparse AE is closer to shrinkage-regularized AE than hard sparse representation.

Interpretation:

AE variants preserve exposure structure better than PCA at the same latent dimension, but stronger reconstruction does not automatically create stronger sleep-outcome classification signal.

---

## Slide 9. Masked AE method: cross-window recovery

Explain Masked AE.

Key points:

- mask one exposure window;
- reconstruct the full exposure vector;
- evaluate the recovery MSE on the masked window;
- this tests whether different exposure windows contain learnable cross-window dependency.

Core message: Masked AE is a stronger validation of exposure structure than ordinary reconstruction, because the model must infer missing window information from the remaining windows.

---

## Slide 10. Masked AE experimental evidence

Use previous Masked AE results.

Suggested content:

- masked PCA recovery MSE vs best Masked AE recovery MSE;
- model capacity trend;
- zero-mask vs indicator-mask observations if needed.

Interpretation:

Masked AE provides strong evidence that cross-window exposure structure is learnable and contains nonlinear information beyond the linear PCA baseline.

---

## Slide 11. CNN method: matrix structure and classification

Explain why CNN is considered.

Key points:

- the exposure data can be reshaped into a 21 × 8 matrix;
- CNN assumes local structure in the matrix;
- convolution may capture local marker-window patterns;
- this assumption is not as natural as image pixels, so it must be experimentally tested.

Reading anchor: Deep learning / CNN review.

---

## Slide 12. CNN experimental evidence

Use previous CNN results.

Suggested content:

- exposure-only CNN;
- covariate-only model;
- exposure + covariate fusion model;
- runtime and performance comparison if useful.

Interpretation:

Exposure-only CNN classification is weak, while covariates provide stronger prediction signal. Fusion has limited additional gain over covariate-only models.

---

## Slide 13. Method comparison matrix

Compare PCA, Ordinary AE, Sparse AE, Masked AE, CNN, and optional Transformer.

Suggested columns:

- objective;
- representation form;
- inductive bias;
- strength;
- limitation;
- role in this project.

Core message: the project is not simply stacking models; it compares different assumptions about how high-dimensional data can be represented.

---

## Slide 14. Code structure and data confidentiality

Explain the GitHub repository structure and data boundary.

Key points:

- real data are confidential and not uploaded;
- the repository documents methods, notes, PPT structure, and safe aggregate results;
- no raw individual-level data or confidential file paths are included.

Core message: the project is reproducible at the level of method logic and presentation materials, while respecting data confidentiality.

---

## Slide 15. Synthesis: why complex models do not necessarily win

Discuss the central interpretation.

Core message:

AE and Masked AE can learn exposure structure very well, but exposure-structure learning and outcome-discriminative prediction are different goals.

More complex models do not automatically improve classification if the input exposure representation contains weak or indirect sleep-outcome signal.

---

## Slide 16. AI-assisted research reflection and conclusion

Explain how AI was used.

Suggested points:

- AI helped structure paper reading notes;
- AI helped organize project logic and presentation materials;
- AI helped clarify code and method explanations;
- human judgment remained necessary for problem definition, model selection, result interpretation, and data confidentiality decisions.

Final message:

Machine learning models learn representations from data; researchers still need to preserve intention, judgment, and responsibility.

---

## Optional appendix. Transformer / attention as future work

If time allows, add one appendix slide based on *Attention Is All You Need*.

Possible idea:

Future work could treat each exposure-window unit as a token and use self-attention to learn global dependencies across exposure markers and time windows.

This is optional and does not replace the PCA → AE variants → CNN main line.
