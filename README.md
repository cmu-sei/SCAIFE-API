# SCAIFE-API

This distribution of SCAIFE API definition files includes YAML, JSON, and HTML formatted files. There is one file in each file format for each of the five SCAIFE modules.

The YAML file specifies the Source Code Analysis Integrated Framework Environment (SCAIFE) API definition (currently v 1.0.0) [1, 2, 3, 5], in a format that developers can easily use to view, modify, and automatically generate code from (e.g., with the Swagger-Editor and Swagger-Codegen tools [4]). The YAML file was almost entirely manually created by SEI developers. The only things that were auto-generated by Swagger tools within the YAML file are some of the examples.

The JSON files were auto-generated by running Swagger-Codegen on the swagger.yaml files, since some developers prefer viewing the API in JSON or have code generation tools that work best with JSON. 

The HTML files also specify the SCAIFE API definition, in a format readable by people who prefer not to (or don't have tools to) read  YAML files. The HTML files can be viewed in any standard web browser. The HTML files contain hyperlinks, and the referenced whitepaper below provides guidance about how to understand the HTML files.

SCAIFE is an architecture that supports static analysis alert classification and prioritization. It is designed so a wide variety of static analysis tools can integrate with the system using the API definition we are developing. We expect the API to be of interest to organizations that develop and/or research static analysis tools, static analysis alert auditing aggregators, and other static analysis alert auditing frameworks. This SCAIFE API definition can be referenced by developers, to help them to estimate development effort that would be required to modify their organization’s tool(s) to make and respond to SCAIFE API calls. Also, this API definition is being published with a goal of generating feedback from developers and organizations interested in implementing the SCAIFE API, to help improve the SCAIFE API to become more easily usable by developers for a wide variety of static analysis tools. A prototype system that implements it has been distributed to research project collaborators.

Special notes for API reviewers:
* Thank you for sending us your API comments about what is useful and what could be modified to make the SCAIFE API more useful to you. Your review comments will help us to improve future versions of the SCAIFE API.
* We are using Swagger version 2, and some limits of Swagger version 2 have effects on the resulting API. For instance, Swagger version 2 does not enable file uploads and JSON-formatted data to be sent as parameters in the same API call. That caused our current API to require more API calls than it would otherwise. In the future, we plan to use Swagger version 3, which allows files and JSON-formatted data to be sent as parameters in one API call.
* Access tokens are used in the SCAIFE API, and [detail is provided here](access_tokens.md)


![Alt text](images/SCAIFE_architecture.png? "SCAIFE Architecture")

1. Lori Flynn, Ebonie McNeil, and Aubrie Woods. "SCAIFE API Definition Beta Version 0.0.2 for Developers", whitepaper, Software Engineering Institute, June 14, 2019. https://resources.sei.cmu.edu/library/asset-view.cfm?assetID=549351
2. Lori Flynn, Ebonie McNeil, and Aubrie Woods. "Integration of Automated Static Analysis Alert Classification and Prioritization with Auditing Tools: Special Focus on SCALe", technical report, Software Engineering Institure, May 13, 2019. https://resources.sei.cmu.edu/library/asset-view.cfm?assetid=546157
3. "Using Automation to Prioritize Alerts from Static Analysis Tools", Software Engineering Institute webpage on research topic, created September 2017. https://www.sei.cmu.edu/research-capabilities/all-work/display.cfm?customel_datapageid_4050=6453
4. Swagger pinned repositories. GitHub Website. https://github.com/swagger-api
5. Lori Flynn and Ebonie McNeil. "Rapid Construction of Accurate Automatic Alert Handling System (2019)", presentation, October 2019. https://resources.sei.cmu.edu/library/asset-view.cfm?assetid=635433 
