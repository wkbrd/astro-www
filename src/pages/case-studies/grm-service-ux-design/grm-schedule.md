---
tags: ['grm', 'egs', 'r2c2']
path: /grm-service-ux-design/grm-schedule
date: Last Modified
layout: project:layouts/docs/docs-layout.astro
title: GRM Schedule
description: The GRM Schedule app allows operators to view and interact with the full schedule of contacts via a Timeline or List View.
---

[Launch GRM Schedule Sample App](https://grm-schedule-react.netlify.app) | [Design Materials and Source Code](/case-studies/grm-service-ux-design/grm-schedule/#design-materials-and-source-code)

Ground Resource Management (GRM) operations require ensuring that all the necessary equipment is available during the time windows when a target satellite is in range. Complicating this task is the fact that there are multiple simultaneous satellite contacts to manage, pieces of equipment that are shared amongst operational groups, and shifting priorities that can require a well-orchestrated schedule to be modified in-flight. Operators need to be able to monitor these impacts to the schedule and make the necessary modifications quickly to ensure that satellite operations can continue.

The GRM Schedule app is designed to allow operators to view and interact with the full schedule of contacts via a Timeline or List View. In addition, it allows the operator to manage the contacts in a single view, including the ability to add, view details, filter, modify, and delete contacts.

![GRM Schedule App](/img/case-studies/grm/grm-schedule-app.webp)

There are three main areas in the Schedule app: the Global Status Bar, the Contacts panel, and the Manage Contacts Pane. The key elements are described below, but you can find much more design and task flow detail in the GRM Design Specification and Wireframes documents. You can also launch the GRM Schedule Sample App to explore the design interactively.

![GRM Schedule App Details](/img/case-studies/grm/grm-schedule-app-details.webp)

## Global Status Bar

As outlined on the [About GRM Designs](/case-studies/grm-service-ux-design/about-the-grm-designs/) page, each of the apps in the GRM Suite is designed to occupy its own browser window, allowing operators to focus on the task at hand. But by virtue of being integrated into a suite, the apps share common functionality, such as a single login. Much of the shared functionality is provided in the [Global Status Bar](/components/global-status-bar/), an Astro component featured in all three apps. Status bars contain an App Switcher Menu, that allows operators to transition quickly from one GRM task flow to another, a [Clock](/components/clock/), and [Monitoring Icons](/components/icons-and-symbols/).

![GRM Schedule Global Status Bar Details](/img/case-studies/grm/grm-schedule-global-status-bar-details.webp)

1. **App Switcher Menu** - The App Switcher Menu allows the user to launch new instances of different GRM apps, sign in/sign out, and edit preferences.
2. **Global Clock** - Time is central to many GRM service task flows, so it is included in the Global Status Bar in all GRM apps.
3. **Monitoring Icons** - The Dashboard app includes Upcoming Contacts Allocated (UCA) status indicator and alert count.

## Contacts Panel

The GRM Schedule app presents operators with two alternative views of their contacts, a Timeline view or a List view. The Timeline view displays contacts as bars within a graphical layout with Ground Stations on the y-axis and time on the x-axis. The List displays contact data in a tabular format to facilitate quickly scanning multiple values and comparing values across contacts.

### Timeline View

In the [Timeline](/components/timeline/) view, contacts are plotted by ground station and antenna on the y-axis and time on the x-axis. The contacts are represented as bars, the length of which indicates the duration of the contact. This design, which is based on the Astro Timeline component, provides operators with a consolidated view of the time and status for all recent, current and future contacts in their system. To allow operators to focus in on particular elements of interest, Ground Station rows can be expanded to show individual antennas, the timeline can be filtered by contact status, or zoomed in/out to focus on a particular time range.

![GRM Schedule Timeline View](/img/case-studies/grm/grm-schedule-timeline-details.webp)

1. **Time Range Display** - Displays the time range for the current timeline view.
2. **Top Line Data Aggregates** - Displays total contacts and contact state counts.
3. **Zoom Controls** - Allows operators to focus on certain time range by zooming the timeline in or out.
4. **View Toggle** - Allows operators to switch between Timeline and List views.
5. **Ground Stations** - Ground stations can be collapsed or expanded to display contacts by antenna.
6. **Playhead** - Line marks current time with completed contacts to the left and future contacts to the right.

### List View

The List view shares many of the elements of the Timeline view including the time range display, data aggregates, and view toggle controls. The main difference is that contacts are displayed in a tabular layout, which allows operators to see settings for contacts without having to click on them in the timeline. As such, it enables comparison of settings across contacts to show, for example, which ones share a particular element in an equipment string.

![GRM Schedule List View](/img/case-studies/grm/grm-schedule-list-details.webp)

1. **Time Range Display** - Displays the time range for the current timeline view.
2. **Top Line Data Aggregates** - Displays total contacts and contact state counts.
3. **Manage Contacts Toggle** - Opens the Manage Contacts Pane to filter or add contacts.
4. **View Toggle** - Allows operators to switch between Timeline and List views.
5. **Contacts Table** - Contacts are listed in a large data table.

## Manage Contacts Pane

Operators can view additional detail on a contact by clicking on it in the timeline or row in the list view. This detail is presented in a [Modeless Pane](/patterns/modeless-panes/) that draws in from the right side of the window so operators aren’t taken away from the main app view. The data in the pane is presented in read-only form initially, but a Modify Contact button swaps the read-only view for an editable one, allowing operators to change the contact’s settings. Similarly, to schedule a new contact, operators can click on the Add Contact button which opens the pane to specify settings.

The image below shows the Contact pane for this Add Contact task flow. To see the view contact and modify contact variants of the pane, and more design and task flow details, download the [GRM Design Specification or Wireframes](/case-studies/grm-service-ux-design/grm-schedule/#design-materials-and-source-code). You can also interact with these elements in the [GRM Schedule Sample App](https://grm-schedule-react.netlify.app).

:::two-col
![GRM Schedule Manage Contacts Pane](/img/case-studies/grm/grm-schedule-manage-contacts-details.webp)

1. **Modeless Pane** - The functionality to manage contact appears in a pane on the right side of the browser window that is collapsed when the task is complete.
2. **Contact Settings** - The settings for the contact are specified using dynamic fields to guide the operator through the process.
3. **Action Buttons** - Once the required values have been specified and the contact is added, the pane closes and a confirmation message is displayed.
   :::

## Task Flow Example - Modify Contact

Below is an animated walkthrough of a representative task flow using the GRM Schedule app. In this scenario, an operator uses the GRM Schedule app to change the priority of an upcoming contact.

<img src="/img/case-studies/grm/grm-schedule-modify-contact.gif" alt="GRM schedule modify" />

## Design Materials and Source Code

Below are design and development resources to get you started on an app that supports GRM equipment management. Note that there are some discrepancies between the design documents and the [GRM Schedule Sample App](https://grm-equipment-react-ts.netlify.app) due to design improvements that were introduced late in the app development cycle.

:::table-overflow
| Resources | Description |
|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| [GRM Design Specifications (pdf)](/pdf/grm-specifications.pdf) | The GRM Design Specification contains information on use cases, task flows, UX research and wireframes for key features of the GRM App Suite. |
| [GRM Design Wireframes (pdf)](/pdf/grm-wireframes.pdf) | The GRM Design Wireframes document contains the complete set of wireframes (mid-fidelity renderings) of the screens designed for the GRM App Suite. |
| <button data-app="GRM" type="button" class="p-source-code-dialog-open">GRM Request Source Code Access</button> | The source code Git repository and other useful documentation for the GRM Dashboard App is hosted at github.com so that you can check it out in detail. |
:::
