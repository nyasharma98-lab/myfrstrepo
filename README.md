# myfrstrepo
# 💻 Tech Stack:
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![CSS3](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white) ![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white) ![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black) ![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white) ![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=for-the-badge&logo=PyTorch&logoColor=white) ![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white) ![TensorFlow](https://img.shields.io/badge/TensorFlow-%23FF6F00.svg?style=for-the-badge&logo=TensorFlow&logoColor=white)

<!-- Proudly created with GPRM ( https://gprm.itsvg.in ) -->
  
## 🌐 Socials:
[![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://linkedin.com/in/nayasha-sharma-5) [![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?logo=YouTube&logoColor=white)](https://youtube.com/@@NayashaSharma-v3h) [![email](https://img.shields.io/badge/Email-D14836?logo=gmail&logoColor=white)](mailto:nyasharma98@gmail.com) 

<!-- Proudly created with GPRM ( https://gprm.itsvg.in ) -->


🌱 Currently Learning

Python
   ↓
Data Structures & Algorithms
   ↓
Machine Learning
   ↓
Deep Learning
   ↓
Generative AI & LLMs
   ↓
AI Agents
   ↓
Advanced AI Systems


💎 "Learn. Build. Improve. Repeat."

⭐ Thanks for visiting my profile! 🍁




import re

# Skills database
SKILLS = [
    "python",
    "java",
    "c",
    "c++",
    "javascript",
    "html",
    "css",
    "sql",
    "machine learning",
    "deep learning",
    "artificial intelligence",
    "data science",
    "pandas",
    "numpy",
    "scikit-learn",
    "tensorflow",
    "pytorch",
    "git",
    "github",
    "flask",
    "django",
    "fastapi",
    "nlp",
    "generative ai",
    "llm",
    "data structures",
    "algorithms"
]


def extract_text(file_path):
    """Read resume text file."""
    with open(file_path, "r", encoding="utf-8") as file:
        return file.read().lower()


def find_skills(text):
    """Find skills present in the text."""
    found_skills = []

    for skill in SKILLS:
        # Escape special characters such as C++
        pattern = r"(?<!\w)" + re.escape(skill) + r"(?!\w)"

        if re.search(pattern, text):
            found_skills.append(skill)

    return found_skills


def analyze_resume(resume_text, job_description):
    """Compare resume with job description."""

    resume_skills = find_skills(resume_text)
    job_skills = find_skills(job_description)

    matched_skills = list(set(resume_skills) & set(job_skills))
    missing_skills = list(set(job_skills) - set(resume_skills))

    if len(job_skills) > 0:
        score = (len(matched_skills) / len(job_skills)) * 100
    else:
        score = 0

    return resume_skills, job_skills, matched_skills, missing_skills, score


def main():

    print("=" * 50)
    print("        AI RESUME ANALYZER")
    print("=" * 50)

    resume_file = input("Enter resume text file path: ")

    try:
        resume_text = extract_text(resume_file)
    except FileNotFoundError:
        print("Resume file not found.")
        return

    print("\nPaste the Job Description below.")
    print("Type END on a new line when finished:\n")

    job_lines = []

    while True:
        line = input()

        if line.strip().upper() == "END":
            break

        job_lines.append(line)

    job_description = "\n".join(job_lines).lower()

    (
        resume_skills,
        job_skills,
        matched_skills,
        missing_skills,
        score
    ) = analyze_resume(resume_text, job_description)

    print("\n" + "=" * 50)
    print("             ANALYSIS RESULT")
    print("=" * 50)

    print(f"\nResume Skills:")
    print(", ".join(resume_skills) if resume_skills else "None")

    print(f"\nRequired Skills:")
    print(", ".join(job_skills) if job_skills else "None")

    print(f"\nMatched Skills:")
    print(", ".join(matched_skills) if matched_skills else "None")

    print(f"\nMissing Skills:")
    print(", ".join(missing_skills) if missing_skills else "None")

    print(f"\nResume Match Score: {score:.2f}%")

    if score >= 80:
        print("Recommendation: Excellent Match")
    elif score >= 60:
        print("Recommendation: Good Match")
    elif score >= 40:
        print("Recommendation: Average Match")
    else:
        print("Recommendation: Low Match")


if __name__ == "__main__":
    main()


































































































































