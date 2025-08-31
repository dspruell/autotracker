# AutoTracker application - maintenance feature support enhancement

This document provides guidance for the design and planning of and enhancement to add maintenance tracking and notification support the AutoTracker application. This enhancement is not part of the initial phase of the application design, but is to be planned and implemented at a later phase.

You are a software engineer and architect with experience and strong skills in design and implementation of full stack web applications in modern Python 3 with the Django MVC framework. You are implementing an enhancement feature set to add support for tracking maintenance activity and planning for vehicles in the application. This include sending notifications to users when maintenance is coming up or is due. Produce a design that can be implemented for a web application that meets the following requirements.

## General information and purpose

* Feature: vehicle maintenance tracking support.
* Enhancement purpose: expand the application to allow users to track maintenance events for vehicles.

## Features

* Associate and track a maintenance history, which is a collection of records related to maintenance events for any tracked vehicle.
* Each maintenance record should consist of several fields:
    * Description (brief)
    * Maintenance type
    * Scheduled or due date (to be used for reminders) (optional)
    * Scheduled or due at mileage (to be used for reminders) (optional)
    * Maintenance status
    * Completed date (optional)
    * Associated supplier/mechanic/dealership (optional)
    * Cost (optional)
    * Details (text, with markdown support)
    * Attached files
    * Metadata:
        * Record created timestamp
        * Record modified timestamp
        * Record created user
        * Record modified user
* The application should support reminders for maintenance events. Reminders should be based on attributes such as mileage or due date. Reminders should support email notifications to users or groups (using user profile emails). Reminders should be sent by default at these periods relative to the due date:
    * One week (7 days) before due date
    * One day before due date
    * The day of due date
* For all types of maintenance, the application should support uploading attachments for the maintenance event. Attachments may include images (e.g. photos or screenshots) or documents (e.g. quotes, estimates, invoices or receipts). Allowed attachment file types should be limited to image files (PNG, JPEG) and PDF.

Examples of the types of maintenance that might be tracked for a vehicle:

* Observation: a vehicle user has noticed that something is wrong with the vehicle.
* Routine maintenance visit: the user has completed routine maintenance and needs to record details, a date, and a cost.
* Repair: the user has completed a repair on the vehicle and needs to record details, a date, and a cost.

Maintenance status options:

* Incomplete
* Completed
