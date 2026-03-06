# User Story Template

**Admin User Stories:**
Title:

As an admin, I want to log into the portal using my username and password, so that I can securely manage the platform.

Acceptance Criteria:

Admin can enter a valid username and password to access the system.

The system authenticates the credentials before granting access.

If the credentials are invalid, an error message is displayed.

Priority: High
Story Points: 3

Title:

As an admin, I want to log out of the portal, so that I can protect system access after finishing my session.

Acceptance Criteria:

Admin can click a logout button to terminate the session.

The system clears the active session securely.

The admin is redirected to the login page after logout.

Priority: High
Story Points: 2

Title:

As an admin, I want to add doctors to the portal, so that they can be available for appointments in the system.

Acceptance Criteria:

Admin can enter doctor details such as name, specialization, and contact information.

The system validates that required fields are completed.

The doctor profile is stored successfully in the database.

Priority: High
Story Points: 5

Title:

As an admin, I want to delete a doctor’s profile from the portal, so that outdated or inactive doctors are removed from the system.

Acceptance Criteria:

Admin can select a doctor from the list and choose to delete the profile.

The system asks for confirmation before deleting the doctor.

The doctor record is removed from the database after confirmation.

Priority: Medium
Story Points: 3

Title:

As an admin, I want to run a stored procedure in MySQL CLI to get the number of appointments per month, so that I can track usage statistics.

Acceptance Criteria:

Admin can execute the stored procedure in MySQL CLI.

The system returns the number of appointments grouped by month.

The results can be used for reporting or monitoring platform activity.

**Patient User Stories:**
Title:

As a patient, I want to view a list of doctors without logging in, so that I can explore options before registering.

Acceptance Criteria:

A public page displays a list of doctors and their specialties.

Patients can access the page without authentication.

The doctor list includes basic information such as name and specialization.

Priority: Medium
Story Points: 2

Title:

As a patient, I want to sign up using my email and password, so that I can create an account and book appointments.

Acceptance Criteria:

Patients can register using an email and password.

The system validates that the email is unique.

The new account is stored successfully in the database.

Priority: High
Story Points: 3

Title:

As a patient, I want to log into the portal, so that I can manage my bookings.

Acceptance Criteria:

Patients can enter their email and password to log in.

The system verifies the credentials before granting access.

An error message is shown if login credentials are invalid.

Priority: High
Story Points: 3

Title:

As a patient, I want to log out of the portal, so that I can secure my account after using the system.

Acceptance Criteria:

Patients can click the logout button.

The system clears the active session.

The patient is redirected to the login page.

Priority: High
Story Points: 2

Title:

As a patient, I want to log in and book an hour-long appointment with a doctor, so that I can consult with them.

Acceptance Criteria:

Patients must be logged in to book an appointment.

Patients can select a doctor, date, and available time slot.

The system confirms and stores the appointment.

Priority: High
Story Points: 5

Title:

As a patient, I want to view my upcoming appointments, so that I can prepare accordingly.

Acceptance Criteria:

Logged-in patients can view a list of upcoming appointments.

Appointment details include doctor name, date, and time.

Only future appointments are displayed.

Priority: Medium
Story Points: 3

**Doctor User Stories:**

Title:

As a doctor, I want to log into the portal, so that I can manage my appointments.

Acceptance Criteria:

Doctors can enter their credentials to log in.

The system validates the credentials.

Doctors are redirected to the DoctorDashboard after login.

Priority: High
Story Points: 3

Title:

As a doctor, I want to log out of the portal, so that I can protect my data.

Acceptance Criteria:

Doctors can click a logout button.

The system ends the session securely.

The doctor is redirected to the login page.

Priority: High
Story Points: 2

Title:

As a doctor, I want to view my appointment calendar, so that I can stay organized.

Acceptance Criteria:

Doctors can view their appointments in a calendar or list format.

The calendar displays appointment dates and times.

Only appointments assigned to the logged-in doctor are shown.

Priority: High
Story Points: 4

Title:

As a doctor, I want to mark my unavailability, so that patients can only book available slots.

Acceptance Criteria:

Doctors can mark specific dates or times as unavailable.

The system prevents bookings during those times.

The changes are saved and reflected in the booking system.

Priority: Medium
Story Points: 4

Title:

As a doctor, I want to update my profile with specialization and contact information, so that patients have up-to-date information.

Acceptance Criteria:

Doctors can edit their specialization and contact details.

The system validates the entered information.

Updated information is saved successfully.

Priority: Medium
Story Points: 3

Title:

As a doctor, I want to view patient details for upcoming appointments, so that I can be prepared.

Acceptance Criteria:

Doctors can access patient details from their appointment list.

The system shows relevant information such as patient name and appointment time.

Only authorized doctors can view their assigned patients.

Priority: High
Story Points: 3

Priority: Medium
Story Points: 2
