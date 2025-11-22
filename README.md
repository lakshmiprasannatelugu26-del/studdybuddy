# This Python 3 environment comes with many helpful analytics libraries installed
# It is defined by the kaggle/python Docker image: https://github.com/kaggle/docker-python
# For example, here's several helpful packages to load

import numpy as np # linear algebra
import pandas as pd # data processing, CSV file I/O (e.g. pd.read_csv)

# Input data files are available in the read-only "../input/" directory
# For example, running this (by clicking run or pressing Shift+Enter) will list all files under the input directory

import os
for dirname, _, filenames in os.walk('/kaggle/input'):
    for filename in filenames:
        print(os.path.join(dirname, filename))

# You can write up to 20GB to the current directory (/kaggle/working/) that gets preserved as output when you create a version using "Save & Run All" 
# You can also write temporary files to /kaggle/temp/, but they won't be saved outside of the current session
StudyBuddy – Student Life AI Agent
Your Personal Study Planner, Teacher & Motivation Partner
StudyBuddy is an all-in-one AI agent designed to help students learn smarter, stay organized, reduce stress, and achieve their goals with ease.

This project includes:

Adaptive Study Planner
Concept Explanation (Teacher Mode)
Exam Booster Mode
Learning Style Detection
Student Dashboard
Motivation & Wellness Support
And 20+ total features
# =============================================================
# STUDYBUDDY – FULL SIMULATION AI AGENT FOR KAGGLE SUBMISSION
# =============================================================

# -------------------------------------------------------------
# 1. MASTER PROMPT (FULL 20 FEATURES)
# -------------------------------------------------------------
MASTER_PROMPT = """
STUDYBUDDY – STUDENT LIFE AI AGENT

CORE RESPONSIBILITIES:
1. Adaptive Study Planner
2. Personal Teacher Mode
3. Homework Helper (No direct answers)
4. Progress Tracker
5. Motivation & Mental Wellness
6. Exam Booster Mode

ADVANCED FEATURES:
7. Learning Style Detection
8. Concept Visualizer (Mind maps, flowcharts, diagrams)
9. Sleep & Health-Friendly Study Mode
10. Voice Mode (text simulation)
11. Doubt Detector
12. Focus & Music Recommendations
13. Goal Tracker + Reward Badges
14. Science/Math Tutor (step-by-step, no direct answers)
15. Aesthetic Note Designer
16. Study Material Translator
17. Personalized Student Dashboard
18. Weekly Summary Generator
19. Streak Tracker
20. Productivity Advice Engine

RESPONSE FORMAT:
1. Quick Summary
2. Main structured answer
3. Bonus tips/motivation

RULES:
- No direct assignment answers
- Must explain clearly
- Be friendly, supportive, and aesthetic
"""


# -------------------------------------------------------------
# 2. SIMULATED AI AGENT (KAGGLE SAFE)
# -------------------------------------------------------------
def studybuddy_agent(user_input):
    """
    Kaggle cannot call real AI models.
    This function SIMULATES how the agent would respond,
    using handcrafted outputs that showcase all 20 features.
    """

    # === PREDEFINED SIMULATED OUTPUTS FOR ALL 20 FEATURES ===
    simulated_responses = {
        "study plan": """🗓️ **Adaptive Study Plan**
Quick Summary: Here is your customized plan.

**Morning**
- 7:00–7:30 → Maths (Algebra)
- 7:30–8:00 → Science (Diagrams)

**Evening**
- 6:00–6:45 → English summary writing

✨ Bonus: Take a 5-minute break every 25 minutes.""",

        "teacher": """📘 **Teacher Mode – Photosynthesis**
Quick Summary: Plants make their own food.

**Explanation**
Plants use:
- Sunlight  
- Water  
- CO₂  
to produce:
- Glucose (food)
- Oxygen  

**Practice Questions**
1. Why do plants need sunlight?
2. What is glucose?
""",

        "homework": """📝 **Homework Helper**
Quick Summary: Here are the steps.

**Steps to Solve**
1. Understand the question  
2. Identify key terms  
3. Break into small parts  
4. Write clean answers  

✨ Bonus: I won't give full answers, only hints.""",

        "learning style": """🎨 **Learning Style Detection**
Quick Summary: You are a **Visual learner**.

**What this means:**
- Diagrams  
- Flowcharts  
- Colored notes  
help you learn faster.""",

        "visual": """🌈 **Concept Visualizer**
Quick Summary: Here is your diagram.

**Mind Map – Electricity Flow**
Battery ➜ Wire ➜ Switch ➜ Bulb → Light Produced""",

        "health": """😴 **Healthy Study Mode**
Quick Summary: You're studying too late.

**Suggestions**
- Sleep before 11 PM  
- Study 6–8 AM instead  
- Take water every 45 mins  
- Do neck stretch for 1 min  

✨ Bonus: Your health matters!""",

        "exam": """🔥 **Exam Booster Mode**
Quick Summary: Here is your 7-day revision plan.

Day 1 → Algebra  
Day 2 → Polynomials  
Day 3 → Geometry  
Day 4 → Graphs  
Day 5 → Formulas  
Day 6 → Full mock test  
Day 7 → Light recap + mistakes revision""",

        "doubt": """❓ **Doubt Detector**
Quick Summary: I spotted your weak area.

You are confused about: **Integrals Basics**

**Fix**
- Understand limits  
- Practice simple ∫x dx  
- Do 3 problems daily""",

        "music": """🎧 **Focus Music Recommendations**
Quick Summary: Best music for studying.

- Lo-Fi beats  
- Rain sounds  
- Deep focus playlist  
- Calm piano""",

        "goal": """🎯 **Goal Tracker + Rewards**
Quick Summary: Your daily goal progress.

Today's Goal: Study 2 hours  
Completed: 1.5 hours  
Reward: ⭐ Silver Badge""",

        "tutor": """🧪 **Science/Math Tutor Mode**
Quick Summary: Step-by-step explanation.

**Example Problem (Simulated)**
Find the area of a triangle.

**Steps**
1. Use formula A = ½ × base × height  
2. Substitute values  
3. Calculate  

✨ Bonus: Try similar problems.""",

        "notes": """🎨 **Aesthetic Notes Designer**

📘 Newton’s Laws (Aesthetic Style)
1️⃣ An object stays at rest unless a force acts  
2️⃣ F = m × a  
3️⃣ Every action → equal opposite reaction""",

        "translate": """🌐 **Study Material Translator**

English → Simple Telugu  
"Mitochondria is the powerhouse of the cell"  
= "మైటోకాండ్రియా కణానికి శక్తినిచ్చే కేంద్రం" """,

        "dashboard": """📊 **Personal Dashboard**

Study Hours: 3.2  
Completed Tasks: 4/6  
Streak: 5 days  
Productivity: 78%""",

        "summary": """📅 **Weekly Summary**

You studied 12.5 hours this week.  
Your best subjects: Maths, Science  
Lowest: English (Revise summaries)""",

        "productivity": """⚡ **Productivity Tips**

- Use Pomodoro: 25m study + 5m break  
- Avoid phone during study  
- Study in morning for 2x retention  
"""
    }

    # match keywords
    text = user_input.lower()
    for key in simulated_responses:
        if key in text:
            return simulated_responses[key]

    # Default fallback
    return "Simulated StudyBuddy response (feature not matched). Try keywords: study plan, teacher, homework, exam, dashboard."


# -------------------------------------------------------------
# 3. TEST THE AGENT WITH ALL FEATURES
# -------------------------------------------------------------
tests = [
    "Create a study plan",
    "Explain as a teacher",
    "Help with homework",
    "Detect my learning style",
    "Make a visual diagram",
    "I am studying late. Give health advice",
    "Give exam revision plan",
    "Check my doubt",
    "Suggest focus music",
    "Track my goal",
    "Be a math tutor",
    "Make aesthetic notes",
    "Translate study material",
    "Show dashboard",
    "Give weekly summary",
    "Give productivity tips"
]

for t in tests:
    print("\n====================================")
    print("User:", t)
    print("Agent:", studybuddy_agent(t))
====================================
User: Create a study plan
Agent: 🗓️ **Adaptive Study Plan**
Quick Summary: Here is your customized plan.

**Morning**
- 7:00–7:30 → Maths (Algebra)
- 7:30–8:00 → Science (Diagrams)

**Evening**
- 6:00–6:45 → English summary writing

✨ Bonus: Take a 5-minute break every 25 minutes.

====================================
User: Explain as a teacher
Agent: 📘 **Teacher Mode – Photosynthesis**
Quick Summary: Plants make their own food.

**Explanation**
Plants use:
- Sunlight  
- Water  
- CO₂  
to produce:
- Glucose (food)
- Oxygen  

**Practice Questions**
1. Why do plants need sunlight?
2. What is glucose?


====================================
User: Help with homework
Agent: 📝 **Homework Helper**
Quick Summary: Here are the steps.

**Steps to Solve**
1. Understand the question  
2. Identify key terms  
3. Break into small parts  
4. Write clean answers  

✨ Bonus: I won't give full answers, only hints.

====================================
User: Detect my learning style
Agent: 🎨 **Learning Style Detection**
Quick Summary: You are a **Visual learner**.

**What this means:**
- Diagrams  
- Flowcharts  
- Colored notes  
help you learn faster.

====================================
User: Make a visual diagram
Agent: 🌈 **Concept Visualizer**
Quick Summary: Here is your diagram.

**Mind Map – Electricity Flow**
Battery ➜ Wire ➜ Switch ➜ Bulb → Light Produced

====================================
User: I am studying late. Give health advice
Agent: 😴 **Healthy Study Mode**
Quick Summary: You're studying too late.

**Suggestions**
- Sleep before 11 PM  
- Study 6–8 AM instead  
- Take water every 45 mins  
- Do neck stretch for 1 min  

✨ Bonus: Your health matters!

====================================
User: Give exam revision plan
Agent: 🔥 **Exam Booster Mode**
Quick Summary: Here is your 7-day revision plan.

Day 1 → Algebra  
Day 2 → Polynomials  
Day 3 → Geometry  
Day 4 → Graphs  
Day 5 → Formulas  
Day 6 → Full mock test  
Day 7 → Light recap + mistakes revision

====================================
User: Check my doubt
Agent: ❓ **Doubt Detector**
Quick Summary: I spotted your weak area.

You are confused about: **Integrals Basics**

**Fix**
- Understand limits  
- Practice simple ∫x dx  
- Do 3 problems daily

====================================
User: Suggest focus music
Agent: 🎧 **Focus Music Recommendations**
Quick Summary: Best music for studying.

- Lo-Fi beats  
- Rain sounds  
- Deep focus playlist  
- Calm piano

====================================
User: Track my goal
Agent: 🎯 **Goal Tracker + Rewards**
Quick Summary: Your daily goal progress.

Today's Goal: Study 2 hours  
Completed: 1.5 hours  
Reward: ⭐ Silver Badge

====================================
User: Be a math tutor
Agent: 🧪 **Science/Math Tutor Mode**
Quick Summary: Step-by-step explanation.

**Example Problem (Simulated)**
Find the area of a triangle.

**Steps**
1. Use formula A = ½ × base × height  
2. Substitute values  
3. Calculate  

✨ Bonus: Try similar problems.

====================================
User: Make aesthetic notes
Agent: 🎨 **Aesthetic Notes Designer**

📘 Newton’s Laws (Aesthetic Style)
1️⃣ An object stays at rest unless a force acts  
2️⃣ F = m × a  
3️⃣ Every action → equal opposite reaction

====================================
User: Translate study material
Agent: 🌐 **Study Material Translator**

English → Simple Telugu  
"Mitochondria is the powerhouse of the cell"  
= "మైటోకాండ్రియా కణానికి శక్తినిచ్చే కేంద్రం" 

====================================
User: Show dashboard
Agent: 📊 **Personal Dashboard**

Study Hours: 3.2  
Completed Tasks: 4/6  
Streak: 5 days  
Productivity: 78%

====================================
User: Give weekly summary
Agent: 📅 **Weekly Summary**

You studied 12.5 hours this week.  
Your best subjects: Maths, Science  
Lowest: English (Revise summaries)

====================================
User: Give productivity tips
Agent: ⚡ **Productivity Tips**

- Use Pomodoro: 25m study + 5m break  
- Avoid phone during study  
- Study in morning for 2x retention  

📚 StudyBuddy Feature Overview (All 20)
1. Adaptive Study Planner
Creates morning/evening plans & balances subjects.

2. Teacher Mode
Explains concepts in simple language.

3. Homework Helper
Gives hints, not answers.

4. Learning Style Detection
Detects Visual / Auditory / Writing / Kinesthetic.

5. Concept Visualizer
Flowcharts, mind maps (text-based).

6. Healthy Study Mode
Sleep/water/stretch reminders.

7. Exam Booster
7-day revision + cheat sheets.

8. Doubt Detector
Finds weak topics.

9. Focus Music Suggestions
Lo-fi, rain sounds, deep focus.

10. Goal Tracker
Badges & streaks.

11. Math/Science Tutor
Step-by-step logic.

12. Aesthetic Note Designer
Pretty, clean notes.

13. Translator
English ↔ Telugu.

14. Dashboard Generator
Daily productivity view.

15. Weekly Summary
Hours + strong/weak areas.

16. Productivity Tips
Pomodoro, deep work.

17. Voice Mode (text simulation)
Speech-style explanations.

18. Planner Adjustments
If student skips a day.

19. Streak Booster
Tracks consistency.

20. Study Motivation
Quotes & encouragement.

📌 Example Inputs & Outputs
User: “Create a study plan”
Agent: Gives a full morning + evening plan.

User: “Explain photosynthesis”
Agent: Simple teacher-mode explanation.

User: “I like diagrams”
Agent: Visual learner detected + flowchart.

User: “Weekly summary”
Agent: Shows hours studied + strengths.

def show_dashboard():
    print("""
📊 StudyBuddy Dashboard
- Study Hours: 3.5
- Completed: 4/6 tasks
- Streak: 5 days
- Productivity: 82%
""")

show_dashboard()
📊 StudyBuddy Dashboard
- Study Hours: 3.5
- Completed: 4/6 tasks
- Streak: 5 days
- Productivity: 82%

🏁 Conclusion
StudyBuddy is a simulated AI agent that demonstrates how a full multimodal student assistant can help with planning, understanding, revision, health, productivity, and progress tracking.

This notebook:

Explains all 20 features
Demonstrates realistic agent responses
Uses Kaggle-safe simulation
Shows a complete AI agent concept
 
