# MIST 4610 Team SQL Snakes Group Project 1
# Team Members
1. Quincy Booth @[quincybooth](https://github.com/quincybooth) 
2. Lauren Johnston @[laurenjohnston](https://github.com/laurenjohnston)
3. Jordan Haynes @[jrosehaynes](https://github.com/jrosehaynes)
4. Ella Tedesco @[ellatedesco](https://github.com/ellatedesco)
5. Devin Dickey @[devin-dickey](https://github.com/devin-dickey)
# Problem Description
Our scenario is about creating a database for a healthcare center, like a hospital or clinic, to keep track of everything that goes on with patients, doctors, treatments, bills, and insurance. Think of it as a big system that makes sure all patient info is organized and accessible so that everything runs smoothly without getting lost or messed up. We want to be able to picture any information being inserted into a hospitals database, which includes patient, doctor, and employee information, as well as billing, treatment, and department data. A hospital is one of the busiest places in its community, and with this database, we hope to give more insight and simplify the daily workload.
# Data Model 
Our hospital management data model is designed to illustrate the core operations of a hospital, including patient care, billing, insurance, and healthcare providers. Each entity models an important aspect of hospital operations, and the relationships between these entities help to organize the flow of work throughout the hospital system.
The Department entity represents different areas of the hospital, such as Surgery, Cardiology, or Administration. Each single department has many healthcare providers working within it, so we established a one-to-many relationship between the Department and healthcareprovider entities. The Department table holds attributes like the department ID, name, and location, which are important for identifying where providers work.

The healthcareprovider entity stores information about the hospital staff, including their first name, last name, role (e.g., doctor, nurse), and years of experience. Each provider is assigned to a specific department, creating the many-to-one relationship with the Department table. The Boss relationship in the data model represents a one-to-many recursive relationship within the healthcareprovider entity. In this model, one healthcare provider can act as the boss of multiple other healthcare providers, but each healthcare provider can only have one boss. This is why the relationship is one-to-many: one healthcare provider (the boss) can supervise many others, but each healthcare provider reports to only one supervisor. The bossno attribute in the HealthcareProvider table references the empno (employee number) of another healthcare provider. For example, a senior doctor may supervise many junior doctors. This chain of command is recorded within the entity and allows for the reporting structure to be managed efficiently.

Since providers can treat multiple patients, and patients can see multiple providers, we created an associative entity called Patient_Provider to show this many-to-many relationship. The Patient_Provider table also includes start and end dates to track when a provider started and ended care for a specific patient, making it easier to manage their assignment history.

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
<img width="730" alt="Screenshot 2024-10-13 at 9 47 37 PM" src="https://github.com/user-attachments/assets/390c57db-bf26-447f-a858-61a24b5c3214">
<img width="722" alt="Screenshot 2024-10-13 at 4 24 16 PM" src="https://github.com/user-attachments/assets/72b1c10e-cadd-4450-ae4e-db5dcdc160af">
<img width="716" alt="Screenshot 2024-10-13 at 4 24 31 PM" src="https://github.com/user-attachments/assets/549e5e10-2f6b-4e85-9664-451b8f520e98">
<img width="720" alt="Screenshot 2024-10-13 at 4 25 00 PM" src="https://github.com/user-attachments/assets/9d04b806-02ac-4a50-b223-6587600e723c">
<img width="718" alt="Screenshot 2024-10-13 at 4 25 10 PM" src="https://github.com/user-attachments/assets/f7c7a8eb-2766-425e-9d8f-d20ac09b006c">
<img width="721" alt="Screenshot 2024-10-13 at 4 25 20 PM" src="https://github.com/user-attachments/assets/9164e659-8c5b-4e3e-a735-bd92fbadf49f">
<img width="722" alt="Screenshot 2024-10-13 at 4 26 22 PM" src="https://github.com/user-attachments/assets/95e98e7c-3bc2-43d0-987c-2aa2f38674ae">

# Queries

<img width="729" alt="Screenshot 2024-10-13 at 9 06 44 PM" src="https://github.com/user-attachments/assets/0d27b5ce-afd1-4bc7-8edc-294476d121b1">

1. Query 1 counts the number of new patients a healthcare provider sees on a given day. It is ordered by the number of new patients seen.

   <img width="527" alt="Screenshot 2024-10-13 at 5 01 38 PM" src="https://github.com/user-attachments/assets/31ceedf9-68f6-4137-8392-af9fea3929ab">
   
Relevance: A manager may want to know how many patients each healthcare provider treats daily to balance workloads. Having a reasonable work life balance is important for healthcare providers as they have crucial roles in society. In addition, knowing this information is beneficial for optimizing scheduling and assessing the performance of the healthcare providers. It allows them to see how many new patients each provider can have on a given day without being too overworked. 

2. Query 2 shows the names of each department heads, the number of employees that they have, and how long they have been working. In this particular query, only the department heads who have been working at the hospital for more than 10 years are displayed.

  <img width="366" alt="Screenshot 2024-10-13 at 5 02 12 PM" src="https://github.com/user-attachments/assets/7d022d81-6c6a-47c9-b5c3-b055ee4bd6e5">

Relevance: A manager may find this useful for assessing workflow distribution. By analyzing the number of employees that each department head is overseeing, it allows managers to visualize the weight of each department, and the number of employees they are overseeing. In addition, by filtering the number of years worked by a decade it allows managers to see which of their employees show company loyalty, which could be useful for pay raises or celebrations for their dedicated department heads.
  
3. Query 3 calculates the number of unique patients covered by each insurance provider and the total amount billed. Results are grouped by the insurance provider and ordered by the total amount     billed in descending order.
   
   <img width="312" alt="Screenshot 2024-10-13 at 5 02 54 PM" src="https://github.com/user-attachments/assets/58567636-dd3f-4296-bd6a-a4f05c85e291">

Relevance: This query allows hospital management to gain insights into the effectiveness and coverage of different insurance providers in terms of both the number of patients covered and the total amount billed. By identifying which insurance providers cover the most patients and generate the highest billing amounts, the hospital can prioritize partnerships and negotiations with these insurance companies. This information helps management optimize revenue streams by focusing on the most impactful insurer. By targeting high-billing insurers, the hospital can streamline billing processes and improve relationships with providers that are driving the most revenue.


4. Query 4 identifies all patients who have not been assigned a healthcare provider and then displays their ID and full name. 

<img width="647" alt="Screenshot 2024-10-13 at 5 35 59 PM" src="https://github.com/user-attachments/assets/0b43b4fe-0264-4c1b-93db-231f5cef43f5">

Relevance: This query identifies patients who have not yet been assigned a healthcare provider, ensuring that no one is left without necessary medical attention. This query helps managers address gaps in patient care assignments quickly, improving patient satisfaction. It also ensures that the hospital operates efficiently, with all patients properly attended to. 


5. Query 5 retrieves the names of treatments, their costs, and the first and last names of patients who received treatments that are more expensive than the average treatment cost. The results are ordered by treatment cost in descending order.

<img width="502" alt="Screenshot 2024-10-13 at 8 27 08 PM" src="https://github.com/user-attachments/assets/71134055-cbe3-47bb-86f4-0c96318b3b53">

Relevance: This query retrieves information on treatments that are more expensive than the average cost, along with the patients receiving them. This is useful for managing treatment costs and ensuring pricing strategies align with the hospital’s financial goals. It also allows managers to assess whether certain treatments are priced appropriately based on their complexity and necessity


6. Query 6 displays health care providers first name, last name, their total patients, their total treatment costs, and total billing amount garnered. The results are ordered in descending order of total treatment cost.

<img width="455" alt="Screenshot 2024-10-13 at 8 28 49 PM" src="https://github.com/user-attachments/assets/60983530-8bee-41b1-ab99-9eb2a358a926">

Relevance: This query identifies the top performing health care providers by providing information regarding how many patients they have worked on and the treatment costs that were administered. This can be useful if managers are looking to give incentives to top performing doctors or identify underperformance. 


SIMPLE QUERIES

7. Query 7 retrieves all patient details, along with their associated insurance information.

<img width="502" alt="Screenshot 2024-10-13 at 8 29 54 PM" src="https://github.com/user-attachments/assets/3ac5a4c3-5546-4b2f-84b2-5a2201a21e5b">

Relevance: This query provides a comprehensive overview of patient details along with their insurance information. This query helps managers streamline administrative processes by making it easier to access key patient data. It also improves customer service by ensuring that staff can quickly retrieve information when handling patient inquiries or insurance issues.

8. Query 8 is used to get all billing information for a specific patient.
<img width="493" alt="Screenshot 2024-10-13 at 5 26 41 PM" src="https://github.com/user-attachments/assets/2bd48fc2-cc18-4446-9fa3-b39870697e83">

Relevance: This query allows office employees to find different billing information for a patient easily without searching through multiple tables. This query also minimizes any errors and ensures that billing details are for the correct individual.

9. Query 9 is used to retrieve all treatments provided by a healthcare provider.
  <img width="473" alt="Screenshot 2024-10-13 at 5 28 14 PM" src="https://github.com/user-attachments/assets/956fba1b-25a6-44d9-a2ce-49642777ee6d">

Relevance: This query provides accurate tracking about separate treatments, making it easy for the healthcare center to keep track of their workload and contributions to patient care. Also, having these accurate records increases accountability and supports performance evaluations based on treatments administered.


10. Query 10 can be applied to count the number of unpaid bills in their financial system.

    <img width="237" alt="Screenshot 2024-10-13 at 5 29 24 PM" src="https://github.com/user-attachments/assets/c23fa738-52bb-4221-bb4b-fffc48b35584">

Relevance: This query is a huge time-saver for hospital employees since it delivers results instantly, and one does not have to manually count each unpaid bill. The billing department can prioritize different tasks, and keep track of what periods retain the most unpaid bills.

# Database Information
Name of databse: cs_dld36590

Stored procedure: 
CALL TP_Q1();  -- Executes the first query stored procedure
CALL TP_Q2();  -- Executes the second query stored procedure
CALL TP_Q3();  -- Executes the second query stored procedure
CALL TP_QN();  -- Executes the (N) query stored procedure 
