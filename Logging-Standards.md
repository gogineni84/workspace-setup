# General Log Standards
| #    | Requirement   | Complete?   |
|------|---------------|-------------|
| 1    | Log with nationwide JSON logging appender: "json-event-layout"  -->  Library for logging in JSON               |     □       |
| 2    | Mask all confidential data that gets written to logs.              |     □       |
| 3    | Log every Request the application sends and receives (i.e. outbound ECIF requests, outbound PBS requests, inbound PPS requests, etc.).              |     □       |
| 4    | Log every Response the application sends and receives (i.e. Responses from ECIF, PBS calls or responses sent from PPS requests, etc.).              |     □       |
| 5    | Log SQL statements that get executed by the application. Include the database, schema, and username that the call is using.              |     □       |
| 6    | Have a unique identifier to follow a user/batch job through their session to completion throughout applications. Add this identifier every place it is available. We will want to monitor a user through their session or a batch job through its processing.              |     □       |
| 7    | Have an identifier that logs where a user/batch job is at in the application. This will help us identify what place in an application a user/job is interacting with. It can also help us tell where errors/data issues are experienced to help track down root cause for incidents. <ul><li>App specific.</li> <li>Have a unique identifier in mdc, as long as it does not cause threading issues.</li> <li>See below</li></ul>              |     □       |
| 8    | Clean up “allowed” exceptions and print them as informational or warnings (i.e. an invalid username/password for a user logging in is not an application failure so it should be informational).<ul><li>Define the difference between warning, errors, and informational exceptions.</li> <li>See below</li></ul>              |     □       |
| 9    | Refrain from using keywords such as “error” and “exception” unless there was an exception (i.e. avoid saying “no error occurred” and instead use “successful”).              |     □       |
| 10   | Break out logs into a location other than the SystemOut.log. SystemOut.log is owned by Java Hosting and having our own logging space will be beneficial to our teams.              |     □       |


# Standard #7
~~~~
sourcetype="iam_application" "Step Details"

{
    "timestamp": "2017-08-31T09:56:55.146-0500",
    "message": "Step Details - flow: \"STANDARD_REGISTRATION\", stepExit: \"PERSONAL_INFO\"",
    "loggerName": "com.nationwide.corporate.iam.util.logging.IndividualPartyFlowLogHelper",
    "level": "INFO",
    "threadName": "WebContainer : 19",
    "app": "iam",
    "env": "PROD",
    "node": "PVMA0167",
    "cell": "PVMA0150",
    "mdc": {
        "partyId": "",
        "GUID": "",
        "UUID": "20170831-104501067_e9fb41ff-ce68-4405-b918-ed732f695cb4",
        "username": ""
    },
    "ndc": "AQwEJh"
}
~~~~

# Standard #8
* ERROR 
Designates error events that will most likely cause the user/request to fail. Anything that causes a halt in the normal business flow. Example: NullPointerException, dependency not available, database down.
* WARN
The process might be continued, but take extra caution. Possibly two levels here: one for obvious problems where 
work-around exists (for example: “Current data unavailable, using cached values”) and second (name it: ATTENTION) for potential problems 
and suggestions. Example: “Application running in development mode” or “Administration console is not secured with a password”. 
The application can tolerate warning messages, but they should always be justified and examined.
* INFO
Important business process has finished. In ideal world, administrator or advanced user should be able to understand INFO messages 
and quickly find out what the application is doing. For example, transitioning through a workflow, incoming/outgoing api responses. Other definition of INFO 
message: each action that changes the state of the application significantly (database update, external system request).
* DEBUG
Result of internal logic that helps developers understand what is happening.
* TRACE
Very detailed information, intended only for development. You might keep trace messages for a short period of time after deployment 
on production environment, but treat these log statements as temporary, that should or might be turned-off eventually. 
The distinction between DEBUG and TRACE is the most difficult, but if you put logging statement and remove it after the feature has 
been developed and tested, it should probably be on TRACE level.
* FATAL (Saving for future implementation)
Very severe errors that cause the application to fail. Example: NPE, database unavailable, mission critical use case cannot be continued.
# Application specific logging standards
* Each application will have to define