---
title: Dedicated Mentoring Program
---

<head>
  <title>C4GT - Dedicated Mentoring Program</title>
 </head>

## Goal

Code for GovTech (C4GT) has conducted multiple rounds of Dedicated Mentoring Program (DMP) since
2022 where selected students and working professionals get an opportunity to contribute to critical
tech building blocks with the guidance of a dedicated mentor. They work closely with DPG builder and
adopter organizations on real world problem statements that have a population-scale social impact.

As part of the initiative, DMP is an experiential learning opportunity for technology enthusiasts
across the globe who are passionate about technology. Participants will solve population-scale
problems, work on live open-source projects and drive impact.

As part of DMP 2024, C4GT has launched the product usability & design track that aims to support
organizations by articulating design and product usability gaps and developing people-centered
solutions. Projects under this track will focus on improving usability and accessibility of the
products and is open for applicants currently enrolled in design or research programs or possess 0-2
years of professional experience.

## Product

In DMP 2023, contributors and mentors tracked project completion using a Vercel app and dedicated a significant amount of time to manually update markdown files to showcase project completion. This meant that progress tracking was not always up-to-date as and when required, and C4GT organizers were not able to intervene on time to resolve project bottlenecks. And in DMP 2024, with the project count increasing exponentially, the need for a smoother, more efficient tracking system had become paramount.

The revamped C4GT DMP CMS aimed to solve this by providing a platform for monitoring the progress of such open-source projects assigned to contributors during the Dedicated Mentoring Program(DMP) period of 3 months. The revamped Vercel app enabled easier and more efficient collaboration between contributors and mentors by linking to GitHub directly, while providing visibility to other relevant stakeholders. And a new second module, the dashboard, allowed administrators/organizers to set certain criterion and be flagged in time to swiftly resolve bottlenecks. 

## Tech

### Project Selection

Each organization submits project ideas through a Google Form. The information is vet by the C4GT
program team and shortlisted problem statement are sent for applications.

### Candidate Selection

Candidate selection is done through the [Unstop
platform](https://unstop.com/competitions/dedicated-mentoring-program-dmp-2024-code-for-govtech-932803).

### Contribution management

Once the candidate is selected for a problem statement and start contributing, the DMP Management
System comes into the picture. The DMP management system consists of a DMP documentation frontend
which gets updates from each project via github comments.

Flow:

1. DMP tickets are added into the database
2. We lookup comments for each ticket every few hours
3. We filter the comment by the mentor for `Weekly Goals`
4. We filter the comment by the contributor for `Weekly learnings`
5. We parse the ticket contents and display onto the frontend.

Modules:
* DMP Cron
* DMP API
* DMP FE

#### DMP Cron

This flask app runs a cron job at periodic intervals. This job pulls all the current DMP tickets,
loops through their comments and saves the relevant information into our database.

Repo: https://github.com/Code4GovTech/DMP-CMS-Backend-CRON

#### DMP APIs

This flask based API system reads information from our database and formats it in a way expected by
the FE. 

Repo: https://github.com/Code4GovTech/DMP-CMS-Backend-API

#### DMP FE

This docusaurus website contains a custom react page to load updates related to the DMP projects via
the DMP API.

Repo: https://github.com/Code4GovTech/dmp-documentation
