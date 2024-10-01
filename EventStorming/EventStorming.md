# Event Storming
 
## 1. Event Identification and Sequencing:
The first phase involved identifying critical events in the "ClearView" system. These events were arranged chronologically to understand data flow and interactions across the platform. By establishing temporal dependencies between events, the team gained clarity on how each event impacts system operations, enhancing the overall user experience. The following key events were identified:
 
- **Candidate Registered**: A candidate initiates their journey by registering in the system.
- **Resume Uploaded**: The candidate uploads their resume to the platform.
- **Resume Parsed**: The system processes the resume for data extraction.
- **Resume Updated**: Candidates update their resume after receiving system suggestions.
- **Resume Previewed**: Candidates review their resume before submission.
- **Resume Submitted**: The resume is finalized and submitted for job applications.
- **Job Applied**: The candidate applies for relevant job openings.
- **AI-Resume Received**: AI modules analyze the resume for matching recommendations.
- **Resume Tips Displayed**: AI provides suggestions to improve the resume.
- **Profile Anonymized**: Candidate profiles are anonymized to ensure privacy and security.
- **Story Created**: AI generates a resume summary after analyzing the data.
- **Job Description Received**: Job postings and descriptions are fetched from HR systems.
- **Job Matched**: The system matches profiles with job postings.
- **Employer Registered**: Employers register their company on the platform.
- **Company Details Filled**: Employers complete necessary company information.
- **Job Posted**: Jobs are posted by the employer.
- **Matching Profile Fetched**: The system identifies profiles that match the job criteria.
- **Matching Profile Displayed**: Matching profiles are displayed to the employer.
- **Profile Viewed**: Employers view limited candidate information.
- **Employer Payment Completed**: Employers initiate payment to access full candidate details.
- **Invoice Created**: A payment invoice is generated for reference.
- **Profile Unlocked**: Full candidate details, including contact information, are unlocked after payment.
- **Profile Sent To HR Systems**: Unlocked candidate profile sent to HR system.
- **Candidate Marked as Hired**: Employers mark candidates as hired for specific roles.
- **Candidate Marked as Not Hired**: The system updates candidates' status as "not hired."
- **Survey Taken**: Both employers and candidates complete surveys about their experience.
- **Admin Registered**: ClearView system admins register for data access.
- **Employer Listed**: Admins list all registered employers.
- **Candidate Listed**: Admins list all registered candidates.
- **Analytics Data Generated**: The system generates data for reporting and recommendations.
- **Report Generated**: Admins access various system reports.
 
<img src="images/Event Storming 1.png" alt="Event Storming 1"/>
 
## 2. Defining Actors and Commands:
The second phase focused on identifying the system’s key actors and their associated commands. This step defined the responsibilities of each user type, as well as how they interact with the system.
 
### User Roles:
- **Candidate**: Job seekers responsible for registering, uploading resumes, and applying for jobs.
- **Employer**: Company representatives responsible for company registration, job postings, and candidate management.
- **Admin**: ClearView system administrators responsible for overseeing system operations, generating reports, and managing data.
 
### Key Commands:
- **Upload Data**: Candidates upload resume files in Word or PDF format.
- **Read Data**: The system reads and processes resume data for job matching.
- **Update Data**: Candidates and employers update resume and job data.
- **Initiate Payment**: Employers initiate payments to access detailed candidate profiles.
- **Create Invoice**: A payment invoice is generated after the employer completes the transaction.
- **Generate Analytics**: The system generates reports and analytics for decision-making.
 
<img src="images/Event Storming 2.png" alt="Event Storming 2"/>
 
## 3. Event Grouping and Bounded Contexts:
The next phase involved grouping events based on their functionality or business processes, helping to define the system's bounded contexts and modular architecture. The key bounded contexts identified were:
 
### 1. **Account Management**:
- Manages candidate, employer, and admin roles.
- Stores profile and company data.
 
### 2. **Resume Processing**:
- Parses resumes and sends data to the AI module.
- Ensures profile security and anonymization.
- Provides data for reporting and analytics.
 
### 3. **Job Matching**:
- Matches candidates with relevant job opportunities.
- Matches job postings with suitable candidates.
 
### 4. **Reporting**:
- Generates and displays candidate and employer details.
- Provides data insights from resumes.
 
### 5. **Hiring**:
- Supports the hiring process, including marking candidates as hired or not hired.
- Updates job statuses accordingly.
 
### 6. **Collecting Jobs**:
- Employer manage jobs.
 
### 7. **Feedback Management**:
- Manages candidate and employer surveys on system performance.
 
<img src="images/Event Storming 3.png" alt="Event Storming 4"/>

## 4. Bounded Contexts & Components:
Bounded contexts are crucial in defining the boundaries within which specific business functionalities and services operate. Each bounded context encapsulates a distinct part of the system, ensuring that responsibilities and processes are modular, maintainable, and independently scalable.

### 1. **User & Role -> Account-Service**:
- Governs the user and role management, handling candidate, employer, and admin profiles.

### 2. **Resume Processing -> Resume-Service**:
- Responsible for resume processing, including parsing, anonymizing, and securing resume data.

### 3. **Job  -> Job-Service**:
- Manages job scheduling and fetching tasks.

### 4. **Job Matching -> Job-Matcher-Service**:
- Handles the core job-matching functionality, linking candidates to relevant jobs and vice versa.

### 5. **Feedback -> Survey-Service**:
- Manages the feedback collection & survey processes to ensure smooth interaction between candidates and employers regarding their system experience.

### 6. **Analytics/Reports -> Analytics-Service**:
- Generates analytics and reports, providing system insights for administrators and users.

Each service operates within its bounded context, promoting a clear separation of concerns and streamlining system performance across various domains.

<img src="images/Event Storming 4.png" alt="Event Storming 4"/>
 
## Conclusion:
The event storming process for the "ClearView" project facilitated a deep understanding of the system’s requirements, user roles, and event flows. By clearly defining events, actors, commands, and bounded contexts, we established a robust foundation for developing a transparent and efficient hiring platform, addressing both technical and business challenges
