# Database Models

## Introduction

This is a table of contents for all of the database tables used in the Learning Management System.

## 💻 Activity

**Description:** The Activity model represents the tutorial and projects that student's follow to learn how to do something in software engineering. An example would be 'How to set up your first React App'.

### Columns

* 📝**name\(string\):** The name of the Activity.
* 📄**filename\(string\):** This is the location of the Activity in Github.
* 🍎**summary\(string\):** A short explanation on what the student will learn in the Activity.
* 🍏**description\(string\):** A more detailed explanation on what skills the student will be learning by doing an Activity.
* 💢**difficulty\(string\):** This determines how hard the Activity is. The difficulties are Hard, Medium, and Easy.
* 👩🏼‍🎨**image\(string\):** This is the image used to represent the Activity.
* ✅**is\_project\(boolean\):** This determines if an Activity is a project.

### ♥️**Relationships**

* 🏄‍♂️**prerequisite\_activities\(one-to-many\):** The Activities that are prerequisites to other Activities.
* 📖**cards\(one-to-many\):** Keeps track of all the Cards that belong to the Activity.
* 🔐**last\_module\(one-to-many\):** This is the last Activity unlocked from a ModuleProgress.  
* 🧶**students\(one-to-many\):** Keeps track of Students in ActivityProgress.
* 🧲**suggested\_students\(one-to-many\):** Keeps track of the Activity that is suggested for a Student.
* 🧺**modules\(many-to-many\):** Keeps track of all the Modules that an Activity belongs to. 
* 🔮**module\_prereqs\(many-to-many\):** Keeps track of the Module in which it is a perquisite to.
* 📮**students\_completed\(many-to-many\):** The Students that have completed an Activity.
* 🖼**students\_incomplete\(many-to-many\):** The Students that have not completed an Activity.
* 📺**students\_current\(many-to-many\):** The Students that are currently working on an Activity. 
* 📻**modules\_completed\(many-to-many\):** The Activities completed in ModuleProgress.
* 🏩**modules\_incomplete\(many-to-many\):** The Activities incomplete in ModuleProgress.
* 🥔**modules\_inprogress\(many-to-many\):** The Activities that are in progress in ModuleProgress.
* 🥨**topic\_prereqs\(many-to-many\):** Keeps track of the Activities needed to do a Topic.
* ⌛️**chosen\_modules\(many-to-many\):** Keeps track of the Activities that are marked as Projects for ModuleProgress.
* ✒️**authors\(many-to-many\):** Keeps track of the Authors that contributed in making an Activity.

## 👩‍🏫 Author

**Description:** The Author model represents the people help make a specific Activity.

### Columns

* 🐙**username\(string\):** This is the Github username of the Author. 

### **Relationships**

* 💻**activities\(many-to-many\):** This is the Activities that the Author has helped make.

## ✉️ Card

**Description:** Cards represent the instructions of an Activity.

### Columns

* 📰**name\(string\):** This is the name of the card.
* 📼**content\(string\):** This is the instruction that the student sees when viewing a Card. 
* 💎**gems\(integer\):** Gems are the amount of gems that the student gains by unlocking a Card.
* 📆**order\(integer\):** Order is the order in which the card will show up in an Activity.
* 👩🏻‍💻**github\_raw\_data\(string\):** This is the card content that was parsed from Github.
* 📄**filename\(string\):** This is the location of the Activity in Github.

### 💏**Relationships**

* 👩‍✈️**activity\(one-to-many\):** The Activity that the Card belongs to.
* 🧚‍♂️**checkpoints\(one-to-many\):** The Checkpoints that the Card owns.
* 🧙‍♂️**hints\(one-to-many\):** The Hints that a Card owns.
* 🔒**activity\_locked\_cards\(many-to-many\):** These are the Cards that are locked in ActivityProgress.
* 🔐**activity\_unlocked\_cards\(many-to-many\):** These are the Cards that are unlocked in ActivityProgress.

## ✅ Checkpoint

**Description:** Checkpoints represent small tasks for students to do. It is used to show how well the student understands the material presented in an Activity. Checkpoints take the form of **Short Answer, Image Upload, Video Upload, Multiple Choice, and Autograder.**

### Columns

* 📰**name\(string\):** This is the name of the Checkpoint.
* 📚**instruction\(string\):** This is the task that the student must follow.
* 📋**checkpoint\_type\(string\):** This tells what type of Checkpoint. Checkpoints could be Short Answer, Image Upload, Video Upload, Multiple Choice, and Autograder.
* 🖌**image\(string\):** This is the image used to represent the Checkpoint.
* 🖥**cli\_command\(string\):** This is the CLI command used to submit code to have it be graded if it is an autograder Checkpoint.
* 📄**filename\(string\):** This is location of the Checkpoint in Github.
* 📺**test\_cases\_location\(string\):** A path to the test cases on Github.
* 📬**tests\_zip\(string\):** Tests zip location on the AWS S3 Bucket.

###  💑**Relationships**

* 🧖‍♀️**cards\(one-to-many\):** The Cards that the Checkpoint belongs to.
* 🦷**criteria\(one-to-many\):** The Criteria that a Checkpoint owns.
* 🎩**checkpoint\_progress\(one-to-many\):** The Checkpoint that belongs to CheckpointProgress.
* 🐉**choices\(one-to-many\):** The McChoices that belong to a Checkpoint.
* 🎍**correct\_choice\(one-to-one\):** The McChoice that is correct for a Checkpoint.

## ⛩ Classroom

**Description:** Classrooms represent a list of modules that a Teacher intends to teach.

### Columns

* 📰**name\(string\):** Name of the Classroom.
* ⚗️**class\_code\(string\):** The class code used to join a Classroom.
* 📅**date\_start\(string\):** The date when the Classroom starts.
* 📆**date\_end\(string\):** the date when the Classroom ends. 

### 🌹Relationships 

* ✨**students\(many-to-many\):** The Students that are enrolled in a Classroom.
* ⚡️**modules\(many-to-many\):** The Modules that the Classroom teaches to its Students. 

## ☁️ Concept

**Description:** An abstract idea that helps the Student understand an Activity more. 

### Columns

* 📰**name\(string\):** Name of the Concept.
* 📄**filename\(string\):** Location of the Concept in Github.

### 🌸Relationships

* 🐹**steps\(one-to-many\):** The instructions used to explain an abstract idea.
* 🐯**cards\(many-to-many\):** The Cards that a Concept belongs to. 

## 💡Criteria

**Description:** A standard for Teachers to use when grading an Image or Video Checkpoint.

### Columns

* 📗**content\(string\):**  The description that the Teacher sees to evaluate a Checkpoint.
* 🔑**criteria\_key\(string\):** A unique key used to identify a criteria in a file.

### 😍Relationships

* 👻**checkpoint\(one-to-many\):** The Checkpoint that a Criteria belongs to. 

## 🎇Event

**Description:** A social gathering of people.

### Columns

* 📰**name\(string\):** Name of the the Event.
* 🗓**date\(string\):** When the Event takes place.
* 🥭**summary\(string\):** A description on what is going to happen in the Event.
* 📸**location\(string\):** Where the Event will take place.

### 🥰Relationships

* 🍃**organization\(one-to-many\):** The Organization thats hosts the Event.
* 🤠**presenters\(many-to-many\):** The Users that are presenting an Event.
* 🥯**rsvp\_list\(many-to-many\):** The Users that have signed up to attend an Event. 

## 🌮 Hint

**Description:** A short description and visualization that is used to help a Student go through an Activity/Project.

### Columns

* 📰**name\(string\):** This is the name of the Hint.
* 💎**gems\(integer\):** The amount of gems that the Student loses when opening a Hint.
* 🚀**order\(integer\):** The order in which the Hint is shown.
* 📄**filename\(string\):** Location of the Hint in Github. 
* 🐱**github\_raw\_data\(string\):** This is content that was parsed from Github.

### 🌷Relationships

* 🍋**card\(one-to-many\):** The Card that the Hint belongs to.
* 🥡**steps\(one-to-many\):** The Steps that a Hint owns.
* 🥍**activity\_progress\(one-to-many\):** The HintStatus that the Hint belongs to.
* 🍖**hints\(many-to-many\):** Hints can own other Hints. This is used to keep track of the Hints that belong to a Hint. 

## 🎾 Module

**Description:** A collection of Activities used to teach a specific software engineering skill. An example would be 'Intro to React'.

### Columns

* 📰**name\(string\):** This is the name of the Module.
* 📄**filename\(string\):** Location of the Module in Github.
* 🍕**description\(string\):** A short summary about what the Module aims to teach a Student.
* 🍫**gems\_needed\(integer\):** This is the gems needed to unlock a Module.
* 📷**images\(integer\):** An image that represents the Module

### 💐Relationships

* 🦀**activities\(many-to-many\):** The Activities that a Module owns.
* 🐣**topics\(many-to-many\):** The Topics in which the Module belongs to. 
* 🦚**students\_completed\(many-to-many\):** The Students have completed the Module. 
* 🍠**students\_inprogress\(many-to-many\):** The Students that are currently working on the Module.
*  🍕**students\_incomplete\(many-to-many\):** The Students that have not started on the Module.
* 🍱**students\(many-to-many\):** The Students that have a ModuleProgress object associated with the Module.
* 🥑**classrooms\(many-to-many\):** The Classrooms in which the Module is being taught in. 
* 🍯**completed\_topics\(many-to-many\):** The Modules that are completed in TopicProgress. 
* 🥌**incomplete\_topics\(many-to-many\):** The Modules that are incomplete in TopicProgress.
* 🏋🏼‍♂️**inprogress\_topics\(many-to-many\):** The Modules that are in progress in TopicProgress.

## 🍓McChoice

**Description:** A choice used in a Checkpoint to create a Multiple Choice Checkpoint.

### Columns

* 🎼**content\(string\):** The description of the choice.
* 🗝**choice\_key\(string\):** A unique string to distinguish other McChoices in a file.

### ♥️Relationships

* 🏮**checkpoint\(one-to-many\):** The Checkpoint that a McChoice belongs to.
* ⛺️**correct\_checkpoint\(one-to-one\):** This is the correct McChoice for a Checkpoint.

## 🏘 Organization

**Description:** A collection of people..\(fill more later\)

### Columns

* 📰**name\(string\):** This is the name of the Organization.
* 📷**image\(string\):** Image that represents the organization.
* 🌆**background\_image\(string\):** Background image for the Organization page.
* 🍘**is\_active\(boolean\):**  A value to keep track if the Organization is active or not.

### 💞Relationships

* 🔱**events\(one-to-many\):** The Events that are hosted by an Organization.
* 💠**owners\(many-to-many\):** The Users that lead the Organization.
* 🔔**active\_users\(many-to-many\):** The list of Users that are active in an Organization.
* 🔕**inactive\_users\(many-to-many\):** The list of Users that are inactive in an Organization.

## 🍇 Step

**Description:** A Step is a small explanation on how to do something in an Activity. 

### Columns

* 📰**name\(string\):** Name of the Step.
* 📜**content\(string\):** This is the Markdown content to display.
* 💻**code\_snippet\(string\):** Code snippets are pieces of code to help a Student with an Activity.
* 🏞**image\(string\):** A visualization to help the Student understand a Card or Concept.
* 🛰**step\_key\(string\):** A unique string to keep track of the Steps in a file.

### 💖Relationships

* 🕯**concept\(one-to-many\):** The Concept that the Step belongs to.
* 🚀**hint\(one-to-many\):** The Hint that the Step belongs to.

**Note:** A Step cannot belong to a Hint and a Concept at the same time.

## 🐚 Submission

**Description:** This is the result after running a Student's code on the autograder.

### Columns

* 🌟**results\(JSON\):** This keeps track of how many test cases the Student gets right and wrong.
* ☃️**date\_time\(string\):** The date that the Submission was created.

### 💙Relationships

* ⚓️**progress\(one-to-many\):** The saved Submission that was saved to the CheckpointProgress.

## 🥠Topic

**Description:** A collection of Modules to help teach Students a broad software engineering skill. An example would be 'Frontend Development'.

### Columns

* 🏔**name\(string\):** Name of the Topic.
* 🏝**filename\(string\):** Location of the Topic in Github.
* 🍞**description\(string\):** A short summary describing what the Topic will teach the Student. 
* 🌯**image\(string\):** An image used to represent a Topic.

### 💛Relationships

* 🎲**modules\(many-to-many\):** The Modules that are used in a Topic.
* ♟**tracks\(many-to-many\):** The Tracks that a Topic belongs to.
* 🎮**student\_completed\(many-to-many\):** Students that have completed a Topic
* 🌽**student\_inprogress\(many-to-many\):** Students that are currently working on a Topic.
* 🥓**students\(many-to-many\):** The Students that have a TopicProgress with this Topic id.

## 🥇Track

**Description:** A collection of Topics. It is very similar to a major. An example would be 'Computer Science'.

### Columns

* 🎹**name\(string\):** The name of the Track.
* 🏮**description\(string\):** A summary of what the Track will teach a Student.

### 🧡Relationships

* 🎷**students\(one-to-many\):** The Students that follow a Track.
* 🌋**topics\(many-to-many\):** The Topics that are used in a Track.

## 🎊 Meta

**Description:** A base class used to keep track of a User, Student, Teacher, and Admin.

### Columns

* 🎬**roles\(string\):** Keeps track of the roles that a User has when logging in.

### 💜Relationships

*  🍝**user\(one-to-one\):** The User that the Meta class keeps track of.
* 🌃**student\(one-to-one\):** The Student that the Meta class keeps track of.
* 🍰**teacher\(one-to-one\):** The Teacher that the Meta class keeps track of.
* 🗿**admin\(one-to-one\):** The Admin that the Meta class keeps track of.

## 👩🏻‍💻 User

**Description:** A person that uses our web app.

### Columns

* 💸**name\(string\):** Name of the User.
* 📧**email\(string\):** Email of the user.
* 💶**token\(string\):** A string used to keep track if the User exists through our Autograder CLI.
* 🎟**github\_access\_token\(string\):** Access token used to authenticate a User with OAuth.
* ♠️**github\_id\(integer\):** The user id stored in Github. This is used to check if the User exists when logging in.
* 🥝**github\_username\(string\):** This is the User's Github username. This is obtained when the User signs up with OAuth.
* 🥃**image\(string\):** Profile image for the user. 
* 🥬**global\_gems\(integer\):** The total amount of gems that the User has earned. 
* 🍘**last\_seen\(string\):** This is the last time that the User has logged in.

### 💚Relationships

* 🛍**meta\(one-to-one\):** The Meta class that the User is associated with.
* 🥋**organizations\(many-to-many\):** The list of Organizations that a User is an owner in.
* 🏹**organizations\_active\(many-to-many\):** The list of Organizations that a User is active in.
* 🥮**organizations\_inactive\(many-to-many\):** The list of Organizations that a User is inactive in.
* 🍧**presenter\_events\(many-to-many\):** Events in which the User is presenting to.
* 🐬**rsvp\_events\(many-to-many\):** Events that the User is planning to attend.

## 🗽Admin

**Description:** A User that has the power to do anything on the site.

### Columns

### ❣️Relationships

* 🐧**meta\(one-to-one\):** The Meta class that the User is associated with.

## 🗼Student

**Description:** A User that learns on our Learning Management System. 

### Columns

### 💝Relationships

* 🔥**current\_track\(one-to-many\):** The Track that the Student is currently pursuing.
* 🚃**activity\_progresses\(one-to-many\):** The progress on how far a Student gets on an Activity.
* 🏄🏻‍♀️**module\_progresses\(one-to-many\):** The progress on how far a Student gets on a Module.
* 🍟**topic\_progresses\(one-to-many\):** The progress on how far a Student gets on a Topic.
* 🚎**suggested\_activity\(one-to-many\):** An Activity that is suggest to the Student based on the Module that they are working on.
* 🐌**meta\(one-to-one\):** The Meta class that the User is associated with.
* 🧗🏻‍♂️**classes\(many-to-many\):** The current Classrooms that the Student is enrolled in.
* 🌵**completed\_activities\(many-to-many\):** The Activities that the Student has completed.
* 🐘**incomplete\_activities\(many-to-many\):** The Activities that the Student has not completed.
* 🦊**current\_activities\(many-to-many\):** The Activities that the Student is currently working on. 
* 🐮**completed\_modules\(many-to-many\):** The Modules that the Student has completed.
* 🦅**incomplete\_modules\(many-to-many\):** The Modules that the Student has not completed.
* 🦄**inprogress\_modules\(many-to-many\):** The Modules that the Student is currently working on. 
* 🐔**completed\_topics\(many-to-many\):** The list of Topics that the Student has completed.
* 🙊**incomplete\_topics\(many-to-many\):** The list of Topics that the Student has not completed.

## 🏯 Teacher

**Description:** A User that manages Students and monitors their progress. 

### Columns

### 💗Relationships

* 🍩**classrooms\(one-to-many\):** The Classrooms that the Teacher is teaching.
* 🍫**meta\(one-to-one\):** The Meta class that the User is associated with.

## 🚞 ActivityProgress

**Description:** An object used to keep track of a Student's progress in an Activity. 

### Columns

* 🎱**is\_completed\(boolean\):** Keeps track if the Activity has been completed. An Activity is considered completed if all cards are unlocked and all checkpoints are completed.
* 🥡**is\_graded\(boolean\):** Keeps track if a Teacher has graded an ActivityProgress.
* 🍙**is\_passed\(boolean\):** Keeps track if an ActivityProgress has passed or not.
* 🥐**last\_card\_unlocked\(integer\):** The id of the last card that a Student views.
* 🌊**date\_graded\(string\):** The date when the Teacher grades an ActivityProgress.
* 🐳**accumulated\_gems\(integer\):** Total amount of gems earned from the doing the Activity.

### ❣️Relationships

* 🍑**student\(one-to-many\):** A reference to the Student that owns an ActivityProgress.
* 🎡**activity\(one-to-many\):** A reference to the Activity that the ActivityProgress is for.
* 🍚**hints\(one-to-many\):** The list of locked and unlocked Hints. 
* 🍒**checkpoints\(one-to-many\):** The list of CheckpointProgress that the Student has to do to complete the Activity.
* 🥦**cards\_locked\(many-to-many\):** Cards that the Student has not seen yet.
* 🍀**cards\_unlocked\(many-to-many\):** The Cards that the Student has already unlocked.
* 🥳**checkpoints\_passed\(many-to-many\):** The CheckpointProgresses that the Student has passed in the Activity. 
* 🤭**checkpoints\_failed\(many-to-many\):** The CheckpointProgresses that the Student has failed in the Activity. 

## 🌈 CheckpointProgress

**Description:** An object to keep track of a Student's progress for a Checkpoint.

### Columns

* 🎋**student\_id\(integer\):** A Student id to keep track of which Student owns a CheckpointProgress.
* 🍁**content\(string\):** The instruction given to solve a Checkpoint.
* 🌺**multiple\_choice\_is\_correct\(boolean\):** A boolean to keep track if a Multiple Choice Checkpoint is correct.
* 🦐**student\_comment\(string\):** A comment from a Student to explain what they did in a Checkpoint. 
* 🦖**teacher\_comment\(string\):** A comment from a Teacher to give a Student on how well they did on a Checkpoint.
* 🐊**is\_complete\(boolean\):** A boolean to keep track whether or not the the CheckpointProgress is completed

### 😘Relationships

* 🤖**checkpoint\(one-to-many\):** A reference to the Checkpoint that the progress is for.
* 👩‍🎨**activity\_checkpoint\_progress\(one-to-many\):** A reference to the ActivityProgress that the CheckpointProgress belongs to.
* 😺**submissions\(one-to-many\):** The code Submission results that the Student has submitted.
* 👨🏻‍🌾**activity\_failed\(many-to-many\):** The CheckpointProgresses that are considered failed in the ActivityProgress.
* 👨🏻‍💻**activity\_passed\(many-to-many\):** The CheckpointProgresses that are considered passed in the ActivityProgress.

## 🍔 HintStatus

**Description:** An object used to keep track if a Hint has been unlocked.

### Columns

* 🍮**card\_id\(integer\):** An id used to keep track of which Card the HintStatus object belongs to.
* 🏓**is\_unlocked\(boolean\):** Keeps track if a Hint has been unlocked or not. If it has then the Student's accumulated gems are decreased. 

### 🥰Relationships

* 🎵**hints\(one-to-many\):** The list of HintStatus objects that a HintStatus owns.
* 🎧**activity\(one-to-many\):** The ActivityProgress that owns HintStatus.

## 👻 ModuleProgress

**Description:** An object to keep track of the Student's progress for a Module.

### Columns

* 🧞‍♂️**is\_completed\(boolean\):** A boolean to keep track if a Student has completed a ModuleProgress.
* 👑**accumulated\_gems\(integer\):** The amount of gems earned from doing the Activities in a Module.
* 🦋**needed\_gems\(integer\):** Gems needed to complete a ModuleProgress.

### ❤️Relationships

* 🦐**student\(one-to-many\):** A reference to the Student that owns a ModuleProgress.
* 🐨**module\(one-to-many\):** A reference to the Module that the ModuleProgress is for.
* 🧢**last\_activity\_unlocked\(one-to-many\):** The last Activity that the Student has started on.
* 🦁**chosen\_projects\(many-to-many\):** List of Activities has chosen as projects for a ModuleProgress.
* 🦔**completed\_activities\(many-to-many\):** The Activities that the Student has completed.
* ❄️**incomplete\_activities\(many-to-many\):** The Activities that the Student has not completed.
* 🐄**inprogress\_activities\(many-to-many\):** The Activities that the Student is currently working on. 

## ☃️ TopicProgress

**Description:** An object to keep track of a Student's progress for a Topic.

### Columns

* 🌹**is\_completed\(boolean\):** A boolean to keep track if a Student has completed a ModuleProgress.

### 💙Relationships

* 🐝**student\(one-to-many\):** A reference to the Student that owns a TopicProgress.
* 🐼**topic\(one-to-many\):** A reference to the Topic that the TopicProgress is for.
* 🐮**completed\_modules\(many-to-many\):** The Modules that the Student has completed.
* 🥠**incomplete\_modules\(many-to-many\):** The Modules that the Student has not completed.
* 🥧**inprogress\_modules\(many-to-many\):** The Modules that the Student is currently working on. 

