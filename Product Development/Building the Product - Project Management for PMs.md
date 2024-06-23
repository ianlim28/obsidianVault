### Product development hierarchy
Goals > Initiatives > Releases > Features > Epics > User stories > Tasks > Subtasks

**Goals**
- what you want to achieve to meet your vision (short term or long term)
- example: "increase the user base by 10% by next year"

**Initiatives**
- high-level efforts that will help you achieve your goals 
- example: "translate our app into 3 more languages"

**Releases**
- a release or delivery of a new customer experience at a high level
- example: the release of our app with the 3 new language translations

**Features**
- one or several sets of capabilities delivered to the end user
- example: the ability for the user to change the language the app is displayed in

**Epics**
- related bodies of work which can not be completed in 1 week, and or will take 1 sprint or more to complete
- example: "prepare the interface to display the long German words"

User stories / Tasks
- a set of things to be done that deliver user value and come together to form the completion of an epic
- example: prepare our back-end systems to handle inputs from 3 more different character types in the new languages

User stories are formatted like this: "As a USER, i want to DO X THING, so that i can SEE Y THING"

**Subtasks**
- one or many things that need to be done to complete a user story or higher level task
- they are usually very granular and technical in nature

You must complete the smaller things in order to complete the larger things up the chain 

![[Screenshot 2024-05-03 at 08.44.33.png]]



### Introduction to Epics

**Background:** Epics are fundamental components in agile development methodologies, serving as a high-level framework to organize and prioritize the development process. They stem from the overarching vision of the company, which is translated into actionable goals and metrics.

**Definition:** An epic is essentially a large, overarching project or initiative that encompasses multiple smaller tasks or features. It represents a significant chunk of work that contributes towards a specific goal but is too substantial to be completed in a single sprint (typically a 2-4 week period used in agile methodologies).

**Characteristics of Epics:**

1. **Broad Scope:** Epics are broad in scope and often encompass multiple features or functionalities that contribute to the strategic goals of the organization.
2. **Longer Duration:** They usually span multiple sprints, distinguishing them from smaller, more immediately achievable tasks known as user stories.
3. **Strategic Impact:** ==Epics are directly linked to the strategic objectives of a company==, helping to move the company closer to achieving its long-term goals.

### Examples of Epics

1. **"Translate the App to Spanish"**
    - **Goal:** To expand the user base by accommodating Spanish-speaking users, enhancing accessibility and market reach.
    - **Tasks Involved:** Includes translating the user interface, adapting marketing materials, localizing content, and perhaps adjusting features to suit cultural preferences.
2. **"Implement Photo Sharing in Direct Messages"**
    - **Goal:** To enhance user engagement by allowing more interactive and personal communication options within the app.
    - **Tasks Involved:** Developing the feature, ensuring privacy and security measures are robust, integrating with existing messaging functionalities, and testing for performance and user experience.

### How Epics Are Managed

**Process:**

1. **Initiation:** Epics begin as high-level ideas often derived from strategic planning sessions that involve senior leadership and product management teams.
2. **Breakdown:** Each epic is broken down into smaller, more manageable components (user stories) that can be tackled incrementally.
3. **Prioritization:** Epics are prioritized based on their alignment with business goals, resource availability, and market demands.
4. **Execution:** Teams work on user stories within designated sprints, gradually progressing towards completing the epic.
5. **Review and Adaptation:** Throughout the sprints, progress is reviewed, and adjustments are made to ensure the epic remains aligned with its objectives and reacts adaptively to any new insights or market changes.
**[Stories, epics and initiatives](https://www.atlassian.com/agile/project-management/epics-stories-themes)**



---

### Components of an Epic Spec Sheet
Epic spec sheets are critical documents in the product development process, especially in environments that use Agile methodologies. These documents serve as a blueprint for the entire lifecycle of an epic, ensuring all team members understand the goals, requirements, and the specifics of what needs to be built. Here’s a detailed breakdown of what goes into creating an effective epic spec sheet:


**1. Introduction**
- **Purpose of the Epic:** Briefly describe what the epic entails and the rationale behind it. This should clearly articulate why the epic is important, and how it aligns with broader business goals.
- **Goals and Objectives:** Outline the specific objectives this epic aims to achieve. Include which business or user metrics the epic intends to improve, providing a direct link between the epic’s implementation and expected outcomes.
- **Supporting Documentation:** Provide links to any relevant documents that can offer more in-depth information, such as market research, user data, or previous project outcomes. This can also include legal requirements, marketing plans, or any external constraints or compliance needs.
- **Early Wireframes:** Include initial designs or wireframes that give a visual overview of what is being built. These serve to give stakeholders a preliminary visual understanding of the proposed changes.

**2. Product Requirements**
- **Feature Details:** List and describe the specific features that make up the epic. This should be detailed enough that someone unfamiliar with the project can grasp what needs to be built.
- **User Stories:** Break down the epic into user stories or smaller tasks that describe in detail the functionalities from the user’s perspective. This helps in ensuring that all functionality is user-centric and meets the needs identified in the user research.

**3. Design Requirements**
- **Collaboration with Designers:** This section is developed in close collaboration with the UX/UI design team.
- **Visual and Interaction Design:** Include detailed design requirements, sketches, and prototypes that outline how the features should look and behave.
- **Design Specifications:** Detailed color schemes, typography, layout, and any animations should be included to guide the development team visually and interaction-wise.

**4. Engineering Requirements**
- **Technical Specifications:** After discussions with the engineering team, include detailed technical requirements necessary to build the features. This might involve architecture decisions, API specs, data models, and third-party services integrations.
- **Performance Criteria:** Define performance requirements that the product must meet, ensuring that the features perform well under expected loads.

### Creating and Maintaining the Epic Spec Sheet
- **Responsibility:** While the product manager is responsible for initiating and maintaining the epic spec sheet, it is a collaborative document. The PM oversees the strategic and product-focused sections primarily.
- **Collaboration:** Regular discussions with the design and engineering teams are crucial. The spec sheet should evolve based on ongoing feedback and new insights as development progresses.
- **Documentation:** Ensure the document is accessible and understandable. It should be clear, concise, and regularly updated to reflect any changes or new decisions.

### Company-Specific Approaches
- **Adaptability:** Each company may have its own template and requirements for epic spec sheets based on their specific workflows, tooling, or industry regulations.
- **Continuous Improvement:** Gather feedback on the effectiveness of the spec sheets in delivering successful projects and iterate on the format and content to better serve the team’s needs.

### Conclusion

Epic spec sheets are foundational tools in the product development process, providing a clear and structured way to communicate complex information across different teams. By effectively detailing every aspect of the epic from conception to requirements, these documents help ensure that all team members are aligned and informed, leading to more successful outcomes and a cohesive product development process.
**[Data flow: using data to constantly improve](https://www.fastcompany.com/3015932/data-flow-using-data-to-constantly-improve-part-6)**



---

### Understanding User Stories
User stories and acceptance criteria are essential tools in Agile software development, helping teams understand what they need to build and ensuring that they meet the required standards before a product or feature is released. Here’s how both fit into the development process:

**What Are User Stories?** User stories are short, simple descriptions of a feature told from the perspective of the person who desires the new capability, usually a user or customer of the system. They typically follow a simple template to clarify who needs the feature, what they need, and why.

**User Story Format:**
- **Template:** "As a [type of user], I want [an action] so that [a benefit/a goal]."
- **Purpose:** This format helps keep the focus on user needs rather than the technical details involved in how the feature will be implemented.

**Example of a User Story:**
- "As a user, I want to send pictures in a direct message to my friends, so that I can share my favorite photos with them."
- This story helps developers understand the value of the feature from the user's perspective, guiding the development process to focus on user benefits.

**Management of User Stories:**
- **Tracking:** User stories are typically maintained within a project management tool and tracked through statuses such as "To Do," "In Progress," and "Done."
- **Visibility and Collaboration:** This visibility allows the entire team to see what everyone is working on and to collaborate effectively, ensuring that all features align with user needs.

==**What’s critical is that each story:**==
- can stand on its own; if it has dependencies, combine them into one story
- can be delivered to QA and tested
- can be shipped to production (even if it has to be paddocked in some way)

*You Are As Smart As Your Stories*
> Stories are the building blocks of product development. In the aggregate, the stories you ship are a representation of your organisation’s strategy. A hundred micro-errors at the story level lead to massive organisational lethargy. Stories define the molecular structure of your company’s leanness.

>Your product managers and engineers need to be cutthroat in their decisions about what to build and what not to build. Every feature on your roadmap could be built in radically different amounts of time. You could spend a year building out a new search experience–or a month. The stories you write about this feature will define this difference. Everything is about opportunity cost; yes, this story will make this feature better, but what else could we be making in this same time period?

>The more specific your stories are, the more they will help engineers to understand the intended scope of the project. This is generally a good thing. However, hopefully your engineers are creative, smart, independent thinkers with a deep interest in the product they are making–so when stories are overwritten it can feel wasteful and demoralising. This is a fine balance.



### Understanding Acceptance Criteria

**What Are Acceptance Criteria?** Acceptance criteria consist of a set of predefined requirements that must be met for a user story to be considered complete. They are used to confirm when a task has been completed and to ensure that the software meets business goals and user requirements.

**Purpose of Acceptance Criteria:**
- **Clarity:** Provides clear and concise details on the functionality that must be implemented for the feature to be accepted.
- **Quality Assurance:** Acts as a checklist that ensures every essential aspect of a user story is addressed before it is marked as completed.

**Example of Acceptance Criteria:**
- "Given I am a user and I click the ‘Add picture’ button in the direct message, I am presented with a popup window to choose the file I want to upload, submit it with the upload button, and see a preview of the uploaded image."
- This criteria describe exactly what needs to happen when the user interacts with the feature, outlining the necessary steps for successful implementation.

### Role of the Product Manager in User Stories and Acceptance Criteria

**Responsibilities:**
- **Creation and Refinement:** The product manager is typically responsible for creating user stories and defining acceptance criteria, often with input from customers, stakeholders, and the development team.
- **Validation:** Product managers are also involved in testing completed features against the acceptance criteria. They ensure that the product meets the established standards before it is released to the public.

**Benefits of Effective User Stories and Acceptance Criteria:**
- **Enhanced Communication:** They ensure all team members understand the what, why, and how of the features they are developing.
- **Improved Product Quality:** By defining clear expectations, they help avoid rework and miscommunication, leading to higher product quality.
- **Customer Satisfaction:** They align product features with user needs and business goals, increasing customer satisfaction.

### Conclusion
User stories and acceptance criteria are fundamental in Agile development, serving as the backbone for understanding user needs and ensuring product functionality aligns with those needs. By effectively using these tools, teams can enhance communication, streamline development processes, and deliver high-quality products that meet or exceed user expectations.

--------------------------------------------------------
### Estimations and Velocity in Software Development

**Challenges in Software Estimation:**
- Software estimation is inherently challenging due to the diverse approaches engineers use in different companies. These can include variations in programming languages, coding styles, and ever-evolving technologies and methods. Such diversity makes it difficult to standardize estimation processes across different teams or projects.

**Understanding Velocity and Story Points:**
- **Story Points:** This is a technique used to measure the difficulty of tasks within a project. It involves a rating system that is universally understood within the company. Story points assess the effort required, complexity, and any risks or uncertainties involved in completing a task.
    
- **Velocity:** Velocity is a metric that quantifies the amount of work a team can complete in a specific time frame, typically measured over the course of a sprint (e.g., two weeks). It is calculated based on the number of story points the team completes during the sprint.
    

**Practical Example of Calculating Velocity:**
- **Scenario:** Consider a sprint where the team tackles five tasks.
- **Completion:** Out of these, three tasks are completed within the sprint.
- **Difficulty Rating:** Each completed task was challenging and rated 5 on a scale of 1 to 5.
- **Calculation:** The velocity for this sprint is the sum of the story points for the completed tasks: 5+5+5=15.

**Interpreting Velocity:**
- The velocity figure (15 in this example) represents the team’s capacity to handle work within a sprint. It helps in planning future sprints more accurately by providing a realistic picture of the team’s work rate and capacity.

**Using Velocity for Future Planning:**
- **Consistency:** Over several sprints, velocity can stabilize and serve as a reliable metric for planning and adjusting workloads.
- **Forecasting:** Teams can use historical velocity data to predict how much work they can realistically undertake in future sprints, aiding in better sprint planning and workload management.

**Benefits of Measuring Velocity:**
- **Predictability:** Helps teams and stakeholders set realistic expectations about deliverables and timelines.
- **Efficiency:** Encourages continuous improvement in work processes and team coordination.
- **Adaptability:** Allows teams to adjust their work strategies based on actual performance versus planned estimates.
**[Engineering flow: planning for high velocity sprints](https://www.fastcompany.com/3015928/engineering-flow-planning-for-high-velocity-sprints-part-3)**

### Roadmapping
[10 tips for creating an agile product roadmap](https://www.romanpichler.com/blog/10-tips-creating-agile-product-roadmap/)
[Atlassian roadmaps: build, share, use, evolve](https://www.atlassian.com/agile/product-management/roadmaps)

### Prioritization Techniques for Product Managers

As a product manager, effective prioritization is crucial in managing the development cycle efficiently. Here’s a structured look at several prioritization methods:

#### 1. **Assumption Testing**

**Overview:**
- Focuses on validating assumptions to minimize risks early in the development process.

**Process:**
- **Identify and List Assumptions:** Write down all assumptions related to the project.
- **Risk Assessment:** Assign a risk value to each assumption (1 being the riskiest, 10 being the least risky).
- **Importance Rating:** Rate the importance of testing each assumption (10 indicating very important).
- **Calculate Priority Score:** Add the risk and importance scores for each assumption.
- **Prioritization:** Sort the assumptions by their total scores, starting with the highest (indicating high risk and high importance).

#### 2. **The BUC Method**

**Overview:**
- Balances business benefits, user benefits, and costs to determine priority.

**Process:**
- **Score Dimensions:**
    - **Business Benefits:** Rate how much the task will benefit the business on a scale of 1 to 10.
    - **User Benefits:** Rate the potential benefits to the users on a scale of 1 to 10.
    - **Cost:** Rate the cost implications of implementing the task on a scale of 1 to 10.
- **Calculate Net Score:** Add the scores for business and user benefits, then subtract the cost.
- **Prioritization:** List tasks in descending order of their net scores, with tasks having the highest scores prioritized.

#### 3. **The MOSCOW Method**

**Overview:**
- Categorizes tasks into four buckets based on necessity: Must, Should, Could, and Won't.

**Process:**
- **Categorize Tasks:**
    - **Must Have:** Tasks that are essential for the launch or critical functionality.
    - **Should Have:** Important but not vital tasks, should be included if possible.
    - **Could Have:** Desirable tasks that are not necessary; can be included if it enhances the product without causing delays.
    - **Won't Have:** Tasks that are least critical and can be excluded from the current scope.
- **Execution Order:** Start with 'Must Have' tasks to ensure critical functionalities are developed first.

### Tips for Effective Prioritization
- **Regular Reviews:** Prioritization is an ongoing process. Regularly review and adjust priorities as new information becomes available or as project dynamics change.
- **Stakeholder Alignment:** Ensure that priorities align with broader business goals and are communicated clearly to all stakeholders.
- **Flexibility:** Be prepared to adapt your prioritization as project requirements and external conditions evolve.

### Conclusion

Each prioritization method offers different advantages and can be suited for various scenarios depending on the project's specific needs. Product managers should choose the method that best aligns with their strategic goals and project requirements, ensuring that resources are allocated efficiently to maximize product success.


Communication
[The introverted product manager](https://www.productplan.com/learn/the-introverted-product-manager/)
[The product manager Vs The engineering manager](https://www.huffpost.com/entry/the-product-manager-vs-th_b_7733156)
[Product Manager: 5 ways you can make the life of an engineer better](https://mtp2017.wpenginepowered.com/product-managers-5-ways-you-can-make-an-engineers-job-easier/)
[Can a product manager be effective without product design skills?](https://www.quora.com/Can-a-product-manager-be-effective-without-product-design-skills)
[4 design skills every PM should have](https://mtp2017.wpenginepowered.com/4-design-skills-every-product-manager-should-have/)
[How to Communicate Effectively at Work With Your Boss](https://blog.hubspot.com/marketing/communicating-effectively-with-your-boss)
[Front end Vs Back end](https://learn.onemonth.com/frontend-vs-backend-developers/)

### Product vision & Strategy
1. You can't create any good products or lead any company well without having clear, defined, transparent goals
2. You can't have good goals without first having a product/company vision
3. You can't have a good product/company vision without having a global vision
4. To have the best global vision possible, you've got to be as knowledgeable as possibe about your industry, technology, global events, and trends
5. Re-assess your global and company vision on a regular basis
6. Strategy isn't limited to one part of the development hierarchy 




