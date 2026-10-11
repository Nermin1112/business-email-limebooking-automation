# Business Email & Booking Automation

Automating business communication and appointment monitoring with **n8n**, email integrations, Telegram, and WhatsApp.

## Project Overview

This project addresses two operational challenges for a fitness and rehabilitation center: missed business inquiries and insufficient visibility into training attendance.

The workflows reduce the need to manually monitor incoming emails and booking notifications by delivering relevant alerts through messaging applications.

## 1. Business Email Notifications → Telegram

### The Problem

Business inquiries and other important messages arrived by email, but the business owner often could not review the inbox promptly due to a busy schedule. This created a risk of missing new client inquiries and important obligations.

### The Solution

An n8n workflow monitors incoming business emails, processes their content, formats a notification, and forwards it to Telegram.

**Workflow:**  
Business Email Trigger → Format Email Notification → Send Telegram Notification

**Benefits**
- Faster visibility into incoming business inquiries.
- Mobile notifications for important business emails.
- Less need to check the business inbox manually.

## 2. LimeBooking Appointment Monitoring → WhatsApp

### The Problem

Clients booked training sessions through LimeBooking. When only one person—or nobody—was registered, the business owner might not notice in time. A trainer could arrive for a session without enough participants.

### The Solution

An n8n workflow processes LimeBooking booking emails, extracts appointment details, and stores bookings in an n8n Data Table using a booking key based on the appointment date and time.

Twelve hours before a session, the workflow checks the number of bookings for that time slot. If fewer than two participants are registered, it sends a WhatsApp notification to the business owner with the appointment details and trainer information.

**Workflow:**  
Gmail Trigger → Filter Booking Emails → Extract Booking Details → Store Booking → Wait Until 12 Hours Before → Retrieve Bookings → Count Participants → Check Condition → Send WhatsApp Notification

**Business rule**
- **0 or 1 participant:** Send an alert.
- **2 or more participants:** Do not send an alert.

**Benefits**
- Earlier visibility into sessions with insufficient registrations.
- Less manual checking of booking emails.
- Better communication with the trainer and registered participant before a potentially cancelled session.

## Technologies

- n8n — workflow automation
- Gmail / email triggers — incoming message monitoring
- n8n Data Tables — booking data storage and lookup
- JavaScript — data extraction, transformation, and participant counting
- Telegram Bot API — business email notifications
- WhatsApp Business Cloud API — booking alerts

## Screenshots

1. Business Email → Telegram



2. LimeBooking → WhatsApp



3. Participant Count Check



4. WhatsApp Notification
   

5. Participant Count Check — Test



Privacy note: This project was developed for a real business use case. All personal names, phone numbers, booking details, and other identifying information shown in the screenshots are fictional. No credentials, access tokens, or private client data are included in this repository.
**Note:** All personal names, phone numbers, booking details, and other identifying information shown in the examples are fictional and used for demonstration. No credentials, access tokens, or private client data are included in this repository.

## Project Context

The workflows were developed for a real business use case. The screenshots use fictionalized example data to protect privacy.

