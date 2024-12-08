
# Named Entity Recognition (NER) Pipeline Report

## **Problem Statement**
The objective of this project is to implement a Named Entity Recognition (NER) pipeline using a transformer-based model. The pipeline extracts structured information, such as:
- Person Names
- Skills
- Educational Qualifications
- Work Experience
- Dates

This NER system aims to assist HR professionals in quickly screening resumes by automating the extraction of key information.

---

## **Model Selection**
### **Selected Model: `dbmdz/bert-large-cased-finetuned-conll03-english`**

- **Reason for Selection:**
  - **Pre-trained Dataset:** This model is fine-tuned on the CoNLL-2003 dataset, which is widely used for NER tasks, making it highly relevant for our use case.
  - **Architecture:** BERT is a transformer-based model that excels in sequence labeling tasks like NER. The `bert-large-cased` variant provides better contextual understanding due to its large architecture.
  - **Performance Metrics:** According to the model’s Hugging Face documentation, it achieves high F1 scores on NER tasks, making it a reliable choice.

---

## **Dataset**
- **Dataset Used:** CoNLL-2003
  - This dataset contains labeled data for NER, including tokens, part-of-speech tags, and named entity tags.
- **Structure:**
  - Features include `tokens`, `pos_tags`, `chunk_tags`, and `ner_tags`.
  - `ner_tags` provide labels for entities like Person (`PER`), Organization (`ORG`), Location (`LOC`), and Miscellaneous (`MISC`).

---

## **Pipeline Implementation**
### **Steps Taken:**
1. **Dataset Loading:**
   - The CoNLL-2003 dataset was loaded using the Hugging Face `datasets` library.
   - The dataset structure was explored to understand its features.

2. **Model and Tokenizer Loading:**
   - The model and tokenizer were loaded using Hugging Face’s `AutoModelForTokenClassification` and `AutoTokenizer`.

3. **NER Pipeline Creation:**
   - An NER pipeline was created using Hugging Face’s `pipeline` API with the loaded model and tokenizer.
   - Aggregation strategy (`simple`) was applied to combine overlapping entities.

4. **Sample Testing:**
   - A sample resume text was provided to the pipeline, and entities such as names, organizations, and skills were accurately extracted.



---

## **Results**
- Extracted Entities from Sample Text:
  - **Person Name:** John Doe
  - **Skill:** Python, Machine Learning
  - **Organization:** Stanford University, Google

These results demonstrate the effectiveness of the pipeline in identifying key entities from resumes.

---

## **Post-Processing (Future Scope)**
- Extracted entities can be formatted into JSON or CSV for easy integration into databases.
- Example JSON output:
  ```json
  {
      "entities": [
          {"type": "PER", "text": "John Doe", "confidence": 1.0},
          {"type": "ORG", "text": "Google", "confidence": 1.0}
      ]
  }
  ```

---

## **Conclusion**
The project successfully implements an NER pipeline capable of extracting structured information from resumes. With additional steps like fine-tuning, performance evaluation, and post-processing, the solution can be further optimized for real-world applications.
