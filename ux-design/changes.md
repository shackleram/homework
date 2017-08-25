Hi,

For this exercise I’ll focus on a specific use case to let you know how I approached it. I’ve supplied some screenshots of the before and after flow and I’ve hidden the client’s name to protect the innocent (or something like that). I have a lot more examples on my portfolio, but I believe this is supposed to be anonymous so I won’t share that here.

I’ll start with some background to put it all in context.

##Background of Project

Earlier this year I was contracted by a Pension Group in Manhattan to lead the design and user experience of a Benefits Administration application. Due to some changes to their policies being implemented in 2018, they were under a time crunch to build a system that they could use to enroll new clients. The application would be used primarily by Customer Service Reps, but would also be accessible by other departments within the organization.

I worked closely with the Web Strategy group (including a junior designer), Developers and Business Analysts. We sat down with stakeholders and subject matter experts from each department to understand their needs, their current pain points, and generally what their typical workflow looks like. From these meetings we compiled a list of use cases, and after getting sign-off from each team, we built out wireframes, screens and interactive prototypes for each use case. Our primary tools were Sketch and InVision. 

We also made an effort to establish and follow general principles for a good user experience. These include, creating and using reusable design patterns, where possible. Showing content on a Need to Know basis; that is, don’t clutter the screen with unnecessary information. Live form validation. Avoid error messages, replace them with helpful hints. The primary button like Save should always be on the right, Cancel on the left. Use a consistent tab order, for example, left column then right column.

After reviewing the prototypes with the stakeholders and doing some light internal user testing (we were cramped for time), we iterated and tested a few times until we felt comfortable that the user’s needs were met, the flow was smooth and the experience was consistent throughout.

##Use Case

One of the many tasks a Customer Service Rep has to perform when enrolling an employee into a plan is Adding Beneficiaries. For each plan, different rules apply around who can be added and what allotments are allowed.

When we started the process the flow was as follows (see screenshots Pre_01 to Pre_05 for reference):

Show Rep a list of all the plans the employee is signed up for. Allow rep to Add a Beneficiary to a particular plan.
When the Rep clicks Add a Beneficiary allow them to search for a beneficiary in the system.
If the Rep searches, but cannot find the beneficiary, they can add one manually.
Once the beneficiary is added, they will show up under the specific plan and the Rep can adjust the contribution percentage allotted to that individual.

After reviewing this initial flow with the stakeholders we identified a couple of challenges. I’ve listed these challenge below, along with the solutions we came up with (refer to the screenshots New_00 to New_09 for reference)

####A. Adding beneficiaries using search was too time consuming and cumbersome

Solution: 
When a Rep clicks to add a beneficiary, we immediately show them a list of potential beneficiaries. If one of these is a match, it’s a one-click add. If not, the Rep will need to add a new beneficiary. 

Although there’s no way to avoid the drudgery of creating a new record and filling out a form, we did implement a few changes to make it a little easier. 

First, we skip the step of first searching for the beneficiary and take the Rep directly to the form. As they fill out the form, we do a live search to identify any close matches and present them to the Rep. If there are no close matches they submit the form.

Secondly, we grouped all required fields together at the top of the page, so they can fill these out first. These are also the fields we use for live search.

Thirdly, we performed live form validation, instead of waiting until they hit Save.

We also opted to automate as much as we could. For example, Child Benefits can only go to children of the employee. As the children are added to the system by a different group, if they exist, we populate them automatically as read-only, and the Rep doesn’t have to do anything.

Lastly, we added a Copy from Above feature to easily share information between plans.
	
####B. We need to differentiate between Primary and Contingent Beneficiaries. Furthermore, you cannot add a Contingent before one or more Primaries are added.

Solution: Under each Plan we added a label for Primary. And under each label we placed the Add Beneficiary button. Only after adding a Primary Beneficiary does the Rep see a second label for Contingent and a second button to + Add a Beneficiary.

####C. It was not clear enough to the Rep that they had to update percentages when two or more beneficiaries had been added. For example, 100% for one and 0% for another was not allowed.

Solution: After adding a second beneficiary, highlight the Percentage field and place the focus there so the Rep can deal with updating the numbers. If there’s only one Beneficiary, we make the Percentage field Read-Only as it can only be 100%.

####D. When adding a new beneficiary not already in the system, we have to take into account Beneficiary Type.

Solution: On the form screen to add a new beneficiary, show radio buttons for each beneficiary type, but default to the most common for the current plan and hide any types that are not applicable to that plan. If the Rep selects a different beneficiary type, update the form below accordingly.

####E. There were too many duplicate records for beneficiaries being created.

Solution: As mentioned in A., while the Rep fills out the form for a new beneficiary we would perform a live search for any close matches and present them to the Rep.

That’s it!
