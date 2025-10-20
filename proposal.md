# Case Title
**ApplicationBuilder**: AI-Powered Application Assistant

## Background
Many students and recent graduates lack experience in writing targeted job applications. They face the challenge of effectively presenting their skills, tailoring their CV and cover letter to each position, and understanding what automated recruitment systems (ATS) look for. This often leads to generic applications that neither capture attention nor pass the initial digital filters. There is a need for a tool that bridges this gap by offering personalized and intelligent guidance.

## Purpose
The main purpose is to provide students with an AI-powered assistant that transforms their CV and a job advertisement into a customized application package. The tool should not only generate content but also serve as a learning platform. It should give users a practical understanding of how AI is used in modern recruitment by highlighting key qualifications, suggesting concrete improvements, and optimizing documents for ATS systems.

## Target Audience
- **Primary Users**: Students and recent graduates applying for part-time jobs, internships, and their first full-time positions.
- **Secondary Users**: Career advisors and university career centers that support students in the job application process.

## Core Functionality

### Must-Haves (MVP)
- **Document Import**: Easy upload of CV (PDF/DOC/TXT) and pasting of job advertisement (text or URL).
- **Interactive Application Generator**: Generates an editable draft of a cover letter. Keywords from the ad are highlighted, and the user can choose the tone (e.g., formal, neutral, enthusiastic).
- **Concrete CV Improvements**: Provides a list of action-oriented suggestions to quantify achievements, use active verbs, and improve structure.
- **Visual Gap Analysis**: Presents an overview of requirements from the job ad and the extent to which the CV matches. Provides suggestions on how to close gaps (e.g., by rephrasing experience or mentioning specific projects).
- **Basic ATS Report**: Provides a checklist for keyword coverage, formatting errors (tables, images), and use of passive expressions.
- **Export**: Download of generated documents in DOCX and Markdown format.
- **Security and Privacy**: Secure login (email/password) and encrypted storage of all user data and documents.

### Should-Haves (Optional Extensions)
- **Personal Dashboard with Version History**: Allows users to manage documents, track applications, and compare previous versions to see improvements over time.
- **Advanced ATS Report**: Simulates a "score" (0-100%) against typical ATS criteria to provide a more detailed analysis.
- **Interview Preparation**: Generates a list of likely interview questions based on the job ad and the user's CV.
- **Multilingual Support**: Autodetection and generation in both Norwegian and English.
- **Templates and Style Guides**: Offers various templates for cover letters, potentially with the option for university branding for partner institutions.

## Data Requirements
- **Users**: `name`, `email`, `password` (hashed/salted), `language_preference`, `consents` (GDPR).
- **Documents**: Original CV (file + additional text), previous applications, generated letters.
- **Job Advertisements**: Raw text, source/URL, identified keywords and requirements.
- **Analysis Results**: Keyword match, gap analysis, ATS findings, recommendations.
- **Settings**: Desired tone/style, rewriting degree, default export format.

## User Stories
1.  As a student, I want to upload my CV and paste a URL to a job ad, so that I can get a customized cover letter in under a minute.
2.  As a recent graduate, I want to see exactly which requirements I do not meet, so that I can adjust my application to better highlight relevant experience from studies and projects.
3.  As a career advisor, I want to be able to see the version history for a student's application, so that I can provide targeted and effective guidance.
4.  As a user, I want to be sure that my personal data and documents are stored securely, so that I can use the service without concern.

## Technical Constraints
- **Authentication and Security**: Passwords must be stored hashed (e.g., with Argon2/bcrypt). All data traffic must be encrypted with TLS.
- **Data Storage and Privacy**: Files and analysis results must be encrypted (e.g., AES-256 at rest). The system must be fully GDPR-compliant, with explicit consent, the right to erasure, and data minimization.
- **File Handling**: Robust parsing of PDF/DOCX, including text extraction with fallback to OCR when needed to handle images of text.
- **Language Model (LLM)**: Evaluation of a local model vs. an external API. Must have mechanisms (prompt-blocking) to prevent sensitive data from being leaked.
- **Infrastructure**: Should have rate-limiting to prevent abuse and control costs.
- **Accessibility**: The interface must follow the WCAG 2.1 AA standard to ensure universal design.
- **Design**: Responsive web application (desktop-first, with good mobile support).

## Decision Points
- **Degree of Rewriting**: Should the tool suggest changes point-by-point, or should it actively rewrite large parts of the text? An adjustable slider (Low → High) could be considered.
- **Choice of Language Model**: Should we use an external API (like GPT-4) for the highest possible quality, or a local/open-source model for better control over costs and privacy?
- **Storage Location**: Should data be stored in a local database or in a cloud service (e.g., AWS S3)? Regardless of the choice, the servers must be within the EU/EEA.
- **Export Formats**: Which formats are most important for the MVP? DOCX and MD are suggested, but PDF may also be relevant.

## Success Criteria
- **Speed**: A user should be able to go from uploading documents to a finished first draft in under 30 seconds.
- **Effectiveness**: At least 80% of the generated applications should pass a basic ATS check for keywords and structure.
- **Data Integrity**: Functionality for secure deletion of user data ("the right to be forgotten") is implemented and verified.
- **Performance**: The application should load in under 2 seconds on a standard internet connection.
- **User Value**: In a pilot study with students, the tool should achieve an average score of over 4/5 on questions about its usefulness.
