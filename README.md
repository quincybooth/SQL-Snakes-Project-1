# MIST 4610 Team SQL Snakes Group Project 1
# Team Members
1. Quincy Booth
2. Lauren Johnston lej26429@uga.edu
3. Jordan Haynes jrosehaynes/SQL-Snakes-Project-1
4. Ella Tedesco @ellatedesco
5. Devin Dickey
# Problem Description
Our scenario is about creating a database for a healthcare center, like a hospital or clinic, to keep track of everything that goes on with patients, doctors, treatments, bills, and insurance. Think of it as a big system that makes sure all patient info is organized and accessible so that everything runs smoothly without getting lost or messed up. We want to be able to picture any information being inserted into a hospitals database, which includes patient, doctor, and employee information, as well as billing, treatment, and department data. A hospital is one of the busiest places in its community, and with this database, we hope to give more insight and simplify the daily workload.
# Data Model 
Our hospital management data model is designed to illustrate the core operations of a hospital, including patient care, billing, insurance, and healthcare providers. Each entity models an important aspect of hospital operations, and the relationships between these entities help to organize the flow of work throughout the hospital system.
The Department entity represents different areas of the hospital, such as Surgery, Cardiology, or Administration. Each single department has many healthcare providers working within it, so we established a one-to-many relationship between the Department and healthcareprovider entities. The Department table holds attributes like the department ID, name, and location, which are important for identifying where providers work.

The healthcareprovider entity stores information about the hospital staff, including their first name, last name, role (e.g., doctor, nurse), and years of experience. Each provider is assigned to a specific department, creating the many-to-one relationship with the Department table. Since providers can treat multiple patients, and patients can see multiple providers, we created an associative entity called Patient_Provider to show this many-to-many relationship. The Patient_Provider table also includes start and end dates to track when a provider started and ended care for a specific patient, making it easier to manage their assignment history.

The Patients entity stores key personal information like patient first and last name, date of birth (DOB), and gender. Since a patient can receive multiple treatments, and a treatment can be administered to multiple patients, we established a many-to-many relationship between the Patients and Treatment entities. This relationship is managed by the associative entity Patient_Treatment. The Patient_Treatment table includes the patient ID, treatment ID, and the date the treatment was administered. This ensures we can accurately track which treatments each patient received and when, while also recording the details of the treatments being provided to multiple patients.

Each treatment is also linked to the healthcare providers who administered it, which is represented by the many-to-many relationship between Treatment and healthcareprovider through the Provider_Treatment associative entity. The Treatment entity contains attributes such as treatment name, cost, and dosage to capture detailed information about the treatments given to patients. The Provider_Treatment table helps link each treatment to the specific provider responsible for administering it.

To handle financial information, we included the Billing entity. Each patient can have multiple billing records, which establishes a one-to-many relationship between Patients and Billing. The Billing table stores attributes like the billing ID, amount charged, bill status (paid or unpaid), and the payment method used, which helps track the financial aspects of a patient's care. Additionally, we created a Billing_Treatment table to manage the many-to-many relationship between billing and treatment records, allowing us to link multiple treatments to a single bill or distribute billing costs across several treatments.

The Insurance entity tracks the insurance policies associated with patients. Since a patient can have multiple insurance policies over time, and an insurance policy can cover multiple patients, we established a many-to-many relationship between Patients and Insurance. This relationship is managed through the Patient_Insurance table, which contains attributes such as the patient ID, insurance ID, and relevant policy details like the start and end dates of coverage and a policy number. The Patient_Insurance table connects each patient to their specific insurance policies. The Insurance entity itself holds information such as the coverage type and insurance name. 

While this model covers essential data related to patient care, provider assignments, treatments, billing, and insurance, it does not handle hospital inventory management or real-time provider scheduling. These aspects of hospital management are outside of our data model scope. 
In summary, our hospital management data model effectively organizes and tracks the relationships between departments, healthcare providers, patients, treatments, billing, and insurance. Most importantly, it supports the necessary data used in hospital operations and helps with efficient management of patient care and financial records.

<img width="946" alt="Screenshot 2024-10-13 at 5 08 59 PM" src="https://github.com/user-attachments/assets/4074e95a-ce33-4482-b3ff-e77e52306013">


# Data Dictionary 
<img width="724" alt="Screenshot 2024-10-13 at 4 21 14 PM" src="https://github.com/user-attachments/assets/64ad7f76-0ce5-451a-a2c9-c02f03ba16c8">
<img width="720" alt="Screenshot 2024-10-13 at 4 21 35 PM" src="https://github.com/user-attachments/assets/213bb0a5-6997-4e45-8967-02a4aec3db9c">
<img width="722" alt="Screenshot 2024-10-13 at 4 22 01 PM" src="https://github.com/user-attachments/assets/db5fa85d-b9c2-4d17-949d-658a58b55b6f">
<img width="721" alt="Screenshot 2024-10-13 at 4 22 22 PM" src="https://github.com/user-attachments/assets/99c4f48f-eee3-4cfc-afab-ae294822ca74">
<img width="722" alt="Screenshot 2024-10-13 at 4 24 02 PM" src="https://github.com/user-attachments/assets/7f9bbfdc-8850-4a12-97e2-6a09d61d382d">
<img width="722" alt="Screenshot 2024-10-13 at 4 24 16 PM" src="https://github.com/user-attachments/assets/72b1c10e-cadd-4450-ae4e-db5dcdc160af">
<img width="716" alt="Screenshot 2024-10-13 at 4 24 31 PM" src="https://github.com/user-attachments/assets/549e5e10-2f6b-4e85-9664-451b8f520e98">
<img width="720" alt="Screenshot 2024-10-13 at 4 25 00 PM" src="https://github.com/user-attachments/assets/9d04b806-02ac-4a50-b223-6587600e723c">
<img width="718" alt="Screenshot 2024-10-13 at 4 25 10 PM" src="https://github.com/user-attachments/assets/f7c7a8eb-2766-425e-9d8f-d20ac09b006c">
<img width="721" alt="Screenshot 2024-10-13 at 4 25 20 PM" src="https://github.com/user-attachments/assets/9164e659-8c5b-4e3e-a735-bd92fbadf49f">
<img width="722" alt="Screenshot 2024-10-13 at 4 26 22 PM" src="https://github.com/user-attachments/assets/95e98e7c-3bc2-43d0-987c-2aa2f38674ae">

# Queries

1. Count the number of new patients a healthcare provider sees on a given day- order by the number of new patients in descending order
   <img width="527" alt="Screenshot 2024-10-13 at 5 01 38 PM" src="https://github.com/user-attachments/assets/31ceedf9-68f6-4137-8392-af9fea3929ab">
2. Show the name of each department head, how many employees they have, and how long they’ve been working, only for department heads who have been employed for more than 10 years
  <img width="366" alt="Screenshot 2024-10-13 at 5 02 12 PM" src="https://github.com/user-attachments/assets/7d022d81-6c6a-47c9-b5c3-b055ee4bd6e5">
  
3. Calculate the number of unique patients covered by each insurance provider and the total amount billed. Results are grouped by the insurance provider and ordered by the total amount     billed in descending order.
   
   <img width="312" alt="Screenshot 2024-10-13 at 5 02 54 PM" src="https://github.com/user-attachments/assets/58567636-dd3f-4296-bd6a-a4f05c85e291">
   
4.Find all Patients who have not been assigned a healthcare provider, display their ID and full name.


5.Write an SQL query that retrieves the names of treatments, their costs, and the first and last names of patients who received treatments that are more expensive than the average treatment cost. The results should be ordered by treatment cost in descending order



6. blah blah blah


SIMPLE QUERIES

7.Query to retrieve all patient details, along with their associated insurance information:


8. jajaja
9. jajajaja
10. jajajjaa
