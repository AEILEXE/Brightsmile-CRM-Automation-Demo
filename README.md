# BrightSmile Dental Clinic — CRM & Workflow Automation Demo

A portfolio project demonstrating CRM configuration, lead management, workflow automation, and process testing using GoHighLevel and Google Sheets.

> **Project type:** Fictional business demo  
> **Status:** In progress — core CRM setup and initial workflow testing completed

## Project Overview

BrightSmile Dental Clinic is a fictional dental clinic used to demonstrate how a small business can organize incoming inquiries, track potential patients, identify incomplete contact information, and create follow-up tasks.

The goal is to build a structured CRM workflow that reduces manual organization, improves lead visibility, and helps staff manage inquiries more consistently.

This project is being developed as a hands-on portfolio demonstration of CRM setup, workflow logic, automation testing, and digital operations.

## Tools & Technologies

- **GoHighLevel (GHL):** CRM, inquiry form, opportunity pipeline, workflow automation, and task management
- **Google Sheets:** Workflow documentation, sample lead tracking, and test-case records
- **GitHub:** Project documentation and versioned portfolio evidence

## Features Implemented

### 1. Inquiry Form

Created a BrightSmile Dental Inquiry Form with:

- First name and last name
- Email and phone number
- Inquiry type selection
- Required inquiry-consent checkbox
- Optional marketing-consent checkbox
- Form submission confirmation message

The form was tested in preview mode to confirm that submission is blocked when the required inquiry-consent checkbox is unchecked and allowed when marketing consent is left unchecked.

These tests verify form behavior only; they do not establish legal compliance or verify marketing-message suppression.

### 2. Lead Pipeline

Configured a four-stage opportunity pipeline:

1. New Inquiry
2. Contacted
3. Appointment Booked
4. Attended

Opportunity outcomes, such as Won or Lost, are handled separately from the four pipeline stages.

The pipeline is intended to help staff track an inquiry from initial contact through appointment attendance.

### 3. New Lead Intake Workflow

**Status: Published**

Configured workflow components:

- Trigger: Form Submitted, filtered to the BrightSmile Dental Inquiry Form
- Action: Apply the `brightsmile-new-inquiry` tag
- Action: Create an opportunity in the New Inquiry stage
- Duplicate-opportunity prevention: Enabled

**Observed test results:**

- Live form submissions entered the workflow.
- The new-inquiry tag action executed successfully.
- An opportunity was created in a test run.
- In a subsequent run, opportunity creation was skipped with the message: `Can not create duplicate opportunity for the contact.`

The observed results demonstrate the configured intake workflow and duplicate-opportunity protection in the tested scenarios. They do not establish that every possible duplicate-contact scenario is prevented.

### 4. Missing Information Review Workflow

**Status: Draft**

Configured workflow components:

- Trigger: Form Submitted, filtered to the BrightSmile Dental Inquiry Form
- Condition: Email is empty OR Phone is empty
- Action on the matching branch: Apply the `brightsmile-missing-info` tag

Both the matching and non-matching branches were tested using GoHighLevel's workflow test feature.

The missing-phone scenario was verified. The missing-email scenario and automatic execution from a live form submission have not yet been verified.

### 5. Follow-up Reminder Workflow

**Status: Draft**

Configured workflow components:

- Trigger: Contact Tag added
- Trigger tag: `brightsmile-follow-up-needed`
- Action: Create a follow-up task
- Task assignment: Configured user account
- Task timing: One day later at 9:00 AM, with weekend skipping disabled

The task action executed successfully during a workflow test. The resulting task's title, description, assignment, and due date were inspected.

Automatic enrollment from a live tag change has not yet been verified.

## Testing & Validation

A Google Sheets test log documents 11 test cases, including:

- Valid new lead submission
- Repeat submission and duplicate-opportunity prevention
- Missing contact information
- Existing-contact submission
- Opportunity stage changes
- Follow-up task creation
- Consent-related form validation
- Workflow failure handling
- Marketing-consent form behavior

Testing distinguishes between successful observations, manually performed actions, workflow-test results, and scenarios that remain untested.

Not all test cases are passed. Marketing-message suppression and genuine workflow failure handling remain unverified.

## Current Limitations

This is an evolving portfolio project. Current limitations include:

- The Missing Information Review workflow remains in Draft.
- The Follow-up Reminder workflow remains in Draft.
- Live-trigger behavior for those two draft workflows has not been verified.
- Marketing-message suppression when consent is absent or unknown has not been tested.
- Genuine workflow failure handling has not been tested.
- Additional reporting, integrations, and operational safeguards may be added in future iterations.

## Planned Enhancements

The next development phase may include:

- More complete lead-routing and follow-up logic
- Better handling of missing information and unsuccessful workflow actions
- Appointment-related automation and follow-up processes
- CRM reporting and performance dashboards
- API or webhook integration, if supported by the chosen tools and implemented
- Additional test cases and stronger end-to-end validation
- Sanitized screenshots and supporting technical documentation

Planned enhancements will be documented as they are implemented and tested.

## Project Documentation

Supporting materials will be added as the project develops:

- Workflow logic documentation
- Test-case records
- Selected screenshots of the actual GoHighLevel configuration
- Updated implementation notes and test results

## Disclaimer

BrightSmile Dental Clinic is a fictional business created for educational and portfolio purposes. Contact records and examples are demonstration data, not real patient records.

This project demonstrates CRM configuration and workflow automation. It is not a production-ready clinical system, and it does not claim legal or regulatory compliance.

---

**Project focus:** CRM Setup · Workflow Automation · Lead Management · Process Testing · Digital Operations
