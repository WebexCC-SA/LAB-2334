# LAB 1: - Proactive Journeys

## About this lab

At Cisco, our customer experience (CX) strategy is centered around
achieving the specific outcomes our customers value the most. The CX
Business Unit has crafted a strategy that showcases Cisco’s unique
capability to meet these outcomes through three primary pillars:
Proactive Journeys, AI Agents, and Human Agents. Understanding how each
pillar supports our overarching CX strategy is critical for delivering
our solutions with confidence, credibility, and a consultative approach.

Our goal is to equip you with comprehensive expertise in this growth
sector for Cisco and the market at large. While we will explore each
pillar separately in the corresponding Labs, the bootcamp is designed to
build a strong foundation that applies broadly across various
technologies and solutions, reinforcing Cisco’s position as a
differentiated partner for businesses seeking to enhance their customer
experience.

In this lab, the focus is on the first pillar: Proactive Journeys. This
session will cover a broader spectrum of technical features and concepts
essential for developing effective proactive strategies. These
strategies can significantly enhance efficiency and helps to reduce the
cost to serve for the business significantly.

Our three key CX software workloads work together to reimagine customer
experience:

 -   Proactive Journeys – Anticipate customer needs and proactively address
    issues before they arise.

 -   AI Agents – Automate and resolve common queries efficiently, reducing
    wait times and improving satisfaction.

 -   Human-AI Collaboration – Equip human agents, supervisors, and analysts
    with AI-driven insights and assistance, enhancing empathy and service
    quality.

## Lab Objective

This lab introduces you to the following concepts: -

1.  Design and build Webex Connect workflows that satisfy for the
    following journey requirements:

    - System triggered flows

    - User initiated flows

    - One-way transactional flows

    - Two-way automated flows

    - Channel fallback logic

    - Consent management

    - Social hours

    - Custom variables

2.  Leverage messaging templates to streamline business user priorities
    without risking the technical components of a journey.

3.  Leverage flow-driven REST API’s to personalize the customer
    experience as well as push and pull key response and tracking data
    to augment the value of and maintain client-side systems.

4.  Leverage Journey Data Services to support a contextualized history
    of interactions and touchpoints with any given end-user.

## Background

The proactive journey pillar of our CX portfolio is powered by WxConnect
and it’s powerful low code no code flow builder and its relationship
with external integrations, one-way and two-way SMS scenarios, internal
CX-focused cross architecture such as JDS, and the flow builder’s
out-of-the-box functions that allow platform users to perform otherwise
complex development tasks in a configuration-based approach. These
features combined offer brands an enormous advantage to rapidly develop,
execute, and iterate on CX communications journeys – whether they’re
proactive in nature, end-user initiated, or self-service oriented (also
referred to as structured two-way engagements).

Lab 1 focuses on creating a structured flow that is a streamlined,
systematic method to automate communications. It involves:

- Clear Objectives: Defined goals for each communication campaign.

- Sequential Steps: Ordered actions based on customer or system
  interactions.

- Decision Points: Branching paths depending on customer or system
  responses.

- Standardization: Reusable templates for consistent messaging.

- Documentation: Visual tools to map out and manage flows (ie., the flow
  builder canvas).

- Control Mechanisms: Analytics to monitor and optimize performance.

The structured flows offer a more guided experience for the customer.

When this lab is completed, we will have built our first workflow, that
handles a two-way structured self-help delivery use-case for the Cisco
Store. The persona chosen for this lab is an existing customer and the
use-case represented is an online purchase of a Core Trio QI Charger
(shown in the picture below) for delivery to an address already on file
with the store’s source system that is referred to as CRM in this lab
guide.

<img src="../assets/L1Images/media/image1.png"
style="width:5.17361in;height:3.53043in"
alt="A white device with a round button AI-generated content may be incorrect." />

The lab will follow these steps in chronological order: -

1.  Let us assume that you are the customer that just purchased the
    above charger from Cisco Store. The system will trigger a
    notification which will trigger a workflow responsible for
    proactively notifying the customer, that their purchase was
    successful and is being processed, and it indicates the details
    surrounding the order in a highly personalized manner.

2.  Then the workflow will build on the previous step and inform the
    customer about the processed order and informs that the order is
    about to be shipped, offering the customer the ability to either
    confirm their delivery details are correct or tweak the delivery
    experience.

    -  Throughout this workflow, you will be asked to request data from
        source system (CRM) to personalize the messaging and associated
        logic steps involved. You will also be asked to update the CRM
        based on the selections made by your end-user.

    -  Throughout this workflow, key milestones in the customer’s
        journey are logged to capture contextual bread crumb trail so
        that the customer’s interactions with respect to this journey
        can be harnessed for improved awareness on the brand-side that
        will benefit both the brand’s operational efficiency and the
        customer’s overall experience.

3.  The last workflow will be a SMS triggered workflow to allow the
    customer’s to initiate contact with the brand in a self-help
    capacity at any given time to check on their order status.

**Due to the time constraints, we will not build the entire flow from
scratch, instead we will copy a pre-built flow and modify the variables
to match the Pod assigned to you.** 



## Best Practices to consider

When designing workflows, there are typically a few considerations that
are rules of thumb. Outside of these, it is up to the brand to structure
the flow to get a customer from point A to B.

- The flows should minimize system overhead; this will reduce points of
  failure and time to complete the transaction.

  - Example: - In proactive journeys, ensuring we have customer’s
    consent to message them is not only important – it is the law! To
    ensure we’re able to respect this business condition, Webex Connect
    has a built-in [Contact
    Policy](https://help.webexconnect.io/docs/contact-policy) module.
    This is completely redundant if the customer already has a source of
    truth such as a CRM that they prefer to use instead. That said, the
    Contact Policy is a valuable ‘last line of defense’ option if the
    customer doesn’t trust their data or would simply prefer to use our
    ‘out of the box’ feature.

- Reporting and metrics are important to consider up front – make sure
  that whatever you’re building, and its corresponding flow-design, is
  architected in a manner that allows you to accurately and efficiently
  collect whatever key data points are valuable towards the use-case and
  the measurement of the solution.

  - NOTE: For the purposes of this lab, we will be leveraging Journey
    Data Service as our repository for key insights regarding the
    customer’s progression.

- A single flow does not need to incorporate every single decision
  branch, API call, or interaction with an end user. Flows can trigger
  other flows at any step, meaning you can break up your use-case into
  more manageable pieces or even incorporate “Catch All” flows that
  triage any inbound message or keyword and funnels it down to the
  appropriate corresponding sub flow(s).

- Consider cost – By leveraging proactive journey’s, brands can serve
  their customers with the lowest cost per interaction compared to
  talking to a human agent.-->

## Cisco Store Use-Case

First, let us understand the use-case or customer journey that is part
of the workflow.

1.  The first leg of the use case is triggered when the customer
    completes the purchase of the Core Trio Qi charger.

    <img src="../assets/L1Images/media/image2.png"
    style="width:6.26806in;height:1.91736in"
    alt="A diagram of a server AI-generated content may be incorrect." />

    -   The business is going to send a transactional notification indicating
        their purchase is confirmed and being processed for shipment.

        <!-- -->

    -   As soon as the customer completes the purchase, the CRM is updated
        with the customer information, and it triggers a notification request
        to be sent to the customer confirming the purchase.

2.  The second leg of the use case is triggered when the customer order
    is shipped.

    <img src="../assets/L1Images/media/image3.png"
    style="width:6.26806in;height:2.09792in"
    alt="A diagram of a diagram AI-generated content may be incorrect." />

    -   The notification is triggered when the order is shipped with the
        delivery date and the address. This notification includes the option
        to manage the order that includes changing the delivery date and safe
        zone designation to deliver the package.

## Goal 1: - CRM Setup

1.  To begin the lab, scan the QR code that is provided to you by the
    proctor


2.  After you have answered the questions, you will receive the “POD”
    assignments with all the credentials that is required for this lab.

3.  Open a web browser and navigate to <http://crm.cxocoe.us> and login
    with the “CRM Login and Password” that was provided to you in step
    \#2

    <img src="../assets/L1Images/media/image4.png"
    style="width:6.26806in;height:3.23542in"
    alt="A screenshot of a login screen AI-generated content may be incorrect." />

4.  The first step is to create the customer record in the CRM. For this
    session, we are going to use a “API” end point as our CRM. To add
    your customer record, open a web browser and go to
    <http://crm.cxocoe.us>. The webpage displayed is as shown below.

    <img src="../assets/L1Images/media/image5.png"
    style="width:6.26806in;height:2.90972in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Click on “Post CRM Data” at the top navigation bar or click on “Go”
    button displayed within Post CRM Data contact card.

    <img src="../assets/L1Images/media/image6.png"
    style="width:6.26806in;height:2.90278in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  Add the data to the following fields: -

    <img src="../assets/L1Images/media/image7.png"
    style="width:6.26806in;height:4.13403in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    - First Name: - **Enter your First name or a fake first name** 

    - Last Name: -  **Enter your Last name or a fake last name**

    - Phone Number: - **Enter your mobile number including the country code (For ex:- if you are in US and your phone number is +14088881111, please enter 14088881111), this should be a number that can receive SMS messages**

    - SMS Consent: - **Yes (for this lab, we will pretend to have obtained customer consent)**

    - Order ID: - **This will be automatically set to your phone number**

    - Product Name: - **Core Trio QI Charger**

    - Delivery Address: - **Any fake address**

    - Delivery ETA: - **any date in future**

    - Delivery Status: - **for the first part of the lab, set this to “Not Shipped”**

    - Safe Location: - **Set to either “Front Door”, “Back Door” or “Garage”**

    - Time Zone: - **America/Chicago**

    - Alternate Date 1: - **Set it to any date after DeliveryETA date**

    - Alternate Date 1: - **Set it to any date after DeliveryETA date that is different than Alternate Date 2**

7.  After entering the data, click “submit order data” button to create
    the CRM record.

    <img src="../assets/L1Images/media/image8.png"
    style="width:6.26806in;height:3.00278in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    <img src="../assets/L1Images/media/image9.png"
    style="width:6.26806in;height:2.17708in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  If the data entry is successful, http response will show the status
    code “200 ok” as shown below.

    <img src="../assets/L1Images/media/image10.png"
    style="width:6.26806in;height:2.75139in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

9. To view the data, click on “Get CRM Data” in the top menu

    <img src="../assets/L1Images/media/image11.png"
    style="width:6.26806in;height:1.46736in"
    alt="A screen shot of a computer AI-generated content may be incorrect." />

10. In the “Get CRM data” screen, enter the phone number that was used
    to create the record in step \#3 and click on “Get Data” button.
    Observe the result and verify the data that was entered. We will use
    this data as our CRM record for all parts of our lab.

    <img src="../assets/L1Images/media/image12.png"
    style="width:6.26806in;height:3.93194in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

11. In case you need to make any changes to the CRM data or record,
    click on “Update CRM Data” in the top menu.

    <img src="../assets/L1Images/media/image13.png"
    style="width:6.26806in;height:1.15208in"
    alt="A screen shot of a computer AI-generated content may be incorrect." />

12. To update any field, enter the phone number for the order Id. Click
    the drop down “Field to Update” to select field that needs to be
    updated and enter the updated information in the “New Value”. For
    Ex: - In the below image, we are going to update the “Alternate Date
    1” from 4/01/2025 to 4/21/2025. In case, there is a need to update
    multiple fields, you can update one field at a time.

    <img src="../assets/L1Images/media/image14.png"
    style="width:5.90435in;height:3.7125in"
    alt="A screenshot of a update record AI-generated content may be incorrect." />

    <img src="../assets/L1Images/media/image15.png"
    style="width:5.9038in;height:5.08696in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

13. Now try step \#10 – Get CRM data and validate the changes are
    updated.

## Goal 2: - Get Started with the flow

Due to time constraints, for this goal you are going to copy an existing
flow and modify it. Lab 2 will be focused on you building it so please
don’t worry about not getting to put together the building blocks for
the customer journey in this lab.

By now, you should have the “POD” assignments and the credentials for
the pod. We are going to use the admin account for this part of the lab.
The admin account is of the format admin\<pod#\>@ciscolivelab.wbx.ai,
where pod# is the pod number assigned to you. Ex: - Pod 22, the admin
account will be <admin22@ciscolivelab.wbx.ai>

Let us get started!

1.  Open a web browser and go to <https://admin.webex.com> and login
    with the assigned admin credentials for your pod.

2.  On successful login, you should be on the Contact Center Overview
    landing page as shown below.
     
     **Note:** There will be an error message on the bottom right which can be
        ignored. It is an error message to let us know that the user was not
        added to few groups and can be ignored.

    <img src="../assets/L1Images/media/image16.png"
    style="width:6.26806in;height:2.98403in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />
     

3. Click on “Webex Connect” under quick links. It will cross launch a
    new tab and display “Services”. 
     
     **Note:** There will be an error message on the bottom right which can be
        ignored. It is an error message to let us know that the user was not
        added to few groups and can be ignored. 

    <img src="../assets/L1Images/media/image17.png"
    style="width:6.26806in;height:2.98403in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

4. Click on “Search Services” and type in Pod \<your pod number\> and
    press “Enter”. In my example below, my Pod \# is 60

    <img src="../assets/L1Images/media/image18.png"
    style="width:6.26806in;height:2.94931in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

5. Click on Pod 60 and you will see the “Dashboard” as shown below.

    <img src="../assets/L1Images/media/image19.png"
    style="width:6.26806in;height:2.93125in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

6. Click on “Flows”.

    <img src="../assets/L1Images/media/image20.png"
    style="width:6.26806in;height:2.93125in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

7. There should be a starter flow called “Lab1 Starter Flow”. We will
    create a flow by copying the starter flow. Click on “Create Flow”.

    <img src="../assets/L1Images/media/image21.png"
    style="width:6.26806in;height:1.87014in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

8. The next screen presented is to “Create Flow”.

    <img src="../assets/L1Images/media/image22.png"
    style="width:6.26806in;height:4.12569in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

9. Add the following details: -

    - Flow Name: - *Enter the name with Pod# Lab1 Proactive Journey. In my
    example below, the pod assigned is 60 and my flow name is “Pod60 Lab1
    Proactive Journey”.*

    - Method: *click the drop-down selection and select “Copy from existing
    flow”.*

    - Select Flow: *click the drop-down selection and select “Lab1 Starter
    Flow”.*

    - Click “Create”.

    <img src="../assets/L1Images/media/image23.png"
    style="width:6.26806in;height:2.94167in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

  

10. The proactive journey gets triggered when the CRM triggers the
    notification to a webhook. The next screen presented is to
    “Configure Webhook”.

    <img src="../assets/L1Images/media/image24.png"
    style="width:6.26806in;height:4.07569in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

11. Under “Configure webhook settings to trigger this flow”, select
    “Create new event” and add the following details.

    - Name: *Pod# Lab1 Trigger. In the below example, the pod assigned is 60
    and the name is set to “Pod60 Lab1 Trigger”.*

    - Example Data: Copy and paste the following JSON code.

    - Note: - JSON is case sensitive so please make sure to pay attention to
    the JSON and maintain the same format.

    ```
    {
    "orderId" : ""
    }
    ```

    <img src="../assets/L1Images/media/image25.png"
    style="width:6.26806in;height:4.03889in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

12. Click on Parse button. This will create “orderId” as a variable that
    can be used throughout the flow.

    <img src="../assets/L1Images/media/image26.png"
    style="width:6.26806in;height:4.05208in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    > After the “Parse” button is clicked, observe the variable created
    > under the “Parsed Variables(0)”. This method can be used to pass any
    > number of custom variables from CRM or external data sources when
    > triggering a flow. The variables created can also be accessed by
    > clicking on “Output Variables”.

    <img src="../assets/L1Images/media/image27.png"
    style="width:6.26806in;height:4.03542in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    <img src="../assets/L1Images/media/image28.png"
    style="width:6.26806in;height:4.04375in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

13. We will rename the “Configure Webhook” to “Trigger Proactive
    Journey” by clicking on the pencil icon as shown below. Enter the
    name and click the check mark to save the edits.

    <img src="../assets/L1Images/media/image29.png"
    style="width:6.26806in;height:4.03542in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    <img src="../assets/L1Images/media/image30.png"
    style="width:6.26806in;height:4.05in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

14. Click “Save” to save the node configuration.

15. Click “Save” at the top menu to save the flow. When the flow is
    saved, the “Errors & Warnings” message will pop up and we will work
    towards fixing the errors in the upcoming steps, but we will ignore
    the warnings. It is strongly recommended that warnings are addressed
    in a production environment for optimal experience.

    <img src="../assets/L1Images/media/image31.png"
    style="width:6.26806in;height:3.01667in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    <img src="../assets/L1Images/media/image32.png"
    style="width:6.26806in;height:3.00417in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

## Goal 3 – Configuring the flow

Orient yourself with the canvas/UI in Webex Connect and some key
tools/functions (if you find yourself struggling, try our documentation
page too @ help.webexconnect.io):

<img src="../assets/L1Images/media/image33.png"
style="width:6.26806in;height:2.96319in"
alt="A screenshot of a computer AI-generated content may be incorrect." />

1.  The first step is to identify the “SMS” nodes and modify them. The
    SMS node enables the brand to send outbound SMS message to their
    customers. The SMS node is indicated in the flow as below

    <img src="../assets/L1Images/media/image34.png"
    style="width:1.48611in;height:1.27778in"
    alt="A blue square with text in it AI-generated content may be incorrect." />

2. The flow consists of 10 SMS nodes and each of the SMS node must be
    modified to include the SMS number. The power of WxConnect is its
    ability to create dynamic variables that makes the flow reusable. We
    will leverage a dynamic variable that stores the SMS number and
    assign this variable to the SMS nodes.

    <img src="../assets/L1Images/media/image35.png"
    style="width:6.26806in;height:2.84722in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

3. Open SMS node \#1 as shown in step \#2 by double clicking on the SMS
    node to open the configuration settings of this node.

    <img src="../assets/L1Images/media/image36.png"
    style="width:6.26806in;height:4.04028in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

4. Observe the image from the above step and note that “From Number” is
    blank. This is one of the errors reported when you save the flow. As
    mentioned earlier in the guide, we will be using a variable called
    “yourAssignedSMSNumber” to dynamically store the number. This
    variable is already created for you. To add this variable, click on
    “From Number” to select the field and then expand the “Custom
    Variables” on the right of the node as shown below and then click on
    “yourAssignedSMSNumber” variable to add it to the “From Number”
    field. Click save to save the node config.

    <img src="../assets/L1Images/media/image37.png"
    style="width:6.26806in;height:4.05in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    <img src="../assets/L1Images/media/image38.png"
    style="width:6.26806in;height:4.04028in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

5. Repeat the above steps for all the other 9 SMS nodes.

6. Click save on the top right after completing step \#5.

7. Let us now open the configuration of SMS node \#3 to understand the
    “Template” concept.

    <img src="../assets/L1Images/media/image39.png"
    style="width:6.26806in;height:2.62639in"
    alt="A diagram of a network AI-generated content may be incorrect." />

8. In this node configuration, observe that we are not configuring the
    SMS message to be sent directly in the node, instead we are
    utilizing messaging templates.

    <img src="../assets/L1Images/media/image40.png"
    style="width:6.26806in;height:4.06458in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    Typically, you can proceed in one of two ways – you can simply
    populate the message in the body of the SMS node, or you can
    leverage templates. For the purposes of this lab, we’ll be going
    down the template path so that you not only understand how they work
    but also because it is often the case that customers don’t use the
    same teams to devise messaging content and technical integrations /
    wiring up of a solution. Thus, templates allow business users or
    marketeers to still control and own a piece of the build process
    (that they can iterate on later) without impacting IT and creating
    backlog for simple copy changes.

9. To check out the templates, please save your work and navigate out
    of the flow canvas by clicking the carrot (or chevron, if you
    prefer) that navigates you back into your service – top left of the
    page:

    <img src="../assets/L1Images/media/image41.png"
    style="width:6.26806in;height:3.01181in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    Then click on the wrench in the menu panel to the left and select
    ‘Templates’.

    <img src="../assets/L1Images/media/image42.png"
    style="width:6.26806in;height:2.54097in"
    alt="A screen shot of a computer AI-generated content may be incorrect." />

    Click on any pre-configured template to view the template
    configuration.

    <img src="../assets/L1Images/media/image43.png"
    style="width:6.26806in;height:2.6375in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    <img src="../assets/L1Images/media/image44.png"
    style="width:6.26806in;height:3.97708in"
    alt="A screenshot of a chat box AI-generated content may be incorrect." />

10. Now that we have seen the templates and the purpose of templates,
    let us get back to modifying the flow by clicking on the tile window
    on the left.

    <img src="../assets/L1Images/media/image45.png"
    style="width:6.26806in;height:2.6375in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    Search the Pod and click on the Pod \# that is assigned to you.

    <img src="../assets/L1Images/media/image18.png"
    style="width:6.26806in;height:2.94931in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    <img src="../assets/L1Images/media/image20.png"
    style="width:6.26806in;height:2.93125in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    There will be two flows in your service, click on the flow “Pod#
    Lab1 Proactive Journey”.

11. As next step we must modify the “receive” nodes in the flow to add
    the sms numbers. Open each receieve node explicitly and click save, to save
    the configuration.Receive nodes facilitate the brands to receive message or message replies 
    from their customers. Receive nodes in the flow can be identified by the below image.

    <img src="../assets/L1Images/media/image46.png"
    style="width:1.26389in;height:1.55556in"
    alt="A blue and green square with arrows and a blue rectangle with a blue arrow AI-generated content may be incorrect." />

12. There are 5 receive nodes in the flow as identified below.

    <img src="../assets/L1Images/media/image47.png"
    style="width:6.26806in;height:2.30833in"
    alt="A diagram of a network AI-generated content may be incorrect." />

13. Open “Receive” node \#1 identified in step \#12 by double clicking
    on the node to verify the configuration and click save.

    <img src="../assets/L1Images/media/image48.png"
    style="width:6.26806in;height:4.04444in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

14. Open all other “Receive” nodes to make sure the variable is set for
    the “Number” field and click save on each node.

15. If any of the “receive” node is not populated with the variable as
    shown below

    <img src="../assets/L1Images/media/image49.png"
    style="width:6.26806in;height:4.04236in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    Click on the Number field and select “—Dynamic--” as shown below.

    <img src="../assets/L1Images/media/image50.png"
    style="width:6.26806in;height:4.04792in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    Now expand the “Custom variables” located on the right hand side of
    the node and select “yourAssignedSMSNumber” as shown below.

    <img src="../assets/L1Images/media/image51.png"
    style="width:6.26806in;height:4.03056in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    Now click on Keyword and select “\*”. The “\*“ keyword allows to
    accept any message. Click “save” to save the configuration.

16. Click “Save” on the top right corner to save the entire flow and
    observe the errors and warnings. There should be no errors reported,
    however there will be warnings that we will ignore for this lab.

    <img src="../assets/L1Images/media/image52.png"
    style="width:6.26806in;height:2.99861in"
    alt="A computer screen shot of a diagram AI-generated content may be incorrect." />

17. We are all set to put the flow into production. Click on “Make
    Live”.

    <img src="../assets/L1Images/media/image53.png"
    style="width:6.26806in;height:2.99722in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

18. Make live configuration is presented, where we will assign the
    actual SMS number to the dynamic variable. Click on “Numbers” and
    select the SMS number that you received in the text by scanning the
    QR code along with your credentials. In the example below, the
    assigned SMS number to Pod60 is 14087862126.

    <img src="../assets/L1Images/media/image54.png"
    style="width:6.26806in;height:4.05in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    Click on “Numbers” field and select the number that was assigned to
    your pod.

    Note: - Please check the box against your assigned number only.

    <img src="../assets/L1Images/media/image55.png"
    style="width:6.26806in;height:4.04861in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    <img src="../assets/L1Images/media/image56.png"
    style="width:6.26806in;height:4.05625in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    Type your number in the format 1+\<phonenumber\> as shown in the
    image below

    <img src="../assets/L1Images/media/image57.png"
    style="width:6.26806in;height:4.04375in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

19. Click “Make Live” to put the flow in production. Please note, the
    flow will take approximately 1 to 2 mins to be live. The status
    initially will show “Publishing” and will change to “Live” to
    indicate it is live and in production.

    <img src="../assets/L1Images/media/image58.png"
    style="width:6.26806in;height:1.40208in"
    alt="A screen shot of a computer AI-generated content may be incorrect." />

## Goal 4 – Testing the Proactive Journey

It is now time to test the flow that we put in production. As mentioned
previously in the lab guide, the flow that we built is triggered by
certain notifications from the CRM or system of record updates. We will
simulate this by creating this notification and keep your mobile phones
ready, let us begin testing.

1.  Open the flow that we put into production and double click on the
    first node “Trigger Proactive Journey”.

    <img src="../assets/L1Images/media/image59.png"
    style="width:6.26806in;height:2.90417in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    In the configuration window, locate the field named “Webhook URL”
    and the url is of the format
    <https://hooks.us.webexconnect.io/events/XXXXXXXXX>. Copy the last
    part of the URL “XXXXXXXXXX” to test.

    <img src="../assets/L1Images/media/image60.png"
    style="width:6.26806in;height:4.03403in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  Open a web browser and login to <http://crm.cxocoe.us> with the
    credentials provided.

    <img src="../assets/L1Images/media/image61.png"
    style="width:6.26806in;height:3.41111in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />


3. Click on “Kick off Proactive Flow”.

    <img src="../assets/L1Images/media/image62.png"
    style="width:6.26806in;height:5.13819in"
    alt="A screenshot of a webpage AI-generated content may be incorrect." />

    - Phone Number: *Enter your mobile number with country code. Ex: -
    14081111111*

    - Webhook Id: *Enter the copied text from step \#1*

    Then click on “Start Flow” to trigger the proactive journey.

    <img src="../assets/L1Images/media/image63.png"
    style="width:6.26536in;height:4.00909in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

4. The flows provide debug capability to identify any issues with the
    configuration. The debug can be accessed by clicking on bug icon
    that is located on the right of the flow.

    <img src="../assets/L1Images/media/image64.png"
    style="width:6.26806in;height:2.76111in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    The debug window contains list of transaction id’s that the flow has
    executed. Click on the appropriate transaction id to debug.

    <img src="../assets/L1Images/media/image65.png"
    style="width:6.26806in;height:2.33889in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    The debug output is encrypted by default. Click “Decrypt Logs” to
    view the logs in plain text.

    <img src="../assets/L1Images/media/image66.png"
    style="width:6.26806in;height:2.99375in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

5. You should have received a proactive notification on your mobile
    phone notifying you the purchase of a Core Trio Qi charger!

    <img src="../assets/L1Images/media/image67.png"
    style="width:3.15455in;height:6.98125in"
    alt="A screenshot of a phone AI-generated content may be incorrect." />

6. Let us now create the shipped notification. Open web browser and
    login to <http://crm.cxocoe.us> with the provided credentials.

7. Click on “Update CRM Data”

    <img src="../assets/L1Images/media/image68.png"
    style="width:6.26806in;height:3.82569in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    The field to update is Delivery Status and the value is “shipped”.
    Then click “Update Record”.

    <img src="../assets/L1Images/media/image69.png"
    style="width:6.26806in;height:4.23333in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

8. Now let us test again by repeating Step \#3

    <img src="../assets/L1Images/media/image62.png"
    style="width:6.26806in;height:5.13819in"
    alt="A screenshot of a webpage AI-generated content may be incorrect." />

9. Verify the messages that you received on your mobile phone

    <img src="../assets/L1Images/media/image70.png"
    style="width:6.26806in;height:2.81111in"
    alt="A phone with a message AI-generated content may be incorrect." />

10. The test can be repeated for changing the date if desired.

## Goal 5 – The Open Door Policy (OPTIONAL GOAL)

- Although this lab focuses on 'proactive' engagement – where the brand
  uses its insights to initiate contact at, or even before, a customer's
  moment of need – it's also crucial that customers can respond to these
  communications. Just as you might reply to a personal update with
  questions, customers should be able to engage in a dialogue with the
  brand following any initiated contact.

- When a brand sends a notification, you should have the capability to
  respond to it, asking any questions that fall within the scope of your
  relationship with the brand, regardless of the notification's original
  intent.

- Although there are different ways for solving this; structured flows
  vs scripted AI vs autonomous AI vs directing the query to a human on
  the brand-side, Cisco maintains a strong advantage in its ability to
  facilitate this ‘open door policy’ for any of our customers.

- Our final objective within this lab is precisely this, albeit through
  the lens of structure flows.

- As you will have likely noticed, in the final confirmation message we
  defined for the end-user, there was a call to action where we stated,
  “*If at any time you would like to check on your order status, you can
  text STATUS to this number.*” This now means that we need a way of
  capturing that keyword and acting on it.

    - NOTE: Keywords are not the only way of capturing user-initiated
        contact. We could instead go the route of a CatchAll flow that is
        literally open to any input from anyone and then filters input
        accordingly and funnels them down appropriate paths based on the
        governing business rules at play. We’re taking the keyword approach
        here to honor the ‘structured’ experience but please note this is
        not the only way, nor is it necessarily the recommended way
        depending on the use-case or breadth of technology at play within
        the solution.

- This one is relatively simple – here is what it should look like when
  you’re done:

    <img src="../assets/L1Images/media/image71.png"
    style="width:6.26806in;height:2.27569in"
    alt="A diagram of a computer process AI-generated content may be incorrect." />

Let us build this simple flow:

1.  From the dashboard of your service, click on “Create Flow”.

    <img src="../assets/L1Images/media/image72.png"
    style="width:6.26806in;height:2.22222in"
    alt="A screenshot of a chat AI-generated content may be incorrect." />

2. In the “Create Flow” shown below, add the details.

    <img src="../assets/L1Images/media/image73.png"
    style="width:6.26806in;height:4.62292in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    - Flow Name: *Pod# Reactive Status Catch All*

    - Method: *New Flow*

    - Click “Create”.

      <img src="../assets/L1Images/media/image74.png"
      style="width:6.26806in;height:4.65694in"
      alt="A screenshot of a chat AI-generated content may be incorrect." />

3. In “Select Trigger Category”, select “SMS” as the channel.

    <img src="../assets/L1Images/media/image75.png"
    style="width:6.26806in;height:5.375in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

4. Once you’ve selected SMS, the “Configure SMS Event” window appears.
    Here you can define the keyword and/or conditions for the inbound
    message (known in industry terms as an MO – mobile Originated
    message).

    <img src="../assets/L1Images/media/image76.png"
    style="width:6.26806in;height:4.06319in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

5. Select your assigned SMS number from the “INCOMING NUMBER”.

    - Select \* as the KEYWORD and then click to “VERIFY”. The verify button
    checks if there are other flows that utilize the same keyword and if
    it does, there will be an error displayed. You’ll see that instead of
    an actual keyword value in the ‘keyword’ field, we’ve placed an
    asterisk \* which indicates to the corresponding flow and session that
    anything on the SMS channel addressed to the respective SMS number
    should be captured by this flow. Effectively, a ‘CatchAll’ at this
    point, however, as indicated in the screenshot to follow, we’ve put
    some boundaries up around this – indicating that the governing logic
    for the flow should only allow it to trigger on behalf of an entry if
    those conditions are met *and* if there are no other live sessions
    (meaning that if an end-user is in a separate flow’s session that
    corresponds to the same number, and they enter valid conditional
    keywords defined here, such as ‘status’ or ‘order’, this flow will NOT
    execute).

    - NOTE: The secondary conditions defined as ‘equalsignorecase’ are
        important to further enforce the rules governing if/when this flow
        gets triggered

    - To add conditions, check conditions and this will bring up the
        conditions box. Select “sms.message” under “Choose Field” and
        “equalsignorecase” under “Choose Condition”. For input value, type
        “status”.

    - Click “OR” button to add “OR” operator. Then select “sms message”
        and “equalsignorecase” as field and condition respectively. Type in
        “order” for the value. This ensures that the inbound message to the
        SMS number will trigger a flow if it matches either “status” or
        “order” in the keyword.

    - Click “Save”.

    <img src="../assets/L1Images/media/image77.png"
    style="width:6.26806in;height:4.05625in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

6. When we receive an inbound message from the customer asking for
    their order status, we need to look up the order information in the
    CRM or in the system of record. In the node palette, displayed to
    the left, click on integrations and find a node named “Custom CRM”.
    This can also be searched for using the search button.

    <img src="../assets/L1Images/media/image78.png"
    style="width:6.26806in;height:4.75903in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

7. Drag the “Custom CRM” node to the flow canvas next to the SMS node.

    <img src="../assets/L1Images/media/image79.png"
    style="width:6.26806in;height:3.67273in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

8. To wire the two nodes, click on the “green” dot of the SMS node and
    drag it until it snaps on to the “Custom CRM” node.

    <img src="../assets/L1Images/media/image80.png"
    style="width:6.26806in;height:3.52569in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    <img src="../assets/L1Images/media/image81.png"
    style="width:6.26806in;height:3.70347in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

9. Now double click on the “Custom CRM” node to add details.

    <img src="../assets/L1Images/media/image82.png"
    style="width:6.26806in;height:4.03889in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

10. Click on “Select Method Name” and select “Fetch CRM Data”. This should
    enable the Phone Number field and to fill this, expand on “Start”
    listed under “Input Variables” that can be found on the right side
    of the panel as shown below.

    <img src="../assets/L1Images/media/image83.png"
    style="width:6.26806in;height:4.04653in"
    alt="A screen shot of a computer AI-generated content may be incorrect." />

    Click on “sms.senderNumber” variable found in the list.

    <img src="../assets/L1Images/media/image84.png"
    style="width:6.26806in;height:4.03681in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    Click “Save” to save the configuration.

11. Next, you will simply add an SMS node to the flow and then select
    the template called [Final Confirmation](#FinalConfirmation) and
    populate the corresponding variables with the relevant parameters
    that is extracted via the Custom CRM node. From the node palette,
    under channels, select “SMS” and drag it to the canvas next to the
    “CRM” node. Now wire the CRM node to SMS node by clicking on the
    green dot and snapping it to the SMS node.

    <img src="../assets/L1Images/media/image85.png"
    style="width:6.26806in;height:2.94444in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    <img src="../assets/L1Images/media/image86.png"
    style="width:6.26806in;height:3.99861in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    <img src="../assets/L1Images/media/image87.png"
    style="width:6.26806in;height:3.67222in"
    alt="A diagram of a diagram of a customer service AI-generated content may be incorrect." />

12. Click on the SMS node to configure.

    <img src="../assets/L1Images/media/image88.png"
    style="width:6.26806in;height:4.04792in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    <img src="../assets/L1Images/media/image89.png"
    style="width:6.26806in;height:4.06458in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    Observe the Message body and this is the power of templates, which
    allows the substitution of variables. All the variables for this
    section is derived from “Custom CRM”. To add the variables, click on
    the value field under each variable and then expand the “Custom CRM”
    on the right panel to choose the appropriate variables as shown
    below.

    <img src="../assets/L1Images/media/image90.png"
    style="width:6.26806in;height:4.03194in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    <img src="../assets/L1Images/media/image91.png"
    style="width:6.26806in;height:4.04514in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    Click “Save” to save the node configuration.

13. Let us capture the customer journey in Journey Data Service (JDS).
    JDS is a free form API that can be used across any system to capture
    the moments that matter for the customer journey. Find the JDS node
    from the node palette, under integrations, find JDS node and drag it
    to the canvas. Wire the connection by connecting the green dot from
    the previous SMS node to snap on to the JDS node.

    <img src="../assets/L1Images/media/image92.png"
    style="width:6.26806in;height:2.65625in"
    alt="A screen shot of a computer AI-generated content may be incorrect." />

14. Double click the JDS node to configure it. Click on Method Name and select
    “Create Events”. Fill the following details

    - Transaction Id: click on the field and select the variable
      **“sms.transId”** from the start node on the right of the panel.

    - What Type of Interaction: **Order check**

    - What is the Source of this Transaction: **Website**

    - Enter the Identity to Tag This Transaction: Click on the field and
      select **“Custom CRM”** on the right panel and in the variables click
      on **orderId**.

    - What Identity Type is This? From the drop down, select **temporaryId**

    - Enter the Subtitle Information: Enter text **Order status request**.

    - What Icon Type Do you want to use? Enter text **email-happy**

    - What is the title for this transaction: Enter text **Order status
      request**

    - What is the Product Name? Click on the field and select **“Custom
      CRM”** on the right panel and in the variables click on **productName**.

    - What is the Website Information: Enter text
      **\[cisco\]([www.cisco.com](http://www.cisco.com))**

    - What was the last Action: Enter Text **Order status update request**.

    - What was the channel used for this transaction: Enter text **SMS**.

    - What is the Order Id: Click on the field and select **“Custom CRM”**
      on the right panel and in the variables click on **orderId**.

    - What is the delivery status: Click on the field and select **“Custom CRM”** on the right panel and in the variables click on
      **deliveryStatus**.

      <img src="../assets/L1Images/media/image93.png"
      style="width:6.26806in;height:4.05139in"
      alt="A screenshot of a computer AI-generated content may be incorrect." />

      <img src="../assets/L1Images/media/image94.png"
      style="width:6.26806in;height:3.14167in"
      alt="A screenshot of a computer AI-generated content may be incorrect." />

      <img src="../assets/L1Images/media/image95.png"
      style="width:6.26806in;height:4.03542in"
      alt="A screenshot of a computer AI-generated content may be incorrect." />

      Click “Save” to save the node configuration.

15. Click the green dot from the JDS node and drag to open canvas to
    open the “End” configuration.

    <img src="../assets/L1Images/media/image96.png"
    style="width:6.26806in;height:3.52569in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

    Click the drop down on “Node Event” and select “success” and select
    “101 – Successfully completed flow \[Success\] under “Flow Result”.

    <img src="../assets/L1Images/media/image97.png"
    style="width:6.26806in;height:4.04236in"
    alt="A screenshot of a computer AI-generated content may be incorrect." />

16. Click “Save” and Click “Make live” to put the flow into production.

17. Now let us test the catch all flow. The last step from the previous
    goal was to test and the message delivered looks like the below
    example.

    <img src="../assets/L1Images/media/image98.png"
    style="width:2.11818in;height:4.19011in"
    alt="A screenshot of a phone AI-generated content may be incorrect." />

18. The last message suggests the customer to send a text “STATUS” to
    that number.

19. From your mobile phone reply to the above text with “STATUS”
    message.

    <img src="../assets/L1Images/media/image99.png"
    style="width:6.26806in;height:4.91181in"
    alt="A screenshot of a phone AI-generated content may be incorrect." />

    Congratulations! You have successfully completed Lab 1.
