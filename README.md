# CareOnco GSOC
Patient-Facing Clinical Trial Chatbot with Interactive Map

# Project Introduction
# CareOnco : Patient Facing Clinical Trial Chatbot with Interactive Map
Contributor Proposal : Stein and Pai Labs, GSoC 2026\
Cancer patients are often left on their own to find clinical trials of cutting-edge therapies. This project seeks to develop an LLM-driven chatbot and interactive map that lets patients describe their situation and find nearby clinical trial sites that they may be eligible for.
The Cancer Trials Canada (CCTS) database holds hundreds of potentially life-saving studies  but its public interface requires patients to already know what they are looking for and most do not. That is why our project CareOnco is needed. To give the patients exactly what they need served on their plate.\
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
Github- https://github.com/code9999-0000 (with my project repositories)\
LinkedIn- https://www.linkedin.com/in/shivanshi-gaur-b86162241/

# Education
University: Manipal University Jaipur, India (2024-2028)\
Degree: Bachelors of technology\
Field of study: Computer and Communication Engineering (CCE)

# My projects:
SMAF- A smart city healthcare framework starting with a medical chatbot for all users involving, Python,MedGemma,React, MongoDB, Hugging face transformers (Ongoing, will take 3 - 4 months). Will have ambulance, traffic etc systems near future.\
https://github.com/code9999-0000/SMAF-Smart-Metropolitian-Ai-Framework-

FinanceFlow-  The Budget Planning and Expense Analyzer is a web-based application designed to help users manage their personal finances efficiently. The main objective of the system is to allow users to record their income, track daily expenses, and plan budgets for different spending categories. The application is developed using web technologies including HTML and CSS for the user interface and MySQL for data storage.\
https://github.com/code9999-0000/FinanceFlow

Rapid India- An ambulance management system, that sends sos, tracks ambulances, guides through the shortest route with real time notifications, updates.
Real-time ambulance tracking system, Route optimization using maps/traffic data APIs, Hospital availability integration (beds, ICU, etc.), Emergency request interface for users, Prototype showing request → dispatch → optimized route. (Group project)\
https://github.com/ashmeets711/Rapid-India

# Potential Mentor(s)
Lincoln Stein <lincoln.stein@gmail.com>\
Shraddha Pai <spai@oicr.on.ca>

# Gantt Chart
Explains the timeline of executing each step involved in the project. This explains the proper schedule of every task going to be executed week wise.

<img width="1522" height="662" alt="image" src="https://github.com/user-attachments/assets/0ef108b8-f544-44f6-8cc8-25c1b59ff104" />

# Detailed Project Proposal

*Pre-Project Preparation : March 20 to April 30\
Six weeks of self-directed learning before the official coding period begins.*

W1  Mar 20-26   Orientation + accounts
- Read the full CareOnco project brief, concept page, and FAQ from Stein and Pai Labs take notes on every unfamiliar term. Create a git repository with readme and all needed folders.
- Browse Cancer Trials Canada (cancertrials.ca) for several hours to understand the trial data structure and what a patient would see.
- Create all required accounts: GitHub, Anthropic API, Mapbox, and ClinicalTrials.gov API access.
- Install Python 3.11, Node.js 20, PostgreSQL 16, and VS Code.
- Watch the official Chainlit and Mapbox getting-started videos in full.
- Understand the React-to-Me journal by Dr. Stein to understand the previous chatbot architecture.

W2  Mar 27-Apr 2   SQL + PostgreSQL
- Revise SQL by covering SELECT, WHERE, JOIN, GROUP BY, INSERT, UPDATE, and ON CONFLICT DO UPDATE.
- After installing PostgreSQL locally, create a test database, and I will write queries.
- Read the PostGIS introduction.
- Write a first geospatial query using ST_DWithin on sample data to confirm understanding is solid.
- Study what a GiST index is and why spatial queries require it for performance.

W3  Apr 3-9   Python + APIs
- Revise Python focusing on classes, dataclasses, abstract base classes, JSON parsing, and exception handling.
- Study the Pydantic v2 library to understand BaseModel, field validators, Optional fields, and how validation errors are raised.
- Read the ClinicalTrials.gov REST API v2 documentation end to end.
- Make the first live API call to ClinicalTrials.gov and print real trial data to the terminal.

W4  Apr 10-16   LLM + Chainlit
- Work through the Chainlit quickstart tutorial — build a simple echo chatbot that runs locally. Go through my own notes for revising.
- Write 5 different system prompts that extract patient fields from a message using JSON.
- Understand what an abstract base class (ABC) is and how it enables swappable LLM implementations.
- Read the RAGAS framework documentation to understand how answer_relevancy, faithfulness, and context_recall are measured.

W5  Apr 17-23   React + TypeScript + FastAPI
- Complete a React with TypeScript beginner tutorial build a small multi-component app with shared state.
- Build a minimal FastAPI application with two endpoints and test using curl.
- Read the Mapbox GL JS documentation on GeoJSON sources, clustering, popups, and the BoxZoomHandler event.
- Understand how React Context and useEffect work together for shared state across components.
- Refine the sketch of the full CareOnco architecture on paper frontend, backend, database, LLM.

W6  Apr 24-30   Final preparation
- Review all personal notes and fill any remaining knowledge gaps.
- Confirm every tool is installed, every API key is active, and the CareOnco GitHub repository is set up with backend and frontend folders.
- Write a one-page personal learning plan: MVP definition, what to cut if time runs short, and biggest technical concern.
- Set up the GitHub project board with labelled issues for each phase.

 
*Project Coding Period : May 1 to November 11*
*The build order follows foundations before features: database schema before chatbot, data ingestion before API, API before frontend, frontend before map, everything before deployment. Each week has concrete, testable deliverables.*

W7  May 1-7   Environment setup
- Create the careonco_db database.
- Set up a Python virtual environment with requirements.txt: fastapi, pydantic, psycopg2, geopy, chainlit.
- Commit to the CareOnco repository: folder structure, .gitignore, .env.example, and README.

W8  May 8-14   Database schema
- In SQL create all five tables: trials, sites, eligibility_criteria, treatments, and patient_sessions.
- Add the geography(POINT, 4326) column to sites and run: CREATE INDEX sites_location_idx ON sites USING GIST (location).
- Add foreign key constraints between trials and all child tables.
- Insert 10 sample rows and run ST_DWithin queries.

W9  May 15-21   DB hardening + upsert
- Write and test the upsert SQL: INSERT INTO trials ... ON CONFLICT (nct_id) DO UPDATE SET ... 
- Create a pipeline_runs log table: run_id, run_type, started_at, finished_at, records_processed, error_count. (will be modified)
- Create a geocoding_errors table: address, trial_id, error_message, attempted_at. (will be modified)

W10  May 22-28   Ingestion,  bulk loader
- Browse Cancer Trials Canada and map visible fields to the local trials and sites schema.
- Write ingestion_bulk.py that fetches trials in 1000-record paginated batches using pageToken cursor pagination.
- Test the bulk loader on a single condition (lung cancer) before running against the full dataset.
- Add retry logic with exponential backoff for failed API requests; log every failure to pipeline_runs.
- Run the geocoding pipeline on all site street addresses.

W11  May 29-Jun 4   Incremental updater + scheduler
- Write ingestion_incremental.py using the lastUpdatePostDate filter set to yesterday's date.
- Confirm the upsert logic correctly updates existing rows and inserts new ones without duplicates.
- Set up APScheduler with a CronTrigger: scheduler.add_job(run_incremental, CronTrigger(hour=2, minute=0)).
- Test by simulating a trial status change.

W12  Jun 5-11   FastAPI foundation
- Set up FastAPI.
- Write the PatientContext Pydantic model: condition, stage, prior_treatments (List[str]), location_description, travel_radius_miles, missing_fields (List[str]), session_id (UUID).
- Write build_trial_query(patient: PatientContext).

W13  Jun 12-18   Search endpoint + PostGIS
- Add the PostGIS filter: AND ST_DWithin(s.location:geography, ST_MakePoint(:lng, :lat)::geography, :radius_metres).
- Write the TrialResult and TrialSite dataclasses with all fields matching the frontend contract.
- Create the POST /search endpoint: accepts PatientContext, calls build_trial_query, returns List[TrialResult] ordered by ST_Distance ascending.
- Test by postinng a mock PatientContext JSON body and verifying real trial results come back.

W14  Jun 19-25   LLMAdapter + extraction
- Write the LLMAdapter abstract base class with one method: chat(messages: list[dict], response_format: dict).
- Write OllamaAdapte selected via LLM_PROVIDER environment variable.
- Write the extraction system prompt in prompts/extract_patient.txt using Anthropic structured output mode to guarantee valid JSON.
- Write extract_patient_context(conversation_history: list) - PatientContext  calls LLMAdapter, parses JSON, validates via Pydantic.

W15  Jun 26-Jul 2   Clarification loop + summariser
- Build the clarification loop: while len(patient.missing_fields) > THRESHOLD  generates one follow-up question per turn, appends reply to conversation_history, re-runs extraction.
- Define REQUIRED_FIELDS = ['condition', 'location_description'].
- Connect extraction, clarification loop, build_trial_query, and LLM summariser into a single end-to-end pipeline. Test with a full conversation.

W16  Jul 3-9   React chat UI
- Initialise the React TypeScript frontend using Vite inside the /frontend folder.
- Build the ChatPanel component that sends messages to the Chainlit backend.
- Build the TrialCard component: plain_summary, phase, nearest site name, distance_km, and a contact button.
- Apply large readable fonts, generous whitespace, no aggressive colours.

W17  Jul 10-16   Results list 
- Build the ResultsList component rendering multiple TrialCard components from the POST /search response.
- Connect live React frontend to live FastAPI backend and test the full flow in a browser.

W18  Jul 17-23   Mapbox map panel
- In Mapbox GL JS, build the TrialMap component initialised with a mapboxgl.Map.
- useEffect hook diffs incoming TrialSite[] against current marker layer using site_id as key new sites get new mapboxgl.Marker(), removed sites call .remove().
- Colour-code pins using Mapbox match expression: green = recruiting, amber = by invitation, gray = completed.
- Add popups with site name, city, distance, and a 'View on Cancer Trials Canada' link.

W19  Jul 24-30   Map to chat synchronisation
- Wire map-to-chat: clicking a marker fires map.on('click', 'trials-layer'), extracts trial_id from e.features[0].properties, updates selectedTrialId in AppState  summary panel fetches trial details.
- Wire chat-to-map: Chainlit emits TRIALS_UPDATED custom action carrying TrialResult[] TrialMap calls map.getSource('trials').setData() to update the GeoJSON layer.
- Wire map filter-to-chat: BoxZoomHandler onBoxZoomEnd coordinates are serialised to MapFilter and injected as a synthetic user message into the Chainlit conversation.
- Test bidirectional sync with edge cases: no results, sites spanning two provinces, single result far from patient.

W20  Jul 31-Aug 6   Geocoding + PDF upload
- Add geocoding enrichment between LLM extraction and query building: geopy.geocoders.Nominatim().geocode(location_description) populates PatientContext lat/lng.
- Implement PDF upload using Chainlit's built-in file upload component.
- Test geocoding with Canadian city names, postal codes, and informal descriptions.

W21  Aug 7-13   Eligibility scoring
- Tier 1 : hard SQL filter: WHERE t.condition ILIKE '%' || :condition || '%'. Only filter that can exclude a trial entirely.
- Tier 2 : Python soft score: incompatible patient.stage and trial.stage_required decrements match_score by 30 but never removes the trial.
- Tier 3 : regex scanner flags complex criteria using patterns: r'\d+\s*[x]\s*10' for lab values, r'ECOG|LVEF|eGFR' for clinical scoring, r'\d+\s*(weeks?|months?)' for time requirements.
- Flagged complex criteria returned in complex_criteria list on TrialResult rendered as 'discuss with your doctor' callout in the UI.

W22  Aug 14-20   Guardrails + security + privacy
- Write GuardrailsMiddleware.
- Failed checks replace responses with a safe fallback message and log for review.
- Audit all SQL queries every single one uses parameterised inputs.
- Confirm patient_sessions stores no personal information: no name, email, date of birth only session_id (UUID) and clinical context.

W23  Aug 21-27   RAGAS testing framework
- Build tests/evaluation/ with few curated test conversations: specific diagnosis, vague description, non-English terminology, paediatric, rare cancer, rural location, refused follow-up.
- Configure RAGAS to measure answer_relevancy, faithfulness, and context_recall on every test case.
- Wire RAGAS test suite to GitHub Actions.

W24  Aug 28-Sep 3   Testing rounds
- Run end-to-end tests for different patient personas.
- Test the map bounding box filter: draw a region around Ontario, verify only Ontario trials appear in chat and map.

W25  Sep 4-10   Refinement
- Revise all chatbot follow-up question phrasing every question must feel human, empathetic, not clinical.
- Improve plain-language trial summaries.
- Polish UI spacing, typography.

W26  Sep 11-17   Stretch features
- Add a direct Cancer Trials Canada link to every TrialCard: cancertrials.ca/trial/{nct_id}.
- Implement out-of-radius secondary sites: trials beyond travel radius shown collapsed with an 'expand' toggle.

W27  Sep 18-24   Deployment preparation
- Set up the production PostgreSQL database with PostGIS on Supabase or Railway.
- Configure all environment variables on the production server.
- Run the full bulk ingestion pipeline against the production database and verify record count.
- Deploy the FastAPI backend to Railway or Render confirm POST /search responds to a test request from the live URL.

W28  Sep 25-Oct 1   Go live
- Deploy the React frontend to Vercel or Netlify and connect to the production backend URL via environment variable.

W29  Oct 2-8   Mentor feedback
- Present the live tool to mentors demonstrating 3 different patient scenarios.
- Collect written feedback and classify every item as: must fix, should fix, or future work.
- Begin addressing all must-fix items immediately.

W30  Oct 9-15   Final fixes
- Complete fixes.
- Update the README.
- Run a final security audit: no hardcoded credentials, no SQL injection risks, no sensitive data in logs.

W31  Oct 16-22   Documentation
- Write the patient-facing user guide: how to use CareOnco step by step, with screenshots.
- Write technical documentation: database schema, API endpoints with request and response examples, deployment steps.
- Record a 5-minute screen walkthrough video.

W32  Oct 23-29   Submission
- Final review of all code, documentation, RAGAS test results, and the user guide before submission.
- Tag the final release on GitHub as v1.0 with a detailed release note.

W33-W34  Oct 30-Nov 11   Buffer + project close
- Use remaining capacity to address stretch goals, improve test coverage, or fix post-submission feedback.

# Tech Stack
In proposal pdf.

# Project Flow
<img width="1440" height="2900" alt="image" src="https://github.com/user-attachments/assets/7b33a7cd-e6d4-46b1-bcc4-197d2b108e55" />

Explanation:\
Patient opens CareOnco and types their situation in plain language.\
The message hits Chainlit, which immediately runs it through guardrails checking for off-topic, harmful content before anything. If the patient uploads a pathology report, pdfplumber extracts the text and passes it to the LLM alongside the message.
The LLM reads the message and extracts structured patient data like condition, stage, location, prior treatments into a PatientContext JSON object via the LLMAdapter layer, which runs on Anthropic during development and switches to Ollama in production without changing any code. If key fields are missing, the chatbot asks one warm follow-up question and loops back until enough information is collected.\
Once PatientContext is complete, the backend takes over. FastAPI receives the object, the geocoder converts the patient's location description to coordinates, and the query builder constructs a parameterised PostGIS SQL query using ST_DWithin to find trial sites within the patient's travel radius.\
The LLM then summarises each matching trial in plain language, personalised to the patient's specific situation.\
Three panels update simultaneously. The chat panel shows the plain-language summaries. The Mapbox map panel places colour-coded pins green for recruiting, amber for by invitation, gray for completed. The summary panel shows structured trial details with a direct link to the Cancer Trials Canada page when a pin is clicked. \
Every response is evaluated by the RAGAS framework in the background, measuring relevancyand context recall against a curated test set.\
The patient clicks a trial, reads the summary, and contacts the study coordinator directly through the Cancer Trials Canada link.


# UML Diagram
1. COMPONENT DIAGRAM\
   A simple diagram to understand diff components in the careOnco project. 

 <img width="1440" height="1102" alt="image" src="https://github.com/user-attachments/assets/7ce9522e-94eb-4bee-a06f-3fc884276f73" />

2. USE CASE DIAGRAM\
   Clearly explains what actors are involved and what action they can perform.

   <img width="1440" height="1016" alt="image" src="https://github.com/user-attachments/assets/00a37133-2c60-4b9a-8c19-38c2417b030e" />

3. SEQUENCE DIAGRAM
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

# How is my project different?
1. *Patient-first conversational design (not just a chatbot)*
Instead of acting as a simple query interface, the system conducts a guided, empathetic conversation. It incrementally builds a structured patient context. This ensures that even non-technical users who describe their situation vaguely can still receive results.
2. *Real-time integration of chat, map, and results (not isolated components)*
Unlike traditional tools where search results and maps are separate, CareOnco tightly synchronizes three components:
Chat (understanding user intent)
Map (visualizing nearby trials)
Results panel (structured summaries)
User actions in one component immediately update the others creating a unified exploratory experience.
3. *Hybrid filtering + intelligent scoring (not rigid eligibility matching)*
Most platforms either over-filter or overwhelm users with irrelevant results. My system combines:
Hard SQL filters for essential eligibility
Flags for complex criteria instead of excluding them
This ensures patients are not prematurely excluded and are encouraged to discuss borderline cases with their doctors.
4. *Built-in evaluation and safety layer*
The system incorporates:
Guardrails to prevent unsafe or misleading responses
RAGAS-based evaluation to continuously measure answer quality (relevancy, faithfulness, recall)
This shifts the project from just a working prototype to a measurable and trustworthy system
6. *At last, this project matters to me* because I have seen many cancer cases in my near vicinity and moreover I understand how overwhelming it could be to patients when medical help is not clear and understandable, how deeply it affects the mental state of a patient and decreases their morale .




THANK YOU
-------------------------------------------------------


