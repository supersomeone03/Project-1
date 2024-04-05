# MIST 4610 Project 1 (Group 1)
# Team Members: 
1. Charlie Kim [@charles8888](https://github.com/charles8888)
2. Gwen Wentworth [@gaw63800](https://github.com/gaw63800)
3. Caroline Cooper [@carolinetcooper6](https://github.com/carolinetcooper6)
4. Kishen Patel [@hubahakhtar](https://github.com/supersomeone03)
5. Hubah Akhtar [@supersomeone03](https://github.com/hubahakhtar)
# Problem Description:
Pretend you are the owner/operator of an emergency healthcare clinic needing to build a relational database. You hired some students from the MIST 4610 class at the University of Georgia to create the database for you. 
They need to know more about your organization to identify which entities, attributes, and relationships are important for you. Start by describing your business as a real client. 
# Data Modeling: 
**CHAT GPT CONVERSATION**

**You** 

Hi. I am the owner of an emergency healthcare clinic needing to build a relational database. I hired some students from the MIST 4610 class at the University of Georgia to create the database for my business. I need to know more about your organization to identify which entities, attributes, and relationships are important for this business data model 

**ChatGPT**

Sure, I'd be happy to help you identify important entities, attributes, and relationships for your emergency healthcare clinic database. To better assist you, could you provide more details about your organization and the specific functionalities you'd like to include in the database? For example: 

    What are the primary services offered by your emergency healthcare clinic? (e.g., urgent care, primary care, specialized care) 

    What types of healthcare professionals do you employ? (e.g., doctors, nurses, physician assistants) 

    What patient information do you need to store? (e.g., demographic information, medical history) 

    What types of medical equipment or resources do you need to manage? (e.g., medical supplies, medications, equipment maintenance) 

    Do you have any specific reporting or analytics requirements? (e.g., tracking patient outcomes, monitoring clinic performance) 

Once I have a better understanding of your organization's needs, I can help identify relevant entities, attributes, and relationships for your database. 

**You**

What do you think our needs should be as an emergency healthcare clinic? 

**ChatGPT** 

As an emergency healthcare clinic, your primary focus is on providing rapid and effective care to patients who require immediate medical attention. Based on this focus, here are some essential needs that your database should address: 

    Patient: 

    Entities: Patients 

    Attributes: Name, address, contact information, date of birth, insurance information, medical history, allergies, emergency contacts. 

    Relationships: Patients may have multiple visits or encounters. Each visit can have details such as date, time, reason for visit, attending healthcare provider, diagnosis, treatment provided, and discharge information. 

    Staff: 

    Entities: Doctors, nurses, physician assistants, etc.) 

    Attributes: Name, contact information, role/title, qualifications, work schedule. 

    Relationships: Staff members may have different roles, shifts, and responsibilities. Assignments to patient cases or visits should also be tracked. 

    Inventory: 

    Entities: Medical equipment, supplies, medications. 

    Attributes: Item name, description, quantity on hand, expiration date (for medications and perishable supplies), supplier information, cost. 

    Relationships: Track usage of items, restocking, and inventory levels. 

    Billing and Insurance: 

    Entities: Invoices, insurance companies. 

    Attributes: Invoice number, patient details, services provided, charges, insurance policy details. 

    Relationships: Link patient visits to billing information. Track payments, outstanding balances, and insurance claims. 

    Emergency Room Operations: 

    Entities: Rooms, beds, triage information. 

    Attributes: Room/bed number, availability, triage level. 

    Relationships: Assign patients to available rooms or beds. Track waiting times and prioritize patients based on urgency. 

    Quality Assurance and Reporting: 

    Entities: Quality metrics, incident reports. 

    Attributes: Type of incident, date/time, involved parties, severity, resolution. 

    Relationships: Link incidents to patient encounters for follow-up and improvement initiatives. Generate reports on patient outcomes, wait times, and clinic performance. 

These are just some initial considerations based on the typical needs of an emergency healthcare clinic. Depending on the specific requirements of your clinic, you may need to further customize the database schema and functionalities.

<img width="700" alt="MIST4610 DataModel" src="https://github.com/charles8888/Project-1/assets/150093221/b4bd19e0-1c2a-4258-85aa-45e592a25839">


# Data Dictionary

# 4 Simple Queries
**#1 Select the name and DOB for all patients born in 1999**

SELECT patient_Name, `date of birth`  
FROM patient 
WHERE `date of birth` regexp "1999";

![image](https://github.com/charles8888/Project-1/assets/150093221/3187ef6d-295d-4bb8-9716-130ee5ddecca)

**#2 Show the name of patient and show their invoice number and amount due**
 

SELECT patient_Name, Invoice_InvoiceNum, Charge 

FROM patient 

JOIN patient_has_Invoice ON patient_has_Invoice.patient_patientID = patient.patientID; 

![image](https://github.com/charles8888/Project-1/assets/150093221/468f40b7-3f79-4b6d-9b5e-b3f8b29db4cc)

**#3 Display all existing appointments along with the date and name of patient**
 

SELECT patient_Name, appointmentID, Date 

FROM patient 

JOIN Appointment ON Appointment.patient_patientID= patient.patientID; 

![image](https://github.com/charles8888/Project-1/assets/150093221/e0246757-6851-427b-8a7e-ffb78f3b8366)

**#4 Display all appointments for a particular staff member**
 

SELECT staffID, staffName, staff_schedule,appointmentID, Date 

FROM Staff 

JOIN Appointment ON Appointment.Staff_staffID = Staff.staffID 

WHERE staffID = "1552";

![image](https://github.com/charles8888/Project-1/assets/150093221/f3623064-bdf5-4ec7-8e41-44c30c9c164c)

# 6 Complex Queries

**#1 Display the patient name, DOB, and their review number and review description**
 

SELECT p.`date of birth`,p.patient_Name, r.reviewNum, r.Desc 

FROM patient p 

JOIN Review r ON p.patientID = r.patient_patientID; 

![image](https://github.com/charles8888/Project-1/assets/150093221/da083367-3724-4358-88d2-36ce806e2b27)

**#2 Find all appointments scheduled for 2027-10-21 along with the patient's name and the staff assigned to each appointment**
 

SELECT a.appointmentID, a.Date, p.patient_Name, s.staffName 

FROM Appointment a 

JOIN patient p ON a.patient_patientID = p.patientID 

JOIN Staff s ON a.Staff_staffID = s.staffID 

WHERE DATE(a.Date) ='2027-10-21'; 

![image](https://github.com/charles8888/Project-1/assets/150093221/bf893ef6-5a5c-4c61-9e19-f022d8dd542f)

**#3 Evaluate staff performance based on the number of appointments attended and the corresponding average patient reviews**
 

SELECT s.staffID, s.staffName,   

COUNT(a.appointmentID) AS num_appointments_attended,  

AVG(r.Rating) AS average_review_rating 

FROM Staff s 

JOIN Appointment a ON s.staffID = a.Staff_staffID 

JOIN Procedures pr ON a.appointmentID = pr.Appointment_appointmentID 

JOIN patient p ON p.patientID = a.patient_patientID 

JOIN Review r ON r.patient_patientID = p.patientID 

GROUP BY s.StaffID, s.StaffName; 

![image](https://github.com/charles8888/Project-1/assets/150093221/341b69eb-6225-44f0-a6c5-cb615fa8b32f)

**#4 Retrieve all appointments scheduled for Cesaro Troake along with their emergency contact details**
 

SELECT a.appointmentID, a.Date, e.EC_Phone, e.EC_Address, p.patient_Name 

FROM Appointment a 

JOIN patient p ON a.patient_patientID = p.patientID 

JOIN Emergency_Contact e ON p.patientID = e.patient_patientID 

WHERE p.patient_Name = 'Cesaro Troake’; 

![image](https://github.com/charles8888/Project-1/assets/150093221/3ff1a36b-c865-4257-bf2e-2f1274b4987e)

**#5 Determine the average number of appointments per staff member over a given period, and display those exceeding the average in descending order**
 

SELECT  

    Staff.staffID,  

    Staff.staffName,  

    COUNT(Appointment.appointmentID) AS NumberOfAppointments 

FROM Staff 

JOIN Appointment ON Staff.staffID = Appointment.Staff_staffID 

WHERE Appointment.Date BETWEEN '2025-08-25' AND '2027-11-03' 

GROUP BY Staff.staffID, Staff.staffName 

HAVING  

    COUNT(Appointment.appointmentID) > ( 

        SELECT (AVG(AppointmentCounts.NumberOfAppointments) - 0.1) -- Slight adjustment for precision 

        FROM ( 

            SELECT COUNT(Appointment.appointmentID) AS NumberOfAppointments 

            FROM Appointment 

            WHERE Appointment.Date BETWEEN '2025-08-25' AND '2027-11-03' 

            GROUP BY Appointment.Staff_staffID 

        ) AS AppointmentCounts 

    ) 

ORDER BY NumberOfAppointments DESC; 

![image](https://github.com/charles8888/Project-1/assets/150093221/bb8450cf-0f0d-4834-95eb-d068040b5ad4)

**#6 Identify patients with the largest balance due on their invoices with a balance exceeding $10,000. Order the balances due in descending order and display the total average balance due**
 

SELECT  

    patient.patientID, 

    patient.patient_Name, 

    Invoice.InvoiceNum, 

    SUM(Invoice.Balence_Due) AS TotalBalanceDue, 

    (SELECT AVG(Balence_Due) FROM Invoice) AS TotalAverageBalanceDue 

FROM patient 

JOIN patient_has_Invoice ON patient.patientID = patient_has_Invoice.patient_patientID 

JOIN Invoice ON patient_has_Invoice.Invoice_InvoiceNum = Invoice.InvoiceNum 

GROUP BY patient.patientID, patient.patient_Name, Invoice.InvoiceNum 

HAVING SUM(Invoice.Balence_Due) > 10000 

ORDER BY TotalBalanceDue DESC;

![image](https://github.com/charles8888/Project-1/assets/150093221/5c971d08-4572-4139-b6de-bb7e01cae213)
