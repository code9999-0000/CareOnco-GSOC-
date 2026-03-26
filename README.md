# CareOnco GSOC
Patient-Facing Clinical Trial Chatbot with Interactive Map

# Project Introduction
# CareOnco : Patient Facing Clinical Trial Chatbot with Interactive Map
Contributor Proposal : Stein and Pai Labs, GSoC 2026\
Cancer patients are often left on their own to find clinical trials of cutting-edge therapies. This project seeks to develop an LLM-driven chatbot and interactive map that lets patients describe their situation and find nearby clinical trial sites that they may be eligible for.
The Cancer Trials Canada (CCTS) database holds hundreds of potentially life-saving studies — but its public interface requires patients to already know what they are looking for and most do not. That is why our project CareOnco is needed. To give the patients exactly what they need served on their plate.\
*What are we building?*\
A LLM driven chatbot and interactive map, here the patients describe their present condition, symptoms in plain language and recieve personalised, location wise list of trials they are eligible for. 
patient can type- "i have stage 3 lung cancer and live in toronto" and recieve nearby trials list with a map showing their locations and links to their description along with summaries using the cancer trial canada website.\
*User Interface :*  (three tightly integrated components)\
A Chainlit chat panel holds a natural conversation with the patient, progressively conducting their diagnosis, stage, prior treatment history, and location. 
A Mapbox map panel updates in real time as the chatbot identifies matching trials, with colour-coded pins reflecting trial status. 
A trial summary panel displays structured details when a patient selects a pin, and links directly to the corresponding Cancer Trials Canada page for full information.

# Contributor information
Name- Shivanshi Gaur\
Age- 19\
Current Location- Jaipur, India\
Email- gaurshivanshi9@gmail.com\
Github- https://github.com/code9999-0000 (with my project repositories)

# Education
University: Manipal University Jaipur, India (2024-2028)\
Degree: Bachelors of technology\
Field of study: Computer and Communication Engineering (CCE)

# Potential Mentor(s)
Lincoln Stein <lincoln.stein@gmail.com>\
Shraddha Pai <spai@oicr.on.ca>

# Project Goals
<img width="1440" height="2900" alt="image" src="https://github.com/user-attachments/assets/7b33a7cd-e6d4-46b1-bcc4-197d2b108e55" />

Explanation:\
Patient opens CareOnco and types their situation in plain language.\
The message hits Chainlit, which immediately runs it through guardrails checking for off-topic, harmful content before anything. If the patient uploads a pathology report, pdfplumber extracts the text and passes it to the LLM alongside the message.
The LLM reads the message and extracts structured patient data like condition, stage, location, prior treatments into a PatientContext JSON object via the LLMAdapter layer, which runs on Anthropic during development and switches to Ollama in production without changing any code. If key fields are missing, the chatbot asks one warm follow-up question and loops back until enough information is collected.\
Once PatientContext is complete, the backend takes over. FastAPI receives the object, the geocoder converts the patient's location description to coordinates, and the query builder constructs a parameterised PostGIS SQL query using ST_DWithin to find trial sites within the patient's travel radius. The eligibility scorer runs a three-tier match hard filter on condition, soft score on stage, flag on complex criteria and returns a ranked list of TrialResult objects.\
The LLM then summarises each matching trial in plain language, personalised to the patient's specific situation.\
Three panels update simultaneously. The chat panel shows the plain-language summaries. The Mapbox map panel places colour-coded pins green for recruiting, amber for by invitation, gray for completed. The summary panel shows structured trial details with a direct link to the Cancer Trials Canada page when a pin is clicked. The map is also bidirectional if the patient draws a bounding box or applies a filter on the map, it fires a synthetic message back into the chat and the LLM refines the results.\
Every response is evaluated by the RAGAS framework in the background, measuring relevancyand context recall against a curated test set.\
The patient clicks a trial, reads the summary, and contacts the study coordinator directly through the Cancer Trials Canada link.

# Gantt Chart
<img width="1522" height="662" alt="image" src="https://github.com/user-attachments/assets/0ef108b8-f544-44f6-8cc8-25c1b59ff104" />


# Detailed Project Proposal


# UML Diagram
1. COMPONENT DIAGRAM
 <img width="1440" height="1102" alt="image" src="https://github.com/user-attachments/assets/7ce9522e-94eb-4bee-a06f-3fc884276f73" />

3. USE CASE DIAGRAM 
   <img width="1440" height="1016" alt="image" src="https://github.com/user-attachments/assets/00a37133-2c60-4b9a-8c19-38c2417b030e" />

5. SEQUENCE DIAGRAM
<img width="1440" height="1440" alt="image" src="https://github.com/user-attachments/assets/5d650c8f-561d-46ab-9c8a-bdc4039d5a27" />

# Planned GSOC Work Hours
Pre-project (W1–W6) — Self-study, 9 hrs/week \
Weekdays: 1 hr/day × 5 = 5 hrs\
Weekends: 2 hrs/day × 2 = 4 hrs\
Active build (W7–W24) — Heavy coding, 13–14 hrs/week\
Weekdays: 1.5 hrs/day × 5 = 7.5 hrs\
Weekends: 3 hrs/day × 2 = 6 hrs\
Refinement + deploy (W25–W30) — Lighter, 9 hrs/week\
Weekdays: 1 hr/day × 5 = 5 hrs\
Weekends: 2 hrs/day × 2 = 4 hrs\
Docs + submission (W31–W34) — Winding down, 6–7 hrs/week\
Weekdays: 45 min/day × 5 = 4 hrs\
Weekends: 1.5 hrs/day × 2 = 3 hrs

# Skill Set
DSA|| Java|| C ||C++ || Python || Chainlit(familiar) || MySQL || React(typescript)|| Mapbox (Geomapping) APIs || VSCode || HuggingFace || MedGemma LLM || Operating System(ShellScript) || HTML || CSS || Github || RAG || Finetuning || PostgreSQL ||

