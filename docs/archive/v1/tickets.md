
---

## Using the Golden Circle for Ticket Requirements

The **Golden Circle** framework, developed by Simon Sinek, emphasizes understanding the **Why**, **How**, and **What** of any task or project. Applying this framework to ticket creation ensures that every task aligns with overarching goals and delivers meaningful value.

### The Three Layers

1. **Why**:
    - **Purpose**: The fundamental reason for undertaking the task.
    - **Defined By**: Product Owner or task author when creating the ticket; refined by developers during refinement meetings.

2. **How**:
    - **Process**: The approach or methods used to achieve the purpose.
    - **Defined By**: Developers during refinement meetings.

3. **What**:
    - **Result**: The tangible outcome or deliverable.
    - **Defined By**: Product Owner or task author when creating the ticket; refined by developers during refinement meetings.

### Steps to Define Tickets Using the Golden Circle

1. **Define the Why**:
    - Articulate the purpose behind the ticket.
    - Explain how it aligns with the product vision or user needs.

2. **Define the What**:
    - Specify the deliverable or the functionality to be implemented.
    - Detail the expected outcome of completing the ticket.

3. **Define the How**:
    - Outline the approach or methods to achieve the desired outcome.
    - Include any technical specifications or design considerations.

4. **Refinement**:
    - Collaboratively refine the Why and What during refinement meetings.
    - Developers contribute to the How based on technical insights and feasibility.

### Roles and Responsibilities

#### Product Owner

- **Define Why and What**:
    - **Why**: Articulate the purpose and value of the ticket.
    - **What**: Clearly describe the deliverable or feature.
- **Prioritize Backlog**:
    - Ensure tickets align with business priorities and user needs.
- **Provide Clarity**:
    - Offer detailed user stories and acceptance criteria.

#### Task Author (Product Owner or Other Stakeholders)

- **Initial Ticket Creation**:
    - Draft the initial Why and What based on requirements.
- **Context Provision**:
    - Provide necessary background information and context for the ticket.

#### Developers (Engineers)

- **Define How**:
    - Propose technical solutions and approaches to implement the ticket.
- **Refine Why and What**:
    - During refinement meetings, question and enhance the Why and What to ensure clarity and feasibility.
- **Estimate Effort**:
    - Provide accurate estimates based on the proposed How.

#### Scrum Master

- **Facilitate Refinement Meetings**:
    - Ensure productive discussions around the Golden Circle components.
- **Remove Impediments**:
    - Address any obstacles that hinder the refinement or execution of tickets.
- **Promote Best Practices**:
    - Encourage the consistent use of the Golden Circle in ticket definitions.

### Example of a Golden Circle Ticket

**Title**: Implement User Authentication via OAuth2

**Why**:
- **Purpose**: Enhance security and provide a seamless login experience for users by allowing them to authenticate using their existing OAuth2 providers (e.g., Google, Facebook).
- **Alignment**: Supports the product vision of offering a secure and user-friendly platform, increasing user trust and reducing friction during sign-up/login processes.

**What**:
- **Deliverable**: Develop a user authentication system that integrates OAuth2 providers.
- **Outcome**: Users can log in using their Google or Facebook accounts, reducing the need to create and remember additional credentials.

**How**:
- **Approach**:
    - Research and select appropriate OAuth2 libraries compatible with our tech stack.
    - Design the authentication flow, including redirect URIs and token handling.
    - Implement backend endpoints to handle OAuth2 callbacks and token exchanges.
    - Update the frontend to include OAuth2 login options and handle authentication states.
    - Ensure secure storage of tokens and compliance with OAuth2 best practices.
    - Write automated tests to cover authentication flows and edge cases.
- **Technical Specifications**:
    - Use [Library Name] for OAuth2 integration.
    - Follow security guidelines outlined in the [Security Policy Document].

**Acceptance Criteria**:
- Users can successfully log in using Google and Facebook accounts.
- Authentication tokens are securely stored and managed.
- The system handles token expiration and refresh seamlessly.
- Comprehensive tests cover all authentication scenarios.
