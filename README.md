# Overview

Here, you can find the information about homework assignments and the final project required for this course.

There are a total of 4 assignments that need to be delivered by their respective deadlines. In addition, each student is required to provide the final project based on the material that has been learnt during this course.

In each directory (HW01-HW04 and Final-Project), there is a README.md file that provides the necessary information for each section; make sure to read them before starting to work on the assignments.

The following explains the steps required to prepare for assignments.

## Fork this Repo

First, you need to fork this repo by following the below instructions:

1. Click on the fork button in the upper right corner of this page.
2. On the fork page, choose an appropriate namespace along with appropriate project name.
3. Make sure to set the visibility level to "private" for this project.
4. Click on the `fork project` button.

## Add TAs to the Forked Project

Next, TAs need to be added to the forked project. Follow the blew instructions:

1. On the forked repo page, hover over the top left corner to see the sidebar.
2. Once the sidebar is visible, click on `mange --> member`.
3. On the project members page, click on the blue button `invite members` on the top right.
4. Search for `???` and add the TA with the owner role. (THIS PART REQUIRES UPDATE FROM THE MAIN TAs)

## Create a Project in Rahti

For HW03 and HW04 you will need to work with Kubernetes. We can use managed Kubernetes provided by [CSC](https://csc.fi), which is named Rahti. In order to have a Rahti project, a CSC project is needed. Follow the below steps to create an account in CSC, and then create a project in CSC, then create a project in Rahti:

1. Create an account in CSC:
   1. Go to [my.csc.fi](https://my.csc.fi/)
   2. Log in with Haka option
   3. Fill in the sign-up instructions
   4. Set your password using 12 characters or more, containing both upper and lowercase letters and at least one number. No special characters are allowed
   5. You will receive your CSC user account information via email
2. Create a project in CSC:
   1. Go to [my.csc.fi/projects](https://my.csc.fi/projects)
   2. Click on the `+ New Project` button on the top right of the page
   3. Choose the project name like: `sdx-assignment- YOUR CSC USERNAME`
   4. Provide a project description like the following: `This project is needed for sdx course in university of Oulu.`
   5. Choose the `Course` option for the project category
   6. Choose current date as the start date, and 5 months after now for the end date
   7. Choose `Engineering and technology` for the field of science drop-down menu
   8. Choose `Electronic, automation, and communications engineering, electronics` for the sub science area drop-down menu
   9. Read the terms and conditions and agree with them
   10. Create the project
   11. **NOTE** the project number once the project is created (you will need it in the following Rahti project creation section)
   12. Select the created project to see the detailed information about the project
   13. On the right of the screen, there is a section named `SERVICES`. In this section, find Rahti, and click on it
   14. Read the terms and conditions and agree with it
   15. Click on the `Add service` button
   16. You may need to wait for about 30 minutes until you can start creating a project in Rahti
3. Create a project in Rahti:
   1. Go to [rahti.csc.fi](https://rahti.csc.fi/)
   2. Click on the `Login page`
   3. Once you authenticate, you will be presented by the Rahti web interface. In this page, you can see the blue button `Create Project`; click on it
   4. Choose the name of the project like: `sdx-assignment- YOUR CSC USERNAME`
   5. In the Description section, enter the following: `csc_project: PROJECT-NUMBER`
      1. You can get the project number by the below instructions:
      2. Go to [my.csc.fi/projects](https://my.csc.fi/projects)
      3. There is a number associated with the CSC project you created earlier in the previous step, use this number for creating the Rahti project (the number is like 200XXXX)
   6. Click the blue button `create` to create the Rahti project
4. Add TAs to your Rahti project:
   1. In your Rahti project page, click on the top-left sandwich button to see the menu
   2. Click on the `Administrator` button and choose `Developer`
   3. Again, click on the top-left sandwich button to see the menu
   4. Choose the `Project` button
   5. Choose the `Project access` tab
   6. Click on `Add access` button
   7. Select `User` for the subject section
   8. Enter `???` in the name section and choose the `Admin` role (THIS PART REQUIRES UPDATE FROM THE MAIN TAs)
   9. Click on the `Save` button at the bottom of the page

## Download Required CLI Tools

You need a couple of command line tools during this course. Install the following tools for your operating system:

- [OC](https://console.rahti.csc.fi/command-line-tools) is needed to interact with Rahti
- [mosquitto](https://mosquitto.org/download/) is needed to interact with MQTT broker. You can check the installation is complete, by doing the following:
  - Open _two_ terminals
  - On the _first_ terminal run `mosquitto_sub -h test.mosquitto.org -p 1883 -t 'sdx/#' -v`
  - On the _second_ one run `mosquitto_pub -h test.mosquitto.org -p 1883 -t 'sdx/<insert_string>' -m '1337'`
  - Check the first terminal, you should see: `sdx/<insert_string> 1337`
  - Replace `<insert_string>` with your own word/number
- [Docker](https://docs.docker.com/engine/install/) is needed for building and managing microservices
- [git](https://git-scm.com/downloads) is needed to deliver your assignments

## Clone the Forked Repo into Your Computer

At this stage, you need to clone the forked repo to start working on the assignments. You can easily clone the project by clicking the blue `code` button in the git lab page of the forked repo. Choose either clone with SSH or HTTPS depending on your own preference. Then run the following in your desired directory:

```shell
# Run the following command in your terminal
git clone THE-COPIED-URL
```

Now, you can start working on the assignments in your computer.

## Fill in the Student Information File

There is a file named [student-info.yml](./student-info.yml) that needs to be filled in according to your information.

## Assignment Checks

For each assignment you can see if you have done everything right by clicking on the icon shown below after you have returned that assignment:

![](/.pics/check-assignments.png)
