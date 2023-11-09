# LF Cloud Native Networking Program Alignment Workshop 2023
- Tuesday, November 7th, 2023 a 2-4pm CST 
- KubeCon North America 2023
- Recording available at: https://wiki.lfnetworking.org/x/mIC-Bg

## Agenda

- (10 min) - Opening Remarks, Ranny
- (10 min) - Collaborative Workshop, Moderator
- (20 min) - Topic 1: High Level Scope & Priorities, Participants
- (20 min) - Topic 2: Positioning / Governance, Participants
- (20 min) - Topic 3: Assets, Participants
- (20 min) - Topic 4: CSP & Vendor Engagement/Demand, Participants
- Next Steps & Closing Remarks, Ranny

## Brainstorming Output

### Topic 1: High Level Scope & Priorities

Platform and Workloads
- Creating CNF <-> platform tests may not be feasible.
- There is too much variance between platforms.
- Better to focus on the CNF level tests.
- Platform needs to be defined as well as the workloads
- If the scope is e2e, we should include platform testing to the first priority targets.
- We could have a layered scope (Sylva specific, Nephio specific, Google specific, etc).
- CNF vendor layer|cnf compatibility | platform compatibility.
- Creating common vendor neutral + upstream based reference for certification and conformance

Types of tests/coverage
- Distributed applications
- Distributed workloads
- Help needed with multi-cloud practices

Community Collaboration and Output
- Scope is hard to parse.  What is the output and how does it relate to other projects?
- Anuket works with GSMA and this is important to maintain to keep up with the industry
- Need to coordinate between initiatives for practices not just definitions. 
- Avoid having multiple programs for the same thing
- Community interaction must be included (avoid a silo)
- Connection with other implied cloud native telco ecosystems + standards bodies
- Is this an open-source initiative, i.e. alignment within open source communities?
- CSPs can call a referendum and veto proposed principles

Other feedback/questions
- Live lab, CI/CD, e2e lab
- Provide local CI runners
- Roles – Need to help define who brings what
- Vendor CNF dashboard
- Concern – how to assure to have good visibility of CNF requirements and specifics in CNCF
- Secondary networking CLIS in K8s for telco network solutions
- Zero trust networking – Security
- Agree
- Should live out CNF internal architecture of the scope (believe the comment is about ignorning internal CNF architecture from scope of the initiative)
- Makes sense – practical & brings concrete value add
- Clear linkage between end users (telco, CSPs) and the work output (especially testing programs)
- Is the anticipated output best practice docs, test plans, and certification or testing program? Something else?

### Topic 2: Positioning & Governance

Merging Scope
- Less is more
- Challenge - covering LFN and CNCF topics in same meeting
- We should merge the overlapping activities, like CNF WG and RA2, CNF Testsuite and RC2 and testbed
- We need to communicate what happens to Anuket Assured
- Managing many different projects and initiatives will be challenging - initiative is vague

Structure
- Contributions by "PowerPoint" people should be possible. Requirements should be in English
- Something new is better than Anuket or CNCF (Pull from multiple sides and buy-in needed)
- Working group sounds natural for continuity
- Agree this should be a new entity so it provides value to many LFN projects
- New work group perhaps? These options need elaboration
- No challenge for having this under LFN board
- New structure preferred but optimize existing outcomes of current projects
- More coherence and focus on c-n tranformation would be beneficial instead of fit to all intiatives
- It should not be a "resource" under LFN, but something what is a valid LFN construct like a project
- Do we envision this governed as a project? It needs governance.
- TOC? to streamline Northstar goals and enabling coordination of workgroup(s)
- Seems vague and disconnected which leads to accountability problems
- Should the effort report metrics or accountability up to LFN board

Output
- We should be able to produce the GSMA docs like RM, RA1 and RA2
- Should be good enough that Sylva uses it
- Provide similar solutions
- Less focus on tooling, more on engagement with CSP end users
- Getting disconnected from c-n mainstream

### Topic 3: Assets

Assets
- Need a thorough audit of assets
- The XGVela project is an asset to consider
- Anuket assets are still mixed b/t CNTT and GH mirrors and using GH directly
- No mention of the current test plans from Anuket and CNCF
- Alignment to Sylva is a must
- De-duplication should be higher priority than non interuption

Onboarding and Contribution
- Tools should not have high barriers to contribution
- Self service to the extent possible is important
- Any tools we decide upon needs to be well supported by LFN and easy to use/collaborate
- Follow the LFN project processes and build on community agreement
- Is the testing self-testing, in-lab testing, self delegation?
- Autonomy (Independant to start but build bridge)

Use Case Output
- Providing guidance on tool output (test output) might make it easier to onboard new or existing tools
- Vertical focus - tooling should be unopinionated
- Is there a plan for functional vs performance testing?
- How is the integrity of results being maintained or preserved (i.e. tool output -> cert or badge)?
- Testing specifications from other organizations, e.g. standards, can these be reused/leveraged?
- Local standup (dev work place)
- All of the ideas mentioned in the slide are good but it will not be easy to realize them.  A substantial investment will be needed.
- Industry wide plugfests?
  
### Topic 4: CSP and Vendor Engagement/Demand

Drive: Use Case, End Users, and Marketing
- RFP/RFQ
- We need cloud provider engagement as part of the ecosystem
- Hyperscaler telco BU co-sell
- We need to hear from CSPs how this initiative can/will help them
- Select a use case and create a showcase to promote at some CSP forum to create support
-  MWC, GSMA
-  Confidence building in vertical events (MWC)
-  Ensure we capture us case from end users (CSPs) to devel output and drive testing or programs
-  Direct interests: Vendors, contributors
-  Affected interests: CSP, purchasers, consumers
-  Afftected intrets should have a veto (CSPs)
-  Provide success stories to incentivize the participation
-  Clear value proposition and focus: Reduce integration costs, more cloud native architecture, easier management
-  What would be vendors incentive to comply with cloud native?
-  Need a catchy name for the program
-  CSPs should incorporate that process in their RFx and vendor selection processes
-  Alignment on criteria/expectations fro conformance, requirements, best practices, patterns

Tools, Testing, Ease of Use
- CSPs will want performance testing which will drive interest and involvement on thier side - security as well
- Usage in devops by the CSP (i.e. the tools and tests are directly used in their operational pipelines)
- Testsuite as a service (SaaS)

Output, metrics, value
- Downstream consumption
- For CSPs to embrace any certification it has to bring value
- Reward participation with awards
- Testing conformance validation as a means to unblock CSP road to Cloud Native
- CSPs have requested certification models and when delivered they have abandoned them
- Comparisons between VNF and CNF systems demonstrate the cost savings or returns for end users
- How can CSPs trust the outcomes from certification process? How to measure the quality of the certification?
- Both CNF and platform vendors need to engage
- Software and cloud vendors engagement and support will be crucial for practical outcomes of any certification program
- Community engagement is the key. With the community we should identify a small number of focal points
- Leverage testing specifications in which telco industry has already invested in

