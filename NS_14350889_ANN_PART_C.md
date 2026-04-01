## 1. Which model performed better and why?

The **Improved MLP from Part A** performed better overall than the GenAI-guided model from Part B. Although the **Baseline MLP** achieved the highest raw accuracy, the **Improved MLP** was the strongest model when judged using the more meaningful metrics for this imbalanced dataset, especially **recall, F1-score, balanced accuracy, ROC-AUC, and PR-AUC**. This made it the most effective model for identifying the minority **“yes”** class, which was a more important goal than simply maximising accuracy.

The GenAI-guided Advanced MLP produced a competitive result and achieved high recall, but it did not surpass the Improved MLP. It generated more **false positives**, had a slightly lower **F1-score**, lower **balanced accuracy**, and weaker performance in the ambiguity analysis. This suggests that while the GenAI model was capable, the independently developed Improved MLP achieved a better overall balance between detecting positive cases and maintaining reliable classification performance. In other words, the best model was not the one with the most complex label or the most AI involvement, but the one that handled the dataset most effectively in practice.

## 2. How did your independent thinking compare to GenAI assistance?

My independent thinking was more effective in producing the strongest final model, while GenAI assistance was more useful for expanding ideas and structuring the experimentation process. In Part A, I developed the earlier models through my own decisions, including the progression from a simple SLP to a baseline MLP and then to an Improved MLP with dropout and class weighting. This process helped me understand how architecture choices affected recall, false positives, and the balance between overall accuracy and minority-class detection.

In Part B, Generative AI was useful because it suggested a more advanced architecture and highlighted ideas such as **batch normalization, learning-rate reduction, broader evaluation metrics, and probability-based ambiguity analysis**. These suggestions helped make the Part B model more structured and academically grounded. However, GenAI did not automatically produce a better outcome. My own judgement was still needed to decide which suggestions were appropriate, which ones should be rejected, and how the final comparison should be interpreted. This showed me that independent thinking remained the more important factor, while GenAI worked better as a supporting tool.

## 3. Did AI miss anything important or surprise you?

Yes, AI did miss some important things, and it also produced one useful surprise. The main limitation was that the AI suggestions were quite generic at first. They were helpful in recommending standard ANN improvements, but they did not automatically understand the specific trade-offs in this dataset, especially the problem of increasing **false positives** when trying to improve recall. That was something I had to identify myself through the confusion matrices, the classification reports, and the ambiguity analysis.

Another limitation was that AI could suggest techniques that sound advanced but are not necessarily suitable, such as overly deep architectures or methods that would reduce fairness when comparing with Part A. These ideas still needed to be filtered critically. The surprising part was that AI did help organise the modelling process well by suggesting a sensible architecture and by reinforcing the need for multiple evaluation metrics beyond accuracy. So AI was helpful in expanding the search space, but it was not strong enough to replace dataset-specific reasoning.

## 4. How would you balance AI assistance vs critical thinking in future tasks?

In future tasks, I would use AI at the **idea-generation and planning stage**, but I would rely on critical thinking for the final decisions. AI is useful for quickly suggesting architectures, tuning options, evaluation metrics, and alternative approaches that I may not think of immediately. It can save time and help make the workflow more structured. However, I would not treat AI output as the final answer.

The most important part of model development is still testing, interpreting results, and understanding the dataset. In this project, the final evidence showed that the best model came from my own modelling decisions rather than the AI-guided version. Because of that, I would use AI as a brainstorming and support tool, but I would always keep human judgement in control. The best balance is to let AI suggest possibilities, while critical thinking decides what is actually valid, fair, and effective.

