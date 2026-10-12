# BrightSmile Dental Clinic — CRM & Workflow Automation Demo

A portfolio project demonstrating CRM pipeline design and workflow automation concepts in GoHighLevel (GHL), using fictional dental-clinic data.

**Project status:** Portfolio demo. The documentation distinguishes implemented configuration from observed tests and behavior that has not yet been verified. This is not a production deployment or a legal-compliance assessment.

## Project Overview

BrightSmile Dental Clinic is a fictional clinic used to demonstrate how inquiries can be organized in a CRM, how staff can identify incomplete contact records, and how follow-up work can be tracked through tasks.

The project combines a GoHighLevel CRM setup with spreadsheet-based workflow documentation and test cases.

## Project Goals

- Organize incoming inquiries in a clearly defined CRM pipeline.
- Apply tags to support lead classification and review.
- Use duplicate-opportunity prevention and document its observed behavior.
- Identify inquiries missing an email address or phone number and create a staff review task.
- Demonstrate follow-up task creation without automatically sending marketing messages.
- Record test results and clearly state limitations.

## Tools Used

- **GoHighLevel (GHL):** CRM pipeline, forms, contact tags, workflows, opportunities, and tasks.
- **Google Sheets / Excel:** Workflow logic, sample test leads, contact field definitions, and test-case documentation.
- **GitHub:** Project documentation and screenshots.

## Workflow Summary

### 1. New Lead Intake

**Trigger:** The BrightSmile Dental Inquiry Form is submitted.

**Configured behavior:**
- Apply the `brightsmile-new-inquiry` tag.
- Classify the inquiry type.
- For the `Braces Consultation` branch, apply the `brightsmile-priority-review` tag.
- Create an opportunity in the `New Inquiry` stage when duplicate-opportunity prevention allows it.

**Observed evidence:** Workflow execution logs showed the priority branch and the `Add Priority Review Tag` and `Create Opportunity` actions executing. A separate test followed the `None` branch and created an opportunity.

**Limitation:** Duplicate prevention was observed in specific tests. This does not prove that every possible duplicate scenario is handled.

### 2. Missing Information Review

**Trigger:** The BrightSmile Dental Inquiry Form is submitted.

**Condition:** The contact's email address is empty OR the phone number is empty.

**Configured behavior:**
- Apply the `brightsmile-missing-info` tag.
- Create a staff review task.

**Observed evidence:** A workflow test using a contact with an email address but no phone number entered the matching branch, applied the tag, and created a task. A test with both fields populated followed the `None` branch.

**Limitation:** The missing-phone scenario was tested. The missing-email-only scenario has not yet been tested.

### 3. Follow-up Task Creation

A separate workflow is configured to create a staff task when the `brightsmile-follow-up-needed` tag is added.

The task prompts staff to review the inquiry, check contact and follow-up status, and record the outcome.

**Evidence limitation:** The task-creation action was tested through a workflow test. The complete live tag-trigger path has not been verified end to end. This workflow remains a draft, so it should not be described as a fully deployed live automation.

## Screenshots

Upload your screenshots into the `screenshots/` folder using these exact filenames so they display correctly on GitHub.

### New Lead Intake — Workflow Builder

![New Lead Intake workflow builder](screenshots/01-new-lead-intake-builder.png)

### Missing Information Review — Workflow Builder

![Missing Information Review workflow builder](screenshots/02-missing-information-builder.png)

### CRM Pipeline Overview

![CRM pipeline and opportunities overview](screenshots/03-crm-pipeline-overview.png)

### New Lead Intake — Execution Logs

![New Lead Intake execution logs showing the priority branch](screenshots/04-new-lead-intake-execution-logs.png)

### Missing Information Review — Execution Logs

![Missing Information Review execution logs showing the branch, tag, and task actions](screenshots/05-missing-information-execution-logs.png)

### Follow-up Task — Workflow Test Evidence

![Follow-up task workflow test evidence](screenshots/06-follow-up-execution-logs.png)

*Note: The follow-up screenshot shows task-action test evidence, not proof that the complete live tag-trigger workflow has run successfully.*

## Supporting Documentation

The workbook contains the project overview, pipeline design, contact field definitions, fictional test leads, workflow logic, and test cases with observed results and known limitations.

[View the test and workflow documentation](documentation/brightsmile-github-documentation.xlsx)

## Testing Summary

| Test Area | Evidence | Status / Limitation |
|---|---|---|
| New lead intake | Workflow logs show tag and opportunity actions executed | Observed in tested scenarios |
| Priority classification | Braces Consultation branch applied the priority tag | Observed in a workflow execution |
| Duplicate-opportunity prevention | Repeated submission did not create an additional open opportunity in the observed test; a log showed the duplicate-opportunity action was skipped | Passed in observed scenario only |
| Missing phone number | Matching branch applied the missing-info tag and created a review task | Tested |
| Both contact fields populated | Workflow test followed the `None` branch without applying the missing-info tag | Tested |
| Follow-up task action | Workflow test log showed task creation and a task appeared in the task list | Action tested; live tag-trigger path not verified |
| Inquiry consent required | Form preview blocked submission when inquiry consent was unchecked | Tested in form preview |
| Marketing consent optional | Form preview allowed submission when inquiry consent was checked and marketing consent was unchecked | Tested in form preview; does not verify message suppression |
| Marketing-message suppression | No test verified suppression when marketing consent is absent or unknown | Not tested |
| Missing email only | No test completed for a contact missing only the email address | Not tested |
| Workflow failure handling | No genuine workflow failure scenario was observed | Not tested |

## Consent and Data Handling

The form separates required consent to be contacted about an inquiry and appointment arrangements from optional marketing consent.

- Inquiry consent is required by the form.
- Marketing consent is optional in the form.
- The form preview was tested for both consent scenarios described above.
- These checks do not establish legal compliance or prove that a separate marketing workflow suppresses messages when consent is absent or unknown.
- Use fictional records and reserved example email addresses for portfolio demonstrations.
- Do not publish real patient, customer, or personal contact information.

## CRM Pipeline

The active GoHighLevel pipeline uses four stages:

1. New Inquiry
2. Contacted
3. Appointment Booked
4. Attended

Completed/converted and lost outcomes are represented as opportunity statuses rather than additional active pipeline stages.

## Known Limitations and Next Steps

- Test the missing-email-only branch.
- Verify the complete live follow-up tag-trigger workflow if it is later published and safe to test.
- Add marketing-message suppression tests only if a separate marketing workflow is implemented.
- Continue documenting only observed results; do not describe planned or draft behavior as production-ready.
- Review all screenshots and exported files for private information before publishing.

## Disclaimer

BrightSmile Dental Clinic and its sample records are fictional. This project is intended for learning and portfolio demonstration only. It is not a live clinic system, a guarantee of automation reliability, or a legal, privacy, or healthcare-compliance review.
