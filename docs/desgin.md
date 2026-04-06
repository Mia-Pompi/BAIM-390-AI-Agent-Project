#1. Problem Statement

Many students struggle to efficiently manage assignments, deadlines, and study plans across multiple courses. Existing tools (like calendars or LMS platforms) are fragmented and don’t actively help with decision-making.

Goal:
Build an AI-powered academic assistant agent that helps students plan, prioritize, and execute their coursework by intelligently organizing tasks and providing actionable recommendations.

2. Agent Scope
In Scope
Input: assignments, deadlines, course info
Generate:
prioritized task lists
study schedules
reminders and summaries
Answer questions like:
“What should I work on today?”
“Am I on track for my deadlines?”
Adjust plans dynamically based on progress
Out of Scope
Full LMS integration (Canvas/Blackboard APIs)
Real-time notifications (unless added later)
Grading or academic evaluation
3. Success Criteria

Your agent is successful if it can:

✅ Correctly prioritize tasks based on deadlines and workload
✅ Generate a realistic daily/weekly study plan
✅ Adapt when new tasks are added or deadlines change
✅ Provide clear, actionable responses (not vague suggestions)
✅ Maintain useful memory across interactions

Stretch Goals:

Personalization based on user habits
Integration with calendar APIs (e.g., Google Calendar)
4. Agent Architecture
Chosen Architecture: ReAct + Tool-Calling Hybrid

Why:

ReAct (Reason + Act) allows step-by-step reasoning
Tool-calling enables structured operations (calendar, task storage, etc.)
High-Level Flow
User inputs request
Agent:
reasons about intent
decides whether to use a tool
Calls tool (if needed)
Observes result
Produces final answer
Loop Structure
User Input → Reason → Tool चयन → Tool Output → Reason → Final Answer
5. Tools & APIs
Core Tools
Task Manager Tool
Add/update/delete assignments
Store deadlines and priorities
Scheduler Tool
Generate study plans
Allocate time blocks
Memory Store
Tracks:
past tasks
user preferences
progress
Optional APIs
Calendar API (e.g., Google Calendar)
Notification service (email/SMS)
File input (syllabus parsing)
6. Memory Strategy
Short-Term Memory
Current conversation context
Recent user queries
Long-Term Memory
Stored in database (JSON, SQLite, or vector DB)

Stores:

Tasks
Deadlines
User preferences (e.g., “study better at night”)
Retrieval Strategy
Retrieve relevant tasks based on:
due date
urgency
user query
7. Data Model (Simple Example)
{
  "tasks": [
    {
      "id": "1",
      "title": "Math Homework 3",
      "due_date": "2026-04-10",
      "priority": "high",
      "estimated_hours": 3,
      "status": "incomplete"
    }
  ]
}
8. Example Interaction

User:
“What should I work on today?”

Agent Process:

Retrieves tasks
Sorts by urgency + effort
Generates schedule

Output:
“You should focus on Math Homework 3 (due in 2 days). I recommend spending 2 hours today and 1 hour tomorrow.”

9. Tech Stack (Suggested)
Frontend: React or simple CLI
Backend: Python (FastAPI)
LLM: OpenAI API
Storage: SQLite / JSON / vector DB (like FAISS)
10. Risks & Challenges
Overly generic responses from the LLM
Poor task prioritization logic
Memory inconsistency
Scope creep (trying to build too much)
11. Future Improvements
Multi-agent system:
Planner agent
Execution agent
Calendar integration
Voice interface
Mobile app
