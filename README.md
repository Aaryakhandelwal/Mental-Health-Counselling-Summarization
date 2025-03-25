# Mental Health Summarization

## Dataset

The dataset used in this project consists of therapist-client conversations, providing a rich source of dialogue data for summarization tasks. It includes a total of **190** samples, which are divided into three subsets:

- **Training Set**: 131 samples (70%)
- **Validation Set**: 21 samples (10%)
- **Testing Set**: 39 samples (20%)

Each sample in the dataset contains:
- The full conversation between the therapist and the client.
- Extracted primary and secondary topics relevant to the conversation.
- A corresponding summary that encapsulates the key points of the dialogue.

## Data Preprocessing

The preprocessing step is crucial for transforming raw conversation data into a structured format that can be used for training and evaluating summarization models. The preprocessing script processes CSV files containing therapist-client conversations and performs the following operations:

1. **File Handling**:
   - The script processes all CSV files in the specified folder, reading each file into a DataFrame.

2. **Topic and Summary Extraction**:
   - Extracts the primary topic, secondary topic, and summary from specific rows in the "Utterance" column.
   - If these elements are missing, default values are assigned: "Unknown" for topics and "No summary available" for summaries.

3. **Data Cleaning**:
   - Removes rows that contain the labels "Primary Topic", "Secondary Topic", and "Summary" to focus on the actual dialogue content.

4. **Emotion Processing**:
   - Converts the "Emotion" column to numeric values, handling any non-numeric entries by replacing them with zero.
   - Computes the global emotion score as the mean of the emotion values for each conversation.

5. **Output Formatting**:
   - Writes the processed data to an output file, including:
     - A header with the primary topic, secondary topic, and global emotion score.
     - Each dialogue line with the speaker, dialogue function, sub-topic, emotion, and cleaned utterance.
     - The summary of the conversation.

6. **Output**:
   - The preprocessed data is saved to a specified output file, ready for use in model training and evaluation.

## Methodology

The Mental Health Summarization project aims to develop models that can effectively summarize therapist-client conversations. The methodology involves several key steps:

1. **Data Collection and Preprocessing**:
   - The dataset consists of therapist-client conversations, which are preprocessed to extract primary and secondary topics, as well as summaries.
   - Emotion scores are computed for each conversation to enrich the dataset with additional context.

2. **Model Selection**:
   - Two models were selected for the task: Pegasus and T5. Both models are well-suited for sequence-to-sequence tasks like summarization.

3. **Training**:
   - The models are trained on the preprocessed dataset using a training-validation split.
   - Early stopping is employed to prevent overfitting, with the best model saved based on validation loss.

4. **Evaluation**:
   - The models are evaluated using standard metrics such as ROUGE, BLEU, BERTScore, and BLEURT.
   - These metrics provide insights into the quality of the generated summaries compared to the reference summaries.

## Results

The performance of the Pegasus and T5 models is summarized in the table below:

| Metric    | Pegasus | T5    |
|-----------|---------|-------|
| ROUGE-1   | 28.80   | 35.62 |
| ROUGE-2   | 9.77    | 13.43 |
| ROUGE-L   | 20.88   | 23.91 |
| BLEU      | 4.34    | 5.68  |
| BERTScore | 50.23   | 56.10 |
| BLEURT    | -0.6896 | -0.5381 |

### Analysis

- **ROUGE Scores**: T5 outperforms Pegasus across all ROUGE metrics, indicating better overlap with reference summaries.
- **BLEU Score**: T5 achieves a higher BLEU score, suggesting improved n-gram precision.
- **BERTScore**: T5 also shows a higher BERTScore, reflecting better semantic similarity with reference summaries.
- **BLEURT**: Both models have negative BLEURT scores, but T5 performs slightly better.

These results demonstrate that T5 is more effective for summarizing mental health conversations in this dataset, providing more accurate and semantically relevant summaries.

## How to Run
git clone https://github.com/Dhawz03/Mental-Health-Summarization.git
cd Mental-Health-Summarization
Then run all the cells in the given ipynb file
