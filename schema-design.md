## MySQL Database Design

Table: patients

id: INT, Primary Key, AUTO_INCREMENT

first_name: VARCHAR(100), NOT NULL

last_name: VARCHAR(100), NOT NULL

email: VARCHAR(150), UNIQUE, NOT NULL

phone_number: VARCHAR(20), NOT NULL

date_of_birth: DATE

created_at: DATETIME, DEFAULT CURRENT_TIMESTAMP

Notes:

Email must be unique to prevent duplicate patient accounts.

Patient records should remain even if appointments are cancelled to maintain medical history.

Table: doctors

id: INT, Primary Key, AUTO_INCREMENT

first_name: VARCHAR(100), NOT NULL

last_name: VARCHAR(100), NOT NULL

specialization: VARCHAR(150), NOT NULL

email: VARCHAR(150), UNIQUE, NOT NULL

phone_number: VARCHAR(20)

created_at: DATETIME, DEFAULT CURRENT_TIMESTAMP

Notes:

Each doctor has a specialization to help patients choose the right professional.

Email is unique to avoid duplicate doctor profiles.

Table: appointments

id: INT, Primary Key, AUTO_INCREMENT

doctor_id: INT, Foreign Key → doctors(id)

patient_id: INT, Foreign Key → patients(id)

appointment_time: DATETIME, NOT NULL

status: INT, NOT NULL (0 = Scheduled, 1 = Completed, 2 = Cancelled)

created_at: DATETIME, DEFAULT CURRENT_TIMESTAMP

Notes:

Each appointment connects one patient and one doctor.

Overlapping appointments for the same doctor should be prevented through application-level validation.

If a patient is deleted, appointments could either be deleted using ON DELETE CASCADE or preserved for history depending on business rules.

Table: admin

id: INT, Primary Key, AUTO_INCREMENT

username: VARCHAR(100), UNIQUE, NOT NULL

password_hash: VARCHAR(255), NOT NULL

created_at: DATETIME, DEFAULT CURRENT_TIMESTAMP

Notes:

Passwords are stored as hashed values for security.

Admin users manage doctors and system configuration.

Table: clinic_locations

id: INT, Primary Key, AUTO_INCREMENT

name: VARCHAR(150), NOT NULL

address: VARCHAR(255), NOT NULL

phone_number: VARCHAR(20)

Notes:

Clinics may operate across multiple locations.

Doctors could later be linked to locations if needed.

Table: payments

id: INT, Primary Key, AUTO_INCREMENT

appointment_id: INT, Foreign Key → appointments(id)

amount: DECIMAL(10,2), NOT NULL

payment_method: VARCHAR(50)

payment_status: VARCHAR(50)

created_at: DATETIME, DEFAULT CURRENT_TIMESTAMP

Notes:

Payments are linked to appointments.

Stores financial records for consultations.

## MongoDB Collection Design

### Collection: prescriptions
{
  "_id": "ObjectId('64abc123456')",
  "patientId": 101,
  "doctorId": 12,
  "appointmentId": 51,
  "medications": [
    {
      "name": "Paracetamol",
      "dosage": "500mg",
      "frequency": "every 6 hours",
      "durationDays": 5
    },
    {
      "name": "Vitamin D",
      "dosage": "1000 IU",
      "frequency": "once daily",
      "durationDays": 30
    }
  ],
  "doctorNotes": "Patient reports mild headache. Monitor temperature daily.",
  "refillCount": 2,
  "pharmacy": {
    "name": "Walgreens SF",
    "location": "Market Street, San Francisco, CA"
  },
  "tags": ["headache", "pain management"],
  "createdAt": "2026-03-05T10:00:00Z",
  "updatedAt": "2026-03-05T10:30:00Z"
}

Design Notes:

Stores multiple medications per prescription as an array of embedded documents.

References patientId, doctorId, and appointmentId instead of embedding full objects to avoid redundancy.

Includes optional metadata such as tags for easier search and filtering.

Flexible structure allows adding new fields like lab tests or attachments without schema migration.

### Collection: patient_feedback
{
  "_id": "ObjectId('64abc654321')",
  "patientId": 101,
  "doctorId": 12,
  "appointmentId": 51,
  "rating": 4.5,
  "comments": "The doctor was very attentive and explained everything clearly.",
  "tags": ["friendly", "informative"],
  "createdAt": "2026-03-05T11:00:00Z"
}

Design Notes:

Feedback can be optional, so not all appointments require it.

Supports searching by tags, such as “friendly” or “informative”.

Flexible for adding images, attachments, or responses from doctors in the future.

### Collection: activity_logs
{
  "_id": "ObjectId('64abc987654')",
  "userId": 101,
  "userType": "patient",
  "action": "check-in",
  "appointmentId": 51,
  "timestamp": "2026-03-05T09:45:00Z",
  "metadata": {
    "device": "mobile_app",
    "ipAddress": "192.168.1.10"
  }
}

Design Notes:

Captures dynamic logs such as check-ins, messages, or updates.

metadata field allows flexible tracking of device, IP, or other context.

Supports audit, analytics, or future ML applications.
