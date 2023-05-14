This script is designed to extract soft and hard skills from text data (e.g., CVs or resumes) using pre-trained models from the HuggingFace Model Hub and is compatible with Jupyter Notebook and Python 3.10.1. The script uses two transformer-based models to perform this task:

1. [Soft skills extraction](https://huggingface.co/jjzha/jobbert_skill_extraction)
2. [Hard/Knowledge skills extraction](https://huggingface.co/jjzha/jobbert_knowledge_extraction)

The extracted skills are stored in a pandas DataFrame and saved as a CSV file.

# Setup
To set up a virtual environment for this project, follow these steps:

`python -m venv my_env`

`.\my_env\Scripts\activate` 

# Installation
To install the necessary dependencies, run the following commands:
pip install -r requirements.txt

# Usage
The script expects an input DataFrame 'df' with a column named 'text', which contains the text data from which to extract skills.

# Output
The script outputs a DataFrame 'out_df' with two new columns: 'soft_skills' and 'hard_skills'. Each of these columns contains a list of the respective skills extracted from the text data. The DataFrame is then saved to a CSV file located at './output/cv_classified.csv'.

# Functions
aggregate_skill_span(results): This function aggregates consecutive classified entities into one. It also removes invalid skills that are one character and non-alphabetic.

extract_skill_entities(text): This function extracts both soft and hard skills from the provided text.

# Customization
You can adjust the threshold for accepting a skill by changing the score_thres variable. It's set to 0.5 by default.

For debugging purposes, there is a flag print_debug. If set to True, the script prints the extracted skills for each CV.

# Note
This script requires a pandas DataFrame 'df' with a column 'text' as input. Make sure your text data is correctly loaded into 'df'. The script handles exceptions related to missing or incompatible data.

# Reference
@inproceedings{zhang-etal-2022-skillspan,
    title = "{S}kill{S}pan: Hard and Soft Skill Extraction from {E}nglish Job Postings",
    author = "Zhang, Mike  and
      Jensen, Kristian N{\o}rgaard  and
      Sonniks, Sif  and
      Plank, Barbara",
    booktitle = "Proceedings of the 2022 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies",
    month = jul,
    year = "2022",
    address = "Seattle, United States",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2022.naacl-main.366",
    pages = "4962--4984",
    abstract = "Skill Extraction (SE) is an important and widely-studied task useful to gain insights into labor market dynamics. However, there is a lacuna of datasets and annotation guidelines; available datasets are few and contain crowd-sourced labels on the span-level or labels from a predefined skill inventory. To address this gap, we introduce SKILLSPAN, a novel SE dataset consisting of 14.5K sentences and over 12.5K annotated spans. We release its respective guidelines created over three different sources annotated for hard and soft skills by domain experts. We introduce a BERT baseline (Devlin et al., 2019). To improve upon this baseline, we experiment with language models that are optimized for long spans (Joshi et al., 2020; Beltagy et al., 2020), continuous pre-training on the job posting domain (Han and Eisenstein, 2019; Gururangan et al., 2020), and multi-task learning (Caruana, 1997). Our results show that the domain-adapted models significantly outperform their non-adapted counterparts, and single-task outperforms multi-task learning.",
}
