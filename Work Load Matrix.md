# Election Management System

## 1. Voter Registration

### Front-end (Member 1)
Design and implement registration UI with the following features:
- **Input Fields**: Name, email, password, and other required voter details.
- **Drop-downs**: Voter region and other relevant options.
- **Error Messages**: Display for invalid input or missing fields.
- **Responsive Design**: Mobile-friendly and adaptable layout.
- **Form Validation**:
  - Required fields.
  - Email format.
  - Password strength.
- **Bot Protection**: Implement reCAPTCHA.

#### UI Pages
- Registration form page.
- Confirmation and success page.

### Back-end (Member 1)
Develop API endpoints:
- `POST /register`: Handle new voter registrations.
- `GET /voter/:id`: Retrieve specific voter details.
- `PUT /voter/:id`: Update voter information.

#### JWT-based Authentication
- Generate tokens during registration and login.
- Verify tokens for subsequent requests.
- Secure API endpoints against SQL injection and other vulnerabilities.

### Database Integration (Member 1)
- **Schema Design**: Tables for voters, including fields for encrypted personal data.
- **Indices**: Optimize key fields (e.g., email, voter ID).
- **Encryption**:
  - Encrypt passwords using bcrypt.
  - Use AES encryption for sensitive personal data.

### Additional Contributions (All)
- **Diagrams**:
  - ER diagram for the voter database.
  - Sequence diagrams illustrating the voter registration process.
- **Documentation**: Write technical documentation for the registration workflow.

---

## 2. Election Configuration

### Front-end (Member 2)
Build admin interfaces:
- **Forms**: Add and update election details (e.g., name, date, type) and create candidate profiles with photo uploads.
- **Validation**: Real-time validation for dates and profile completeness.

#### UI Pages
- Election setup page.
- Candidate profile creation page.
- Election type selection page.

### Back-end (Member 3)
Develop APIs:
- `POST /election`: Create a new election.
- `GET /election/:id`: Fetch details of a specific election.
- `POST /candidate`: Add candidate details.
- `PUT /candidate/:id`: Update candidate profiles.
- `GET /election/types`: Fetch supported election types.

#### Election Logic
- First-past-the-post: Voters select one candidate, and the candidate with the most votes wins.
- Proportional representation: Seats allocated based on percentage of votes.

### Database Integration (Member 3)
- **Schema Design**:
  - Election table with type, date, and metadata.
  - Candidate table linked to elections.
  - Relationships between candidates, voters, and elections.
- **Constraints**: Prevent duplicate candidates or conflicting election schedules.

### Additional Contributions (All)
- **Diagrams**:
  - UML class diagrams for election-related entities.
  - Activity diagrams showing workflows.

---

## 3. Vote Casting

### Front-end (Member 4)
Develop voting interface:
- **Candidate List**: Display photos and names.
- **Feedback**: Real-time feedback for selected options.
- **Confirmation**: Confirm vote button with a final dialog.
- **Accessibility**: Features for visually impaired users.

#### UI Pages
- Voting page displaying candidates.
- Confirmation dialog page.
- Voting success page.

### Back-end (Member 5)
Implement vote-casting APIs:
- `POST /vote`: Submit a vote.
- `GET /vote/status`: Check if a voter has already cast their vote.

#### Vote Storage
- Store votes in a write-once, read-many format.
- Timestamp votes with unique voter IDs.
- Validate voter eligibility and prevent duplicate votes.

### Database Integration (Member 5)
- **Schema Design**:
  - Secure vote storage with anonymized voter IDs.
  - Logs for tracking vote submissions.
- **Safeguards**:
  - Monitor for unusual patterns.
  - Secure database against unauthorized access.

### Additional Contributions (All)
- **Diagrams**:
  - Use case diagram for vote-casting process.
  - Sequence diagram for API interaction during voting.

---

## 4. Result Calculation and Reporting

### Front-end (Member 3)
Build dashboards:
- **Real-Time Results**: Display candidate names and vote counts.
- **Filters**: By city, province, and election type.
- **Visualizations**: Bar and pie charts for results.
- **Export**: Support for PDF/CSV export.

#### UI Pages
- Results dashboard page.
- Analytics and filtering page.
- Export results page.

### Back-end (Member 2)
Develop APIs:
- `GET /results/:election_id`: Fetch real-time election results.
- `POST /results/calculate`: Trigger manual result calculation.
- `POST /results/export`: Export results for external systems.

#### Analytics
- Metrics: Voter turnout, invalid votes.
- Real-time updates with WebSocket integration.

### Database Integration (Member 2)
- **Schema Design**:
  - Result storage tables.
  - Historical tables for archived results.
- **Optimization**: Query optimization for analytics.

### Additional Contributions (All)
- **Diagrams**:
  - State diagrams for result processing.
  - Documentation for reporting APIs.

---

## 5. Auditing and Security

### Front-end (Member 5)
Admin UI for audit trails:
- **Log Filters**: User actions, timestamps.
- **Notifications**: Real-time alerts for suspicious activities.
- **Security Logs**: Visualize trends in failed logins or API abuses.

#### UI Pages
- Audit trail page.
- Security logs dashboard.
- Suspicious activity notification page.

### Back-end (Member 4)
Develop APIs for auditing:
- `GET /audit`: Retrieve audit logs.
- `POST /audit`: Record a new audit event.

#### Logging
- Encrypt audit logs.
- Include user details, timestamps, and action descriptions.

### Database Integration (Member 4)
- **Schema Design**:
  - Audit trail tables with IP addresses.
  - Indices for quick filtering.
- **Real-Time Monitoring**: Trigger alerts for unusual patterns.

### Additional Contributions (All)
- **Security Documentation**:
  - Deployment diagrams showing secure setup.
  - Threat models identifying vulnerabilities.

---

## Shared Responsibilities (All)

### Collaboration on System Design
- **Architecture**: Microservices with clear boundaries:
  - Services include authentication, voter management, election setup, vote processing, result reporting, and auditing.
- **Inter-Service Communication**: Define protocols and test compatibility.
- **Integration Testing**: Conduct end-to-end tests.

### Testing and Debugging
- **Unit Tests**: Write tests for APIs and components.
- **Integration Tests**: Validate data flow between front-end and back-end.
- **User Acceptance Tests**: Gather usability feedback.

### Documentation
- **System Features**:
  - User guides for admin and voter roles.
  - Technical guides for developers.
- **Workflow Diagrams**: Flowcharts for major processes (e.g., voter registration, vote casting).
