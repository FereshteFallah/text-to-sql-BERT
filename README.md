# 🎯 Main Goal of Using BERT:

Our main idea was to use BERT for question type detection.  
For example:

- **"What is the age of Alice?"** → Question Type: `AGE_QUERY`  
- **"What is the grade of Bob?"** → Question Type: `GRADE_QUERY`  
- **"Show all students."** → Question Type: `LIST_QUERY`  

## ⚙️ How Can BERT Help?

The BERT model can learn from various question examples and classify the type of question.  
In general, BERT's role here is as follows:

- **Input:** Textual question (e.g., "What is the age of Alice?")  
- **Output:** Classify the question into a specific type (e.g., "AGE_QUERY")  

Then, based on this type, we generate an appropriate SQL query:

- **AGE_QUERY** → `SELECT age FROM students WHERE name = ?`  
- **GRADE_QUERY** → `SELECT grade FROM students WHERE name = ?`  
- **LIST_QUERY** → `SELECT * FROM students`

---

## 📝 How Do We Do This?

Now, I want to extend the previous code with the real BERT model and add the following steps:

### 1️⃣ Training Data:
A list of questions with their corresponding question types to train the BERT model:

```python
training_data = [
    ("What is the age of Alice?", "AGE_QUERY"),
    ("What is the grade of Bob?", "GRADE_QUERY"),
    ("Show all students.", "LIST_QUERY"),
    ("Who is older than 20?", "AGE_COMPARISON"),
    ("List all students with grade A.", "GRADE_FILTER")
]
```
### 2️⃣ Fine-tuning BERT:
We fine-tune the BERT model with this data to learn how to map textual questions to the correct type.

### 3️⃣ Converting Question Type to SQL:
Once BERT predicts that the question type is, for example, AGE_QUERY, we automatically generate the appropriate SQL query.
### 🔧 Requirements

- Python 3.x
- transformers library for BERT
- torch (PyTorch) for model training
- sqlite3 for database management
