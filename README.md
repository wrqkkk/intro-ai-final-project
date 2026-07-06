# Intro to AI Final Project

## Project title

**High-dimensional environmental exposure representation learning and health prediction: PCA, Autoencoder variants, and CNN-based classification**

中文题目：**高维环境暴露数据的表征学习与健康预测：PCA、AE 变体与 CNN 分类比较**

## Project type

This is an **academic-track** final project for the Introduction to Artificial Intelligence course.

The project does not aim to build a commercial AI application. Instead, it focuses on understanding and comparing several AI / machine learning methods for representing high-dimensional data.

## Core question

The original research setting contains a high-dimensional environmental exposure matrix with:

- 21 environmental exposure markers;
- 8 exposure windows;
- 168 exposure features in total;
- a binary sleep disturbance outcome used for downstream classification validation.

The central question is:

**Can low-dimensional representations learned from high-dimensional exposure data preserve exposure structure, and can such representations be translated into sleep disturbance classification signal?**

This project separates two related but different tasks:

**Representation validation:** whether PCA and Autoencoder-based models can reconstruct or recover the original exposure matrix.

**Classification validation:** whether the learned exposure representation helps predict sleep disturbance, especially compared with covariate-only and fusion models.

## Main methods

The project focuses on three method families:

**PCA** is used as a linear dimensionality-reduction baseline. It tests whether the exposure matrix contains a strong low-dimensional linear structure.

**Autoencoder variants** are used for nonlinear representation learning. Ordinary AE, Sparse AE, and Masked AE are discussed as different ways of learning or validating exposure structure.

**CNN-based classification** is used to test whether the matrix structure of the exposure data can provide useful information for downstream sleep disturbance prediction.

Variational Autoencoder and Transformer / attention are treated as optional extensions rather than the main project line.

## Repository contents

This repository will contain:

- `docs/final_ppt_outline.md`: the planned structure of the final PPT presentation;
- `notes/paper_reading_notes.md`: concise reading notes for representative papers behind each method;
- `data/README_data_confidentiality.md`: explanation of why the original data are not included;
- selected non-identifiable presentation materials and summary-level results to be added later.

## Data availability

The original dataset used in the previous experiments is confidential and cannot be uploaded to GitHub. This repository does not contain raw individual-level data, identifiable information, or confidential file paths.

The repository is used only to document the project logic, AI methods, paper-reading process, and final presentation structure.

## Planned final output

The final submission will mainly include:

- a PPT presentation;
- concise paper reading notes;
- a short project documentation file;
- selected aggregate-level experimental summaries and figures if they do not contain confidential information;
- optional code or notebook excerpts if they are safe to share.
