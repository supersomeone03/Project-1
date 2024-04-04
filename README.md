# MIST 4610 Project 1 (Group 1)
# Team Members: 
1. Charlie Kim [@charles8888](https://github.com/charles8888)
2. Gwen Wentworth [@gaw63800](https://github.com/gaw63800)
3. Caroline Cooper [@carolinetcooper6](https://github.com/carolinetcooper6)
4. Kishen Patel [@hubahakhtar](https://github.com/hubahakhtar)
5. Hubah Akhtar [@supersomeone03](https://github.com/supersomeone03)
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

[App Screenshot] (
