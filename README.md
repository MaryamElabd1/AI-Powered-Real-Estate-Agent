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

[▶️ Watch Buyer Verification & Registration Demo](./buyer-verification-registration.mp4)

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

---

### 6. Reservation Expiry Reminder

The system supports reservation expiry reminders to help customers keep track of their reservation deadlines.

Customers can receive reminders before their reservations expire, helping them take the necessary action before the reservation reaches its expiry date.

**Workflow:**

`Active Reservation → Check Expiry Date → Approaching Expiry → Send Reminder`

**Flow:**

<img width="713" height="604" alt="reservation-expiry-reminder-flow" src="https://github.com/user-attachments/assets/ec5936f0-5f1c-447f-9859-50ca9a4f0420" />


#### 🎥 Demo

The following video demonstrates the main functionalities of the AI-powered real estate agent in a single interaction.

The demonstration includes:

* Buyer verification
* Viewing existing reservations
* Exploring available real estate projects
* Checking available units within a specific project
* Searching for units based on specific requirements
* Receiving alternative unit recommendations when an exact match is unavailable

[▶️ Watch the Demo](./real-estate-agent-FunctionPart1-demo.mp4)
  
