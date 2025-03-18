# Enhancing GPT-Neo Performance: Hybrid Fine-Tuning and Quantization

This research project implements a hybrid optimization methodology that progressively refines model efficiency through fine-tuning and quantization strategies, ensuring optimal balance between performance and resource utilization.

**This project was a collaborative effort by Team Matrix, consisting of three team members:**
1. Owais Hussain: [GitHub](https://github.com/owais-syed) , [LinkedIn](https://www.linkedin.com/feed/)
2. Jyothindra Pallikonda: [Git Hub](https://github.com/jyothindrapallikonda)  , [Linkedin](https://www.linkedin.com/in/jyothindrapallikonda/) 
3. Minorah Palli: [GitHub](https://github.com/Minorah-7)  , [Linkedin](https://www.linkedin.com/in/minorah-palli-01b286266?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app)

## Project Overview
This project focuses on optimizing the EleutherAI GPT-Neo 1.3B model for a text summarization task using the CNN/DailyMail dataset. The goal is to enhance efficiency by reducing inference time and memory usage while maintaining or improving accuracy. We explore various optimization techniques, including LoRA fine-tuning and quantization, and compare their performance to determine the best approach for real-world deployment.

# Step 1: Benchmarking the Base Model

In this step, we benchmark the performance of the EleutherAI GPT-Neo 1.3B model on a text summarization task using the CNN/DailyMail dataset. The approach involves measuring inference time, memory usage, and ROUGE score on a CPU setup before applying any optimizations. We load the model and tokenizer, process a sample article, generate a summary, and track performance metrics to establish a baseline.

The results from this benchmarking serve as a reference for evaluating future optimizations. By understanding the initial performance, we can measure improvements in efficiency and accuracy as we implement techniques like quantization and LoRA fine-tuning in the next steps.

### Benchmark Results (CPU)
- **Inference Time:** 92.58 seconds
- **Memory Used:** 7288.12 MB
- **ROUGE Score:**
  - ROUGE-1: 0.0948
  - ROUGE-2: 0.0552
  - ROUGE-L: 0.0795
  - ROUGE-Lsum: 0.0826

# Step 2: Applying LoRA Fine-Tuning and Benchmarking

In this step, we optimize the model using LoRA (Low-Rank Adaptation) fine-tuning. We adjust the rank, dropout, and scaling parameters to enhance efficiency. The goal is to reduce inference time while maintaining or improving the model's performance.

### Benchmark Results (Optimized Model) - Approach 1
- **Inference Time:** 208.19 seconds
- **Memory Used:** 5861.79 MB
- **ROUGE Score:**
  - ROUGE-1: 0.1258
  - ROUGE-2: 0.0758
  - ROUGE-L: 0.0964
  - ROUGE-Lsum: 0.0964

### Benchmark Results (Optimized Model) - Approach 2
- **Inference Time:** 46.26 seconds
- **Memory Used:** 8698.58 MB
- **ROUGE Score:**
  - ROUGE-1: 0.2895
  - ROUGE-2: 0.1733
  - ROUGE-L: 0.2632
  - ROUGE-Lsum: 0.2632

The results indicate that Approach 2 significantly improves inference time and accuracy at the cost of higher memory usage. However, the increased memory usage presents a drawback, so we will be moving to Step 3 to explore quantization techniques to further optimize performance while reducing memory consumption.

# Step 3: Implementing Quantization for Optimization

In this step, we incorporate quantization techniques to optimize the model further. We experiment with FP16 precision to balance performance and memory efficiency. The primary objective is to reduce memory usage while maintaining acceptable inference speed and accuracy.

### Benchmark Results (Optimized Model) - Approach 3
- **Inference Time:** 319.27 seconds
- **Memory Used:** 4761.81 MB
- **ROUGE Score:**
  - ROUGE-1: 0.0948
  - ROUGE-2: 0.0552
  - ROUGE-L: 0.0795
  - ROUGE-Lsum: 0.0826

This approach successfully reduces memory consumption but comes at the expense of increased inference time. Further optimizations will be explored to balance both aspects effectively.

# Step 4: Hybrid Approach - Combining LoRA and Quantization

To achieve an optimal balance between inference time, memory efficiency, and accuracy, we combine LoRA fine-tuning with quantization. This hybrid approach leverages the benefits of LoRA’s accuracy improvements while utilizing quantization to reduce memory consumption.

### Benchmark Results (Optimized Model) - Approach 4
- **Inference Time:** 78.42 seconds
- **Memory Used:** 5289.56 MB
- **ROUGE Score:**
  - ROUGE-1: 0.2154
  - ROUGE-2: 0.1387
  - ROUGE-L: 0.1986
  - ROUGE-Lsum: 0.1986

The results indicate that this approach significantly reduces inference time compared to quantization alone while also improving memory efficiency compared to LoRA-only methods. This makes it a more practical choice for real-world applications.

# Conclusion

The optimization techniques explored present trade-offs between inference time, memory usage, and accuracy. The hybrid approach (LoRA + Quantization) provides the best balance, making it a viable solution for efficient model deployment.

# Comparison Table

| Approach | Inference Time (s) | Memory Used (MB) | ROUGE-1 | ROUGE-2 | ROUGE-L | ROUGE-Lsum | Best Use Case |
|----------|------------------|----------------|---------|---------|---------|------------|---------------|
| Baseline (CPU) | 92.58 | 7288.12 | 0.0948 | 0.0552 | 0.0795 | 0.0826 | Reference Benchmark |
| LoRA - Approach 1 | 208.19 | 5861.79 | 0.1258 | 0.0758 | 0.0964 | 0.0964 | Balanced Performance |
| LoRA - Approach 2 | 46.26 | 8698.58 | 0.2895 | 0.1733 | 0.2632 | 0.2632 | High Accuracy |
| Quantization | 319.27 | 4761.81 | 0.0948 | 0.0552 | 0.0795 | 0.0826 | Low Memory Usage |
| Hybrid (LoRA + Quantization) | 78.42 | 5289.56 | 0.2154 | 0.1387 | 0.1986 | 0.1986 | Best Overall Balance |

This table provides a clear comparison of the different approaches, highlighting their impact on performance and efficiency.

# Next Steps

Moving forward, additional techniques such as pruning and knowledge distillation could be explored to further enhance model efficiency. Implementing distributed inference strategies might also provide improvements for real-world deployment scenarios.
