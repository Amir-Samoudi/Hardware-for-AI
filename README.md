# Hardware for AI Projects

This repository contains a series of projects from the **"Hardware for AI"** course. The projects explore the end-to-end process of designing, optimizing, and deploying neural networks for resource-constrained hardware, such as embedded systems.

---

## Topics Covered
- **AI Basics:** Foundational concepts of neural networks and deep learning.  
- **Model Optimization:** Techniques like pruning and quantization to reduce model size and computational complexity.  
- **Model Deployment & Integration:** Converting trained models into formats suitable for low-level implementation.  
- **Hardware Acceleration:** Implementing and evaluating models on embedded systems using C.  
- **Case Studies & Practical Projects:** Hands-on application of theoretical concepts.

---

## Projects

### Project 1: Efficient CNN Implementation for CIFAR-10
- **Goal:** Design a Convolutional Neural Network (CNN) for the CIFAR-10 dataset with a strict model size constraint of less than 7 MB, while maximizing accuracy.  
- **Description:**  
  A custom CNN with 6 convolutional layers was designed and trained from scratch. Through careful architectural choices and training strategies, the final model achieved a **test accuracy of 88.4%** with a compact size of only **4.5 MB**, successfully meeting the project requirements.

---

### Project 2: Model Compression via Pruning Techniques
- **Goal:** Reduce the parameter count of the CNN from Project 1 using various pruning methods and analyze the trade-offs.  
- **Description:**  
  Explored both **structured and unstructured pruning**. Compared:
  - **One-shot pruning:** remove weights all at once.  
  - **Iterative pruning:** remove weights gradually over several steps with fine-tuning in between.  

  Different compression rates were tested to evaluate the trade-offs between **model size reduction** and **performance degradation**.

---

### Project 3: Model Compression via Quantization
- **Goal:** Further reduce the model's memory footprint by applying quantization to both the original and pruned models.  
- **Description:**  
  Implemented **LSQ+ (Learned Step Size Quantization)** to quantize both weights and activations.  
  Custom `QuantConv2D` and `QuantLinear` classes were created to replace standard layers.  
  Applied this technique to:
  - The base model from Project 1 (testing various bit-lengths).  
  - The best pruned model from Project 2, analyzing combined effects.  

  This allowed a thorough exploration of **accuracy vs. model size trade-offs** to find the optimal combination of optimization techniques.

---

### Project 4: Low-Level C Implementation for Embedded Systems
- **Goal:** Prepare the optimized models for deployment on embedded systems by converting them to low-level C code and evaluating performance.  
- **Description:**  
  - Converted trained PyTorch models (including quantized versions) to **ONNX** format.  
  - Used **ONNX2C** to generate equivalent C code.  
  - Verified correctness by running inference on test images.  
  - Evaluated key performance metrics:
    - Execution Time  
    - Memory Footprint  
    - Memory Accesses (Read/Write)  

  This analysis helped identify computational bottlenecks and areas for acceleration with dedicated hardware.
