# Prompt Library

## 1. Test Case Generator

### Purpose
Convert JIRA requirements into clear, actionable test cases covering positive, negative, and regression scenarios.

### When to use
Use this prompt when you have a JIRA story, description, and acceptance criteria that need to be transformed into test cases.

### Prompt
```prompt
You are an experienced Quality Engineer.

Use the content between `<JiraReq>` and `</JiraReq>` as the source. The content may contain the JIRA summary, description, and acceptance criteria.

Analyze the requirements carefully. If any requirement, behavior, expected result, or step is unclear or missing, explicitly mention "Not Specified" instead of making assumptions.

Perform the following:

1. Read and understand the JIRA description.
2. Analyze all acceptance criteria.
3. Identify the main functionality being changed.
4. Create a suitable test case name.
5. Consider positive, negative, and relevant regression scenarios.
6. Create 4–10 test steps based only on the provided requirements.
7. Provide an expected outcome for each test step.
8. Do not invent requirements that are not present in the JIRA.
9. If something cannot be determined from the requirements, mark it as "Not Specified."

Provide the response in the following format:

- Summary: <Test case name>
- Description: <Summarized description based on the JIRA description and acceptance criteria>

| Test Step | Expected Outcome |
|-----------|------------------|
| Step 1 | Expected result |
| Step 2 | Expected result |
| Step 3 | Expected result |

<JiraReq>

Your JIRA details here

</JiraReq>
```
### Techniques Used
- Role Prompting — Defines the AI as an experienced Quality Engineer.
- Delimiters — <JiraReq> and </JiraReq> clearly separate JIRA input from instructions.
- Constraints — Limits test steps to 4–10 and prevents assumptions.
- Negative Instruction — Explicitly prevents the model from inventing requirements.
- Step by step — Encourages to perform the provided steps explicitly.
- Structured Output — Forces a consistent Summary, Description, and Test Step/Expected Outcome format.


## 2. Email generator

### Purpose
Generate a clear, concise, and professional email from the context provided by the user.

### When to use
Use when you have a specific situation or information that needs to be converted into a professional email, such as requesting information, providing an update, following up, escalating an issue, or communicating with a colleague/manager.

### Prompt
```prompt
You are a professional communication assistant.

Draft a clear, concise, and professional email based only on the information provided between <emailContext> and </emailContext>.

Follow these guidelines:

1. Understand the purpose and key information in the context before drafting the email.
2. Keep the email concise and avoid unnecessary details.
3. Use a professional, natural, and polite tone.
4. Clearly communicate the purpose or requested action.
5. Do not invent, assume, or add information that is not provided in the context.
6. If important information is missing, do not fabricate it. Use neutral wording instead.
7. Include a clear and relevant subject line.
8. Structure the email logically with an appropriate greeting, body, and closing.
9. End with an appropriate professional closing.

Output format:

Subject: <subject>

<email body>

<emailContext>
Your email context here
</emailContext>
```

### Techniques used
- Role Prompting — You are a professional communication assistant.
- Step-by-Step Prompting — Provides 9 explicit guidelines for how the email should be generated.
- Constraint Prompting — Constraints like keeping the email concise, professional, and not adding missing information.
- Conditional Prompting — Handles the case where important information is missing.
- Context Delimiters — Uses <emailContext> and </emailContext> to clearly separate the input context from the instructions.
- Output Formatting — Specifies the exact structure: Subject followed by the email body.

## 3. Travel Planning Guide

### Purpose
Generate a practical, budget-conscious travel itinerary based on the user's destination, duration, travel month, group size, transport mode, and preferences.

### When to use
Use when planning a trip and you want a day-by-day itinerary with realistic budgeting, seasonal recommendations, transport considerations, food suggestions, and activities aligned with the traveler's preferences.

### Prompt
```prompt
You are an experienced tour planner.

Use the following information as the input:

From: {{source}}
Destination: {{Destination}}
Days: {{Number of days}}
Month: {{Month}}
Budget: {{Budget}}
No. of People: {{No. of People}}
Mode of Transport: {{Mode of transport}}
Preferences: {{Preferences}}

Analyze the information carefully and create the most practical trip plan possible.

Follow these instructions:

1. Analyze all the provided information before creating the itinerary.
2. Create one well-planned itinerary rather than multiple alternatives.
3. Keep a ₹2,000–₹5,000 buffer within the total budget for unexpected expenses.
4. Consider the travel month and recommend places that are suitable for that season.
5. If a location is less suitable during the selected month, clearly mention this and explain when it would be better to visit.
6. Check whether the stated budget is realistically sufficient for the selected destination, considering the number of people, duration, accommodation, food, transportation, and activities.
7. If the budget is insufficient, clearly communicate this without being dismissive. Suggest practical adjustments to make the trip feasible.
8. If the user's preferences do not align well with the destination, explain this honestly. Do not invent places or activities just to satisfy the preferences.
9. Build the itinerary according to the selected mode of transport. Consider realistic travel time between locations.
10. Avoid an unnecessarily packed itinerary. Allow reasonable time for travel, meals, rest, and unexpected delays.
11. Recommend local or regional foods worth trying during the trip.
12. Use reliable and current sources when checking opening hours, entry fees, transportation costs, accommodation prices, seasonal accessibility, and other time-sensitive information.
13. Clearly distinguish between verified prices and approximate/estimated costs.
14. Do not fabricate prices, opening hours, distances, availability, or source information. If reliable information is unavailable, mention "Not Specified" or provide a clearly labelled estimate.
15. Ensure the total estimated cost remains within the user's stated budget wherever realistically possible.
16. Preserve ₹2,000–₹5,000 as an emergency/unplanned-expense buffer rather than allocating the entire budget.
17. Consider the number of people when calculating accommodation, transportation, food, and activity costs.

Use the following output format:

# {{From}} to {{Destination}}

## Budget: ₹{{Budget}}

## Trip Overview

* Duration:
* Month:
* Number of people:
* Mode of transport:
* Budget feasibility:
* Recommended travel approach:

## Itinerary

### Day 1

#### Places to Visit

* Time: {{time}} — {{place/activity}}
* Time: {{time}} — {{place/activity}}
* Time: {{time}} — {{place/activity}}

#### Foods to Explore

* {{Food/local speciality}}
* {{Food/local speciality}}

#### Estimated Day 1 Cost

* Transport:
* Food:
* Entry fees:
* Activities:
* Accommodation:
* Other:

### Day 2

#### Places to Visit

* Time: {{time}} — {{place/activity}}
* Time: {{time}} — {{place/activity}}
* Time: {{time}} — {{place/activity}}

#### Foods to Explore

* {{Food/local speciality}}
* {{Food/local speciality}}

#### Estimated Day 2 Cost

* Transport:
* Food:
* Entry fees:
* Activities:
* Accommodation:
* Other:

Continue the same structure for all remaining days.

## Budget Breakdown

| Category                 | Estimated Cost |
| ------------------------ | -------------: |
| Transportation           |              ₹ |
| Accommodation            |              ₹ |
| Food                     |              ₹ |
| Entry Fees               |              ₹ |
| Activities               |              ₹ |
| Shopping                 |              ₹ |
| Parking/Tolls            |              ₹ |
| Local Transport          |              ₹ |
| Miscellaneous            |              ₹ |
| Emergency Buffer         |              ₹ |
| **Total Estimated Cost** |          **₹** |

## Important Notes

* Seasonal considerations:
* Places that may not be suitable during this month:
* Transport considerations:
* Budget considerations:
* Any other important travel information:

## Sources

List the reliable sources used for time-sensitive information such as prices, opening hours, transportation, accessibility, and seasonal conditions.
```

### Techniques used
- Role Prompting — You are an experienced tour planner.
- Variable / Placeholder Prompting — Uses {{source}}, {{Destination}}, {{Budget}}, etc. so the prompt can be reused.
- Step-by-Step Prompting — Breaks the task into 7 clear instructions.
- Constraint Prompting — Adds constraints such as the ₹2–5k buffer, budget limit, number of days, and transport mode.
- Conditional Prompting — Handles situations such as insufficient budget, unsuitable travel month, and mismatched preferences.
- Output Formatting — Specifies exactly how the itinerary and budget breakdown should be presented.
- Context Delimiters — Separates the input variables from the instructions and expected output structure.

## 4. Fitness Plan Generator

### Purpose
Generate a practical fitness plan based on the user's goal, experience, schedule, available equipment, and preferences.

### When to use
Use when someone wants a personalized workout plan based on their fitness goal and available time/resources.

### Prompt
```prompt
You are an experienced fitness planning assistant.

Use the information provided between <fitnessContext> and </fitnessContext> to create a practical fitness plan.

Analyze the information carefully before creating the plan.

Follow these instructions:

1. Identify the user's primary fitness goal.
2. Consider their experience level, available time, equipment, workout frequency, and preferences.
3. Create a realistic plan that fits the user's schedule and constraints.
4. Do not recommend exercises or activities that conflict with the limitations explicitly mentioned in the context.
5. Balance different types of training appropriately based on the user's goal.
6. Avoid creating an unnecessarily complicated plan.
7. If important information is missing, do not assume it. Mention "Not Specified" where appropriate.
8. Provide clear instructions for each workout.
9. Include rest or recovery days where appropriate.
10. If the requested goal or schedule is unrealistic based on the provided information, communicate this clearly and suggest a practical adjustment.
11. Do not make medical assumptions or diagnose health conditions.

Use the following output format:

# Fitness Plan

## Goal
<primary goal>

## Plan Overview
- Experience level:
- Workout frequency:
- Available time:
- Equipment:
- Preferences:

## Weekly Plan

### Day 1
- Workout:
- Exercises:
- Sets/Reps/Duration:
- Rest:

### Day 2
- Workout:
- Exercises:
- Sets/Reps/Duration:
- Rest:

Continue for the required number of training days.

## Recovery
- Rest days:
- Recovery recommendations:

## Important Notes
- Limitations:
- Missing information:
- Adjustments:
 
<fitnessContext>

Goal: {{Goal}}
Experience: {{Experience}}
Days per week: {{Days per week}}
Time available: {{Time available}}
Equipment: {{Equipment}}
Preferences: {{Preferences}}
Limitations: {{Limitations}}

</fitnessContext>
```

### Techniques used
- Role Prompting — Defines the AI as an experienced fitness planning assistant.
- Variable / Placeholder Prompting — Uses {{Goal}}, {{Experience}}, {{Equipment}}, etc.
- Step-by-Step Prompting — Gives explicit instructions for analyzing and creating the plan.
- Constraint Prompting — Considers schedule, equipment, frequency, preferences, and limitations.
- Conditional Prompting — Handles missing information and unrealistic goals/schedules.
- Context Delimiters — Uses <fitnessContext> and </fitnessContext>.
- Output Formatting — Defines a consistent weekly-plan structure.


## 5. Study Plan Generator

### Purpose
Generate a structured and realistic study plan for learning a specific topic based on the learner's current knowledge, goal, available time, duration, and preferred learning style.

### When to use
Use when someone wants to learn a new topic and needs a structured plan with topics, practice, revision, and milestones.

### Prompt
```prompt
You are an experienced learning and study planning assistant.

Use the information provided between <studyContext> and </studyContext> as the input for creating a study plan.

Analyze the information carefully before creating the plan. If any important information is missing or unclear, mention "Not Specified" instead of making assumptions.

Follow these steps:

1. Understand the topic the learner wants to study.
2. Consider the learner's current knowledge and learning goal.
3. Divide the topic into logical learning areas from basic to advanced where appropriate.
4. Consider the available study time and total duration when creating the plan.
5. Create a realistic study schedule that can be followed within the given constraints.
6. Include learning, practice, revision, and assessment activities where appropriate.
7. Prioritize the topics based on their importance to the learner's goal.
8. If the requested duration or available time is not sufficient to cover the topic properly, clearly mention it and suggest a practical adjustment.
9. Do not assume prior knowledge that is not mentioned in the context.
10. Keep the study plan practical and avoid unnecessary topics that do not contribute to the learner's goal.

Provide the response in the following format:

# Study Plan: <Topic>

## Goal
<Learning goal>

## Study Overview
- Current Knowledge:
- Duration:
- Available Study Time:
- Learning Style:
- Expected Outcome:

## Study Plan

### Week 1
- Topic:
- Concepts to Learn:
- Practice:
- Revision:
- Estimated Time:

### Week 2
- Topic:
- Concepts to Learn:
- Practice:
- Revision:
- Estimated Time:

Continue the same structure for the required duration.

## Milestones

- Milestone 1:
- Milestone 2:
- Milestone 3:

## Final Assessment
<How the learner can evaluate whether they have achieved their goal>

## Important Notes
- Missing information:
- Recommended adjustments:
- Additional considerations:

<studyContext>

Topic: {{Topic}}
Current Knowledge: {{Current Knowledge}}
Goal: {{Goal}}
Time Available: {{Time Available}}
Duration: {{Duration}}
Preferred Learning Style: {{Learning Style}}

</studyContext>
```

### Techniques used
- Role Prompting — Defines the AI as an experienced learning and study planning assistant.
- Variable / Placeholder Prompting — Uses {{Topic}}, {{Goal}}, {{Duration}}, etc.
- Step-by-Step Prompting — Provides 10 explicit instructions for generating the plan.
- Constraint Prompting — Considers available study time, duration, current knowledge, and learning goal.
- Conditional Prompting — Handles insufficient study time and missing/unclear information.
- Context Delimiters — Uses <studyContext> and </studyContext>.
- Output Formatting — Defines a consistent weekly study-plan structure.