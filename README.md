# AI-Powered Real Estate Agent

An AI-powered real estate assistant built using **Salesforce Agentforce** to help customers explore real estate projects, find suitable units, view property details, verify buyers, and manage reservations through a conversational interface.

## Project Overview

The AI-Powered Real Estate Agent is a conversational AI solution developed using Salesforce Agentforce to automate common real estate customer interactions.

The agent enables customers to:

* Explore real estate projects and available units
* Search for units based on their requirements
* View detailed unit information
* Verify buyer information
* Create and manage reservations
* Cancel existing reservations

The goal of the project is to provide a seamless conversational experience while reducing the need for manual intervention in routine real estate processes.


## Key Features

* 🔎 **Unit Search & Matching** — Find suitable units based on customer requirements and preferences.
* 🏢 **Project & Unit Information** — Provide information about real estate projects and available units.
* 👤 **Buyer Verification** — Verify buyer information before performing reservation-related operations.
* 📋 **Reservation Management** — View and manage existing reservations.
* ✅ **Create Reservation** — Create a reservation for a selected unit.
* ❌ **Cancel Reservation** — Cancel an existing reservation through the conversational agent.
* ⏰ Reservation Expiry Reminders — Send reminders to customers before their reservation expires.
* 💬 **Conversational AI** — Interact with the real estate agent using natural language.

## Functionalities & Demo

The following sections demonstrate the main functionalities of the AI-powered real estate agent through flow diagrams, screenshots, and an end-to-end video demonstration.

### 1. Buyer Verification & Registration

Before handling customer requests, the agent verifies the customer's identity using their mobile number.

Both **Buyer Verification** and **Buyer Registration** are implemented using custom **Apex services/actions** integrated with Agentforce.

The verification and registration process includes:

* Checking the available `ChannelPhoneNumber` when provided.
* Normalizing the phone number and country code before verification.
* Verifying the customer against existing buyer records using an Apex service.
* If no matching buyer is found, offering the customer the option to create a new account.
* Collecting the required registration information, including First Name, Last Name, Phone Number, Email, National ID, and Buyer Type.
* Creating the buyer account using the Apex registration service.
* Confirming successful registration and continuing with the customer's original request.

**Workflow:**

`Customer Message → Phone Number Detection → Phone Normalization → Buyer Verification`

`Buyer Found → Verification Successful`

**OR**

`Buyer Not Found → Account Registration → Buyer Account Created → Continue Original Request`

#### 🎥 Demo

A short demonstration of the buyer verification and registration flow.

https://github.com/user-attachments/assets/cf7b0003-186f-4786-ae3e-cf95bdb90102

---

### 2. Show Reservations

The agent allows verified buyers to view their existing reservations through a conversational interaction.

When the customer asks to view their reservations, the agent retrieves the relevant reservation information and presents it to the customer.

**Workflow:**

`Customer Request → Buyer Verification → Retrieve Reservations → Display Reservation Information`

**Flow:**

<img width="762" height="630" alt="ShowReservations" src="https://github.com/user-attachments/assets/a9af88b1-d6be-4732-ac94-67a5f01fbeb5" />

---

### 3. Show Projects

The agent can provide information about the available real estate projects through a conversational interaction.

When the customer asks about available projects, the agent retrieves the relevant project information and presents the available projects.

**Workflow:**

`Customer Request → Retrieve Projects → Display Available Projects`

**Flow:**

<img width="510" height="585" alt="show-projects-flow" src="https://github.com/user-attachments/assets/80f73476-b177-4dbc-b9a8-5e61f1ed88b1" />

---

### 4. Available Units

The agent allows customers to check the available units within a specific real estate project.

The customer can ask about available units for a particular project, and the agent retrieves and presents the relevant available units.

**Workflow:**

`Customer Request → Identify Project → Retrieve Available Units → Display Available Units`

**Flow:**

<img width="584" height="631" alt="available-units-flow" src="https://github.com/user-attachments/assets/b1f4b7fe-f4bd-404e-9849-73bede2e82ff" />

---

### 5. Unit Search & Matching

The agent can search for suitable units based on specific customer requirements.

Customers can provide preferences such as the desired project, unit type, price range, number of bedrooms, or other available unit criteria.

The agent analyzes the provided requirements and searches for matching units.

If an exact match is not available, the agent identifies and recommends alternative units that are close to the customer's requested criteria.

**Workflow:**

`Customer Requirements → Analyze Requirements → Search Available Units → Match Criteria`

`Exact Match Found → Display Matching Units`

**OR**

`No Exact Match → Find Closest Alternatives → Recommend Suitable Units`

**Flow:**

<img width="567" height="632" alt="unit-search-matching-flow" src="https://github.com/user-attachments/assets/81b2ada4-c9c7-4b78-9604-9cde333b8472" />


#### 🎥 Demo

The following video demonstrates the main functionalities of the AI-powered real estate agent in a single interaction.

The demonstration includes:

* Buyer verification
* Viewing existing reservations
* Exploring available real estate projects
* Checking available units within a specific project
* Searching for units based on specific requirements
* Receiving alternative unit recommendations when an exact match is unavailable

https://github.com/user-attachments/assets/9a42fd38-1e54-4196-b069-e1ceac4d624d

---
### 6. Create Reservation

The agent allows verified buyers to reserve a selected unit through a conversational interaction.

The customer selects a specific unit and provides the required reservation details, including the **deposit amount** and **reservation hold period**.

Before creating the reservation, the agent validates the unit's availability to prevent double booking. If the unit is already reserved or on hold, the agent informs the customer and can help identify an alternative available unit.

Once the reservation is successfully created, the agent confirms the **reservation number** and **hold expiry date**.

**Workflow:**

`Select Unit → Specify Deposit & Hold Period → Validate Unit Availability → Create Reservation → Reservation Confirmation`

**Flow:**

Step 1 — Unit Availability Validation
The flow retrieves the requested unit and checks its availability. If the unit is unavailable, the process stops; otherwise, it continues by checking for any existing active reservation.

<img width="1165" height="627" alt="Step1" src="https://github.com/user-attachments/assets/2bfd5221-b6ed-4c1a-acf2-28c4dd6c4c5f" />

Step 2 — Check Reservation & Create Booking
The agent checks for any existing reservation, validates the unit’s availability, and retrieves relevant pricing information. If the unit is already reserved, the agent provides an appropriate message and suggests similar available units. Otherwise, it creates the new reservation, updates the unit status, handles any creation errors, and returns the booking confirmation.

<img width="1276" height="634" alt="Step2" src="https://github.com/user-attachments/assets/86140714-cc46-4cda-9259-3f9ec62df471" />


---

### 7. Reservation Expiry Reminder

The agent supports reservation expiry reminders to help customers keep track of their reservation deadlines.

After completing the customer's main request, the agent checks whether there is a reservation approaching its hold expiry date. If a reservation is due to expire within **3 days**, the agent provides a reminder to the customer before the conversation ends.

This functionality is handled through the **Reservation Expiry Reminder** action and works as a supporting step after the customer's main request has been completed.

**Workflow:**

`Completed Customer Request → Check Reservation Expiry → Expiry Within 3 Days → Send Reminder`

**Flow:**

<img width="713" height="604" alt="reservation-expiry-reminder-flow" src="https://github.com/user-attachments/assets/ec5936f0-5f1c-447f-9859-50ca9a4f0420" />

#### 🎥 Demo — Reservation & Expiry Reminder

Demonstrating the reservation process and automated reminders for expiring reservations.

https://github.com/user-attachments/assets/d6d93799-65ff-4aaa-b307-d5bcaab6baa7

---
### 8. Update Reservation

The agent allows verified buyers to update supported details of an existing reservation through a conversational interaction.

Customers can request changes to their **deposit amount** or **hold expiry date**. The agent identifies the requested modification, collects the new value, and updates the reservation using the verified buyer information.

If the update is successful, the agent returns the confirmation message to the customer. If the update fails, the agent clearly communicates the reason for the failure.

**Workflow:**

`Customer Request → Buyer Verification → Identify Reservation → Determine Modification → Update Reservation → Confirmation`

**Flow:**

***Update by Unit Code***

The agent retrieves the unit, finds its active reservation, and updates the requested reservation detail, such as the hold date or deposit.

<img width="732" height="608" alt="Update-By-Unitcode" src="https://github.com/user-attachments/assets/71b89362-3c52-4fc2-a3c1-08fe4b9db476" />

***Update by Reservation Number***

The agent retrieves the buyer's active reservations, identifies the requested reservation, and proceeds with the update.

<img width="366" height="496" alt="Without-Unitcode" src="https://github.com/user-attachments/assets/e42524bd-11f4-48eb-bfb7-a4f227d65dae" />

---

### 9. Cancel Reservation

The agent allows verified buyers to cancel an existing reservation through a conversational interaction.

When the customer explicitly requests cancellation, the agent identifies the reservation using the provided **reservation number** or **unit code**. The reservation is then validated before the cancellation is performed.

If the cancellation is successful, the agent confirms that the reservation has been cancelled. If the reservation cannot be found or the cancellation fails, the agent provides an appropriate response.

**Workflow:**

`Customer Request → Buyer Verification → Identify Reservation → Validate Reservation → Cancel Reservation → Confirmation`

**Flow:**


#### 🎥 Demo — Update & Cancel Reservation

The following video demonstrates both the reservation update and cancellation flows through a conversational interaction.

YOUR_VIDEO_URL

---

