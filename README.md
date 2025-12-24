# HACKATHON-PROJECT
ai-study-planner

ai-study-planner/
├── app.py
├── requirements.txt
└── README.md

import streamlit as st
import openai

# This app helps students generate a daily study plan using AI
# Created as a hackathon project for learning purposes

# ---------------- PAGE CONFIG ----------------
st.set_page_config(page_title="AI Study Planner", page_icon="📚")

st.title("📚 AI Study Planner")
st.write("AI powered study planning for students")

# ---------------- USER INPUT ----------------
name = st.text_input("Syeda Alina")
level = st.selectbox("Education Level", ["School", "College", "University"])
subjects = st.text_area("Subjects (comma separated)")
hours = st.slider("Study hours per day", 1, 10, 3)
exam_days = st.number_input("Days left until exam", 1, 365, 30)

# ---------------- AI FUNCTION ----------------
def generate_plan():
    openai.api_key = "YOUR_OPENAI_API_KEY"

    prompt = f"""
    Create a simple daily study plan for a student.

    Level: {level}
    Subjects: {subjects}
    Study hours per day: {hours}
    Exam in: {exam_days} days

    Use easy language.
    """

    response = openai.ChatCompletion.create(
        model="gpt-3.5-turbo",
        messages=[{"role": "user", "content": prompt}]
    )

    return response.choices[0].message.content

# ---------------- BUTTON ----------------
if st.button("Generate Study Plan"):
    if subjects.strip() == "":
        st.warning("Please enter subjects")
    else:
        with st.spinner("Creating your study plan..."):
            plan = generate_plan()
            st.success("Your AI Study Plan")
            st.write(plan)

streamlit
openai

#Hackathon Ready

# AI function temporarily disabled because API key is missing
# def generate_plan():
#     ...


st.info("AI feature disabled: API key missing")





# 📚 AI Study Planner

AI Study Planner is a beginner-friendly hackathon project that helps students
create a personalized daily study plan using Artificial Intelligence.

---

## ❓ Problem
Many students struggle with:
- Time management
- Study planning
- Knowing what to study daily

---

## 💡 Solution
AI Study Planner takes basic student information and generates a
clear daily study plan using AI.

---

# 🚀 Features
- Simple input form
- AI-generated study plan
- Beginner-friendly design
- Real-world student use case

---

# 🛠 Tech Stack
- Python
- Streamlit
- OpenAI API

---

# Hackathon Focus
- Clear problem
- Simple solution
- Working MVP
- Easy to understand

---

# Future Improvements
- Study reminders
- Progress tracking
- Mobile app version

openai.api_key = "sk-...0NAA"
