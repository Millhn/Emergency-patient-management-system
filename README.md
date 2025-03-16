# Emergency Department Patient Management System (C)

This project implements an **Emergency Department (ED) patient management system** in C, focusing on managing patient records, triaging patients based on symptoms, generating prescription numbers, and converting patient data to **HL7 format** for electronic medical records (**EMR**).

## Features
- **Patient Management**: Add, display, and prioritize patients in the ED.
- **Triage System**: Assigns a priority based on symptoms (Red, Yellow, Green).
- **Prescription Number Generation**: Automatically generates a prescription number for each patient.
- **HL7 Message Creation**: Converts patient data into HL7 format for use with medical systems.

## Structure
- **Patient Data**: Each patient has an ID, name, symptoms, priority, and prescription number.
- **Linked List**: Patients are stored in a linked list, sorted by priority, where lower priority numbers represent higher urgency.
- **Triage System**: Based on common symptoms, patients are classified into different priority levels (Red, Yellow, Green).

## Requirements
- C compiler (e.g., GCC)
- Standard C libraries (stdio.h, stdlib.h, string.h)

## How to Use

1. **Compile the code**:
    ```bash
    gcc -o emergency_department patient_management.c
    ```

2. **Run the program**:
    ```bash
    ./emergency_department
    ```

3. **Input Patient Data**:
    - Enter the patient ID.
    - Enter the patient's name.
    - Enter the patient's symptoms (must be a valid symptom to proceed).

4. **Priority Assignment**: Based on the symptoms entered, the program will assign a priority:
    - **Red**: High priority (e.g., chest pain, shortness of breath)
    - **Yellow**: Medium priority (e.g., headache, fever)
    - **Green**: Low priority (e.g., minor injuries)

5. **Prescription Number**: A prescription number is generated automatically in the format `MEDXXX`.

6. **HL7 Format**: For each patient added, an HL7 message is created.

7. **Repeat**: You can continue adding patients or exit after displaying the patient list.

## Example of HL7 Message for a Patient
```plaintext
MSH|^~\&|HOSPITAL|ER|EMR|HOSPITAL|202503161200||ADT^A01|12345|P|2.3
PID|1||12345||John Doe||19850505|M|||123 Main St.^^Anytown^NY^12345||(555)555-5555|||EN|S|123456789|||Emergency
```

## Code Overview

### Patient Structure
The `Patient` structure holds essential information about a patient, including:
- **ID**: Unique identifier for each patient.
- **Name**: The name of the patient.
- **Symptoms**: Describes the patient's symptoms.
- **Priority**: A priority level assigned based on the patient's symptoms (Red, Yellow, Green).
- **Prescription Number**: A unique prescription number generated for each patient.
- **Next**: A pointer to the next patient in the linked list.

### Linked List
- The **linked list** is used to store and sort patient records based on their triage priority. 
- Lower priority numbers represent higher urgency.
- The linked list ensures that patients are sorted by priority, with the highest priority patients appearing first.

### Functions

- **`add_patient()`**:
    - Adds a new patient to the linked list.
    - The new patient is inserted at the correct position based on triage priority (sorted in ascending order).

- **`display_patients()`**:
    - Displays a list of all patients in the linked list.
    - It outputs each patient's details, including their ID, name, symptoms, priority, and prescription number.

- **`triage()`**:
    - Assigns a triage priority to the patient based on their symptoms.
    - Symptom categories:
        - **Red**: High priority (e.g., shortness of breath, chest pain)
        - **Yellow**: Medium priority (e.g., headache, fever)
        - **Green**: Low priority (e.g., minor injuries)

- **`validate_symptoms()`**:
    - Validates the entered symptoms to ensure they match a known list of recognized symptoms.
    - If the symptom is unrecognized, the user is prompted to enter a valid symptom.

- **`create_hl7_message()`**:
    - Converts a patient's data into **HL7** format for integration with electronic medical records (EMR) systems.
    - The HL7 message contains important patient data such as ID, name, and priority.

