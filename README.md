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
