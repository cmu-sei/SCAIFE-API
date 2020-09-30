# SCAIFE-API

This distribution of SCAIFE API definition files includes YAML, JSON, and HTML formatted files. There is one file in each file format for each of the five SCAIFE modules.

The YAML file specifies the Source Code Analysis Integrated Framework Environment (SCAIFE) API definition [1, 2, 3, 5], in a format that developers can easily use to view, modify, and automatically generate code from (e.g., with the Swagger-Editor and Swagger-Codegen tools [4]). The YAML file was almost entirely manually created by SEI developers. The only things that were auto-generated by Swagger tools within the YAML file are some of the examples.

The JSON files were auto-generated by running Swagger-Codegen on the swagger.yaml files, since some developers prefer viewing the API in JSON or have code generation tools that work best with JSON. 

The HTML files also specify the SCAIFE API definition, in a format readable by people who prefer not to (or don't have tools to) read  YAML files. The HTML files can be viewed in any standard web browser. The HTML files contain hyperlinks, and the referenced whitepaper below provides guidance about how to understand the HTML files.

SCAIFE is an architecture that supports static analysis alert classification and prioritization. It is designed so a wide variety of static analysis tools can integrate with the system using the API definition we are developing. We expect the API to be of interest to organizations that develop and/or research static analysis tools, static analysis alert auditing aggregators, and other static analysis alert auditing frameworks. This SCAIFE API definition can be referenced by developers, to help them to estimate development effort that would be required to modify their organization’s tool(s) to make and respond to SCAIFE API calls. Also, this API definition is being published with a goal of generating feedback from developers and organizations interested in implementing the SCAIFE API, to help improve the SCAIFE API to become more easily usable by developers for a wide variety of static analysis tools. A prototype system that implements it has been distributed to research project collaborators.

## SCAIFE

![Alt text](images/SCAIFE_architecture.png? "SCAIFE Architecture")
The SCAIFE architecture shown in the figure includes five servers. The system is modular, designed so each module can be instantiated by different tools/software while the overall system should maintain the same functionality. The UI Module has a GUI front-end that enables display of flaw-finding static analysis (FFSA) alerts and stores local projects. The SCAIFE architecture is intended to enable a wide variety of FFSA tools and alert aggregator tools to obtain classification and prioritization functionality by interacting as a UI module with the rest of the SCAIFE system. These tools must instantiate UI module API calls to the other servers, to do so. The Datahub module stores data (tool, alert, project, test suite meta-data, adjudicatons, etc.) from one or more UI modules and adjudicates some meta-alerts. The Statistics module creates, runs, and stores classifiers and adaptive heuristic (active learning) algorithms and automated hyper-parameter algorithms. The Prioritization module stores prioritization formulas and user-uploaded prioritization fields. The Registration module is used for authentication and access control. It generates registration tokens, plus it provides authentication and basic authorization for other servers.


## How to get started with the API

Select one of the five modules to start inspecting.: 
Most FFSA tool and alert aggregator tool developers will be most interested in the UI Module's API definition. To enable their tool to interact with the SCAIFE system, their tool needs to instantiate the UI Module's API.
However, some researchers/developers focused on improving classification, active learning, and automated hyper-parameter optimization will instead want to focus on the Statistics Module's API. They can develop new algorithms and modularly incorporate them within a prototype we've developed (if they are our research collaborator) or simply modify their own tools to instantiate the Statistics Module's API and then interact with a SCAIFE system with other modules developed by different people (e.g., for a UI Module they could use the version of SCALe we developed to work modularly with SCAIFE).
Similarly, some researchers/developers have a focus on improving performance, security, resilience, and scalability of aggregated and eventually expected-to-be-large data storage. Those people will want to focus on the DataHub Module's API.
We expect a smaller number of researchers/developers to implement Registration or Prioritization modules. However, their APIs will still be useful to review, since other servers need to interact with them whether in a client or a server role.

If you can, we encourage you to use the open-source (and free) Swagger Editor [4] or a similar API viewing and editing tool. Open an API definition file (.yaml or .json) in that. Swagger Editor provides a user-friendly way to view, do simple tests, and modify the API definition.

Otherwise, view the HTML API definition file in a web browser. This way, the models and methods can be accessed by following the hyperlinks associated with each resource in the SCAIFE API Definition section below. 

Each API definition section is categorized based on the source and destination modules of the API calls. For instance, the Rapid Models Registration and Login Module API Definition section contains only one category of API calls under the label
UIToRegistration. The source (request) of the API calls comes from the UI Module, and the API calls are forwarded to the destination—the Registration Module. Data models are defined in the bottom section of the file.


Hopefully you won't only inspect the API, you will use it to integrate your tool or code into a SCAIFE system. You can automatically generate code from the YAML or JSON API definition of any of the SCAIFE modules, using Swagger Codegen [4] or similar tools. This not only has the benefit of accelerating and automating code development, but it also ensures that code instantiates the SCAIFE API. If you have a tool you want to generate client code for (meaning, you want code that will make a call to a SCAIFE server defined in that server's API definition), tools like Swagger Codegen will generate code in any of a wide variety of languages. You can plop the generated client code into your own code in the right place, and use your own variables as the parameters. Similarly,you can automatically generate server code for any of the SCAIFE modules, including controller function stubs for each of the API calls to that server that you will then flesh out internal code for.

Special notes for API reviewers:
* Thank you for sending us your API comments about what is useful and what could be modified to make the SCAIFE API more useful to you. Your review comments will help us to improve future versions of the SCAIFE API.
* We are using Swagger version 2, and some limits of Swagger version 2 have effects on the resulting API. For instance, Swagger version 2 does not enable file uploads and JSON-formatted data to be sent as parameters in the same API call. That caused our current API to require more API calls than it would otherwise. In the future, we plan to use Swagger version 3, which allows files and JSON-formatted data to be sent as parameters in one API call.
* Access tokens are used in the SCAIFE API, and [detail is provided here](access_tokens.md)




## Related Information

1. Lori Flynn and Ebonie McNeil. "SCAIFE API Definition Beta Version 0.0.2 for Developers", whitepaper, Software Engineering Institute, June 14, 2019. https://resources.sei.cmu.edu/library/asset-view.cfm?assetID=549351
2. Lori Flynn and Ebonie McNeil. "Integration of Automated Static Analysis Alert Classification and Prioritization with Auditing Tools: Special Focus on SCALe", technical report, Software Engineering Institure, May 13, 2019. https://resources.sei.cmu.edu/library/asset-view.cfm?assetid=546157
3. "Using Automation to Prioritize Alerts from Static Analysis Tools", Software Engineering Institute webpage on research topic, created September 2017. https://www.sei.cmu.edu/research-capabilities/all-work/display.cfm?customel_datapageid_4050=6453
4. Swagger pinned repositories. GitHub Website. https://github.com/swagger-api
5. Lori Flynn and Ebonie McNeil. "Rapid Construction of Accurate Automatic Alert Handling System (2019)", presentation, October 2019. https://resources.sei.cmu.edu/library/asset-view.cfm?assetid=635433 
