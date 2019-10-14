>If you are unable to view the IPYNB notebook in GitHub, Please copy the GitHub notebook URL and paste it in [nbviewer](https://nbviewer.jupyter.org/).


### DonorsChoose.org dataset Analysis and Modelling Using Various Machine Learning Models

DonorsChoose.org receives hundreds of thousands of project proposals each year for classroom projects in need of funding. Right now, a large number of volunteers is needed to manually screen each submission before it's approved to be posted on the DonorsChoose.org website.

Next year, DonorsChoose.org expects to receive close to 500,000 project proposals. As a result, there are three main problems they need to solve:

How to scale current manual processes and resources to screen 500,000 projects so that they can be posted as quickly and as efficiently as possible How to increase the consistency of project vetting across different volunteers to improve the experience for teachers How to focus volunteer time on the applications that need the most assistance The goal of the competition is to predict whether or not a DonorsChoose.org project proposal submitted by a teacher will be approved, using the text of project descriptions as well as additional metadata about the project, teacher, and school. DonorsChoose.org can then use this information to identify projects most likely to need further review before approval.

## About the DonorsChoose Data Set

The `train.csv` dataset provided by DonorsChoose contains the following features:

Feature | Description 
----------|---------------
**`project_id`** | A unique identifier for the proposed project. **Example:** `p036502`   
**`project_title`**    | Title of the project. **Examples:** Art Will Make You Happy! First Grade Fun
**`project_grade_category`** | Grade level of students for which the project is targeted. One of the following enumerated values: Grades PreK-2 ,Grades 3-5 ,Grades 6-8, Grades 9-12 
 **`project_subject_categories`** | One or more (comma-separated) subject categories for the project from the following enumerated list of values:  Applied Learning,Care &amp; Hunger,Health &amp; Sports,History &amp; Civics,Literacy &amp; Language,Math &amp; Science,Music &amp; The Arts,Special Needs,Warmth **Examples:** Music &amp; The Arts,,Literacy &amp; Language, Math &amp; Science 
  **`school_state`** | State where school is located ([Two-letter U.S. postal code](https://en.wikipedia.org/wiki/List_of_U.S._state_abbreviations#Postal_codes)). **Example:** `WY`
**`project_subject_subcategories`** | One or more (comma-separated) subject subcategories for the project. **Examples:** Literacy,Literature &amp; Writing, Social Sciences<
**`project_resource_summary`** | An explanation of the resources needed for the project. **Example:** My students need hands on literacy materials to manage sensory needs!
**`project_essay_1`**    | First application essay 
**`project_essay_2`**    | Second application essay
**`project_essay_3`**    | Third application essay
**`project_essay_4`**    | Fourth application essay
**`project_submitted_datetime`** | Datetime when project application was submitted. **Example:** `2016-04-28 12:43:56.245`   
**`teacher_id`** | A unique identifier for the teacher of the proposed project. **Example:** `bdf8baa8fedef6bfeec7ae4ff1c15c56`  
**`teacher_prefix`** | Teacher's title. One of the following enumerated values: nan,Dr.,Mr.,Mrs.,Ms.,Teacher.
**`teacher_number_of_previously_posted_projects`** | Number of project applications previously submitted by the same teacher. **Example:** `2` 

Additionally, the `resources.csv` data set provides more data about the resources required for each project. Each line in this file represents a resource required by a project:

Feature | Description 
----------|---------------
**`id`** | A `project_id` value from the `train.csv` file.  **Example:** `p036502`   
**`description`** | Desciption of the resource. **Example:** `Tenor Saxophone Reeds, Box of 25`   
**`quantity`** | Quantity of the resource required. **Example:** `3`   
**`price`** | Price of the resource required. **Example:** `9.95`   

**Note:** Many projects require multiple resources. The `id` value corresponds to a `project_id` in train.csv, so you use it as a key to retrieve all resources needed for a project:

The data set contains the following label (the value you will attempt to predict):

Label | Description
----------|---------------
`project_is_approved` | A binary flag indicating whether DonorsChoose approved the project. A value of `0` indicates the project was not approved, and a value of `1` indicates the project was approved.

### Notes on the Essay Data


Prior to May 17, 2016, the prompts for the essays were as follows:
__project_essay_1:__ "Introduce us to your classroom"
__project_essay_2:__ "Tell us more about your students"
__project_essay_3:__ "Describe how your students will use the materials you're requesting"
__project_essay_4:__ "Close by sharing why your project will make a difference"


Starting on May 17, 2016, the number of essays was reduced from 4 to 2, and the prompts for the first 2 essays were changed to the following:
__project_essay_1:__ "Describe your students: What makes your students special? Specific details about their background, your neighborhood, and your school are all helpful."
__project_essay_2:__ "About your project: How will these materials make a difference in your students' learning and improve their school lives?"

For all projects with project_submitted_datetime of 2016-05-17 and later, the values of project_essay_3 and project_essay_4 will be NaN.

