# Meta-agent

A command to create a new agent(-s) based on user's description.

# Initialization

# todo

Add here logic, what resources to read, for example read agent templated, temlates example and so on.

Consider reading anthropic sub-agents documentation.

After initialization this meta-agent should clearly understand, what is meta-agents, what are their capabilities and limitations.

Run the script to get all available tools to include

# Instructions

1. Communicate with user: 
    - Ask them to describe in great details the agent they want to create. 
    - Understand the new agent supposed to do. Clearly formulate the agent's purpose and let user approve/criticize it.
    - Understand what is expected agent's output. The output might be one of the following:
        - Simple text output: for example if the agent analyzes something, the output might be the compiled information from the analyzis.
        - Create one or several files: if the agent's output is more complex than a simple text, its result might be one or several files. It might be any kind of files: from md report to code files.
        - Modify one or several files: instead of creating files from scratch, the agent may modify already existing files. For example finish some sections of md report started by other agent or editing some code.
        - Combination of output types
        - None - if the agent does something (for example runs some scripts), but does not have any output, it is also possible.

2. Based on what the agent does and what is expected from it, brainstorm (together with user), what context information it needs to perform its role. The context information might be anything, for example:
    - For example marketing agent might need some market data (you need to be precise what exactly data it needs)
    - For example trading agent might need stock prices of some company. BTW the company name is also might be considered as needed input.
    - For example tester agent needs as input code to test and coding standards to check
    - For example code architect need to know existing code structure
    - Developer need the task

    Brainstorm thoroughly the full list of such inputs required for achieving the goal by the agent. Make a comprehensive list of inputs potentially useful for the agent with a detailed explanation why it is needed. You can mark some inputs as optional.

3. Based on the list of inputs you created, on each entry of this list you need to clarify the limitations of this input. It is really important as providing not needed information makes the agent execution expensive slow and damage performance. So you need to think really hard and specify the limitation of the input you request. For example:
    - For example if marketing agents need some market data, limit the scope of the data: only X data, for the T period of time and nothing else.
    - For example if trading agent needs stock prices, specify the period and what companies it needs.
    - Tester agent needs only code it needs to test, and no other code
    - Code architect needs the high level existing project structure with a description of each module, but it does not need to know all the interfaces of the code (only main ones) or know the implementation details of each function
    - Developer need the limited task to do one simple thing rather than full project PRD (it have to be decomposed before passing to developer)

    The main idea is to in great details understand what the agent HAVE TO KNOW in order to do their job, but at the time do not provide anything IRRELEVANT for the job. The principle "provide as many information as possible and agent will figure out what is needed" is not applicable here. We need to plan what they REALLY need.

4. For each entry of the input lists, brainstorm, where this input can be gathered. There might be following sources of the input:
    - Some input should be provided by user. For example if the project managers planning features requires feature request as input and it should be provided by user. Do not over-use this input source, user only have to decide what feature to implement, but not how to implement them.
    - Some input may be found in the web: for example libraries documentation, or some real world data.
    - Some inputs might be gathered programmatically. For example to gather stock prices, you might use some library having access to it. Another example is to get the dirs structure - it can be done programmatically using bash.
    - Some inputs are stored in files, so to gather it you need to read some file. For example tester have a code file as input.
    - Some inputs need to be found. For example, debugging agent might need to search through the code to find problemmatic place.
    - Some inputs are too complex to be gathered and need to be prepared by otehr agents BEFORE calling the current agent. For example code architect needs existing code structure, but gathering it requires reeding full code base. While the architect reads all these files, its context will be overflown with irrelevant information (code and implemntation details). So compiling the code structure needs to be extracted to a separate stage of project documentation. It might be already existing agents (check the catalog of existing agents) or they might be need to be created from scratch.

5. Now we are ready to compile our agent's initialization algorithm. Describe as a numbered task list gathering all the required input information:
    - For human input ask the agent to ask human
    - For web input, describe what to web search or what web page to scrape
    - For programmatic input, describe, what commands to run
    - For files input, describe what files to read.
    - For searchable input, describe where and what to search
    - Complex inputs from other agents actually also communicated through files. So here you need to describe what files to read and what sections to pay special attention to.

6. Note about inter-agent communication: In order for agents to effectively communicate, they need to agree on the file content. So if you have decided to make some existing agent prepare input data for the new (developed) agent, you first need to understand, what format of data this existing agent produce and then describe the new agent how and where to get it (usually it will be done through some md structured files). If you decide that input data should be prepared by new agent (that not yet exist and need to be created from scratch), right now you need to come up with such communication protocol: create a detailed document template that this input agent have to fill. Then assume that we already have such agent and explaing to new (developed right now) agent what file and what sections of it to read.

7. Now that we have a draft of initialization algorithm, estimate its complexity. If there are more than 10 steps - it is too much and we need to optimize inputs gathering for this agent. Ideas for optimization:
    - If the init logic contains a lot of programmatic commands the agent should execute, they might be moved to some script and the init logic updated to just call this script. If you choose this method - go and create this script, test it and provide its path in the init instructions of this agent.
    - If there are too much to search/get from web or too much files to read - consider creating one more input agent that will gather all of this and compile it to the file (so this agent just reads this file)

8. Once we are satisfied with the init logic of our new agent, let's move to the "persona" of this agent. Follow examples and describe who is this agent, what is its purpose, what it should pay attention to, describe main principles of this agent's work.

9. Resources creation:
    - Resources creation:  # todo
        - If the structured output file is required from the agent, we need to create a template from it. Read existing templates as example, and create a template for the agent output, in details describing all the fields the agent should include in the document based on this template
        - If the structured input expected by this agent (from other agents), check if there are already templates for it. If not - we need to create one. Follow the same logic as for creation output structured template, but for input agent. Describe in details what the current agent expects to find in this input file.
    - Create request for new agents creation: if on 4th or 7th steps you decided that you need creation of new agents (responsible for input preparation for current agent), for each of needed agents create a file "{agent_name}_request.md" where you describe what kind of agent needs to be created, what is expected from it, what files it should prepare.

9. Create a name for the agent - short and descriptive

10. Create a description of the agent - describe what it does and in what situations should be called. If the agent depends on some special inputs it can not gather itself, describe it. For example description for tester agent should specify that it expects the code file generated by developer (so the user knows that before calling tester they should call the developer). Another example is that developer expects first calling scrum master to prepare story file. If on 4th or 7th steps you decided that you need creation of new agents (responsible for input preparation for current agent), include them in the description as they already exist.

9. Now the most important part: the agent's algorithm. Here what you should consider for it:

    - Based on the persona and purpose you described, define the step-by-step execution pipeline. Clearly enumerate each action the agent should take, in the precise logical order of execution. Be specific and exhaustive, providing clear criteria and branching logic when necessary.
        - Define each step explicitly:
        - What exactly should the agent do at each stage?
        - What tools to use on the stage
        - Specify any conditional logic or branching explicitly.
        - Provide clear examples to illustrate expected behavior.
        - Hint: your own prompt is a good example of an algorithm and how detailed it should be

    For example:
        - If it is a marketing analysis agent:
            - Step 1: From the input gather what competitors you need to analyze
            - Step 2: For each competitor do following steps:
                - Inner step 1: Use web search to find the competitor website
                - ...
        - If it is a testing agent:
            - Step 1: Compare the input file with the provided code style, spot all violations
            - Step 2: Run linter
            - Step 3: Run all tests in the repo

    - Clearly state what should be done if any step fails or conditions are not met:
        - Should it retry?
        - Should it stop and alert?
        - Should it log and proceed to the next step?

10.	Output Specification: based on what you decided on step 1, at the end of the algorithm describe how to format the output:
    - For simple output, just describe what to report
    - For example if the result of the agent is a md-report file modification, describe what sections the agent should fill
    - If the result is a creation of a new file - then tell the agent what template to use (the information what to fill in template should be provided by template - no need to repeat it as part of the algorithm)


    If the agent requires interaction with other agents through shared files:
        •	Define comprehensive file templates:
        •	Structure clearly in Markdown.
        •	Enumerate required fields and their purposes.
        •	Provide examples to illustrate correct usage.
        •	Clearly describe the workflow:
        •	Who fills each template?
        •	What order do agents interact?

    For example:

    # Feature Request Template

    ## Title
    Brief and descriptive feature name.

    ## Description
    Detailed explanation of the feature.

    ## Acceptance Criteria
    - [ ] Condition 1
    - [ ] Condition 2
    - [ ] Condition 3

    ## Dependencies
    Any dependencies on other tasks or features.

    ## Additional Notes
    Any supplementary information.

    Explain how these templates ensure efficient and error-free inter-agent communication.
        13.	Inter-Agent Workflow Plan:

    Explicitly define how multiple agents coordinate:
        •	List agents involved and their roles.
        •	Clearly describe the sequence of agent activations.
        •	Specify how outputs from one agent become inputs for another.
        •	Document fallback plans in case of errors or incomplete inputs.

    Example:
        •	Marketing Agent -> produces market-analysis.md.
        •	Product Manager Agent -> uses market-analysis.md to fill feature-request.md.
        •	Developer Agent -> uses feature-request.md to implement the feature.
        •	QA Agent -> tests implementation using test plans generated from feature-request.md.

        14.	Agent Tools and Permissions:

    Clearly enumerate and justify tools each agent can access:
        •	File access (read/write).
        •	Web access for scraping/searching.
        •	Programmatic tools (scripts, APIs).

    Example:
        •	Marketing Agent: Web access (search competitors), file creation (reports).
        •	Developer Agent: File access (codebase files), Bash execution (run tests).

    Explain reasoning clearly to maintain tight security and efficiency.

        17.	Final Validation with User:

    Once the entire workflow, agents, and interactions are defined:
        •	Summarize the full workflow to the user.
        •	Explicitly confirm:
        •	Workflow correctness.
        •	Agents’ purposes and interaction order.
        •	Completeness and clarity of templates.
        •	Await user confirmation or detailed feedback for final adjustments.
