## Jira Terminal

This application can be used for personal usage to manage jira from terminal.

## Installation
You can download this application from [https://github.com/amritghimire/jira-terminal/releases](https://github.com/amritghimire/jira-terminal/releases)
After you download this application, be sure to move it to one of the PATH.

One of such path is `~/.local/bin/`

## Usage
When running the application for first time, you will be asked with following values.
- namespace [This will be used to identify the namespace to be used.]
- email [Email address you use to login with the application.]
- token [You can obtain the app password from the link specified in the application]

After that, you can use following commands for help.
```
jira-terminal help
jira-terminal help list
jira-terminal help transition
jira-terminal help alias
jira-terminal help detail
jira-terminal help fields
jira-terminal help update
jira-terminal help new
```

```
Amrit Ghimire <oss@amritghimire.com>
This is a command line application that can be used as a personal productivity tool for interacting with JIRA

USAGE:
    jira-terminal [SUBCOMMAND]

FLAGS:
    -h, --help       Prints help information
    -V, --version    Prints version information

SUBCOMMANDS:
    help          Prints this message or the help of the given subcommand(s)
    list          List the issues from JIRA.
    transition    Transition of ticket across status.

```

### List of Tickets
```
jira-terminal-list 
List the issues from JIRA.

USAGE:
    jira-terminal list [FLAGS] [OPTIONS]

FLAGS:
    -h, --help       Prints help information
    -M, --me         Issues assigned to you.
    -V, --version    Prints version information

OPTIONS:
    -A, --alias <ALIAS>               Save the applied options as an alias. You can use it with jql option later.
    -a, --assignee <ASIGNEE>...       Assignee username or email to filter with.
    -c, --component <COMPONENT>...    Component name or ID to filter with.
    -d, --display <DISPLAY>            Comma separated list of fields to display.
                                      Possible options for fields are: 
                                      key,resolution,priority,assignee,status,components,creator,reporter,issuetype,project,summary
                                      
                                      You can pass alias as option for display. You can save alias using alias
                                      subcommand for the application.
                                      
                                       Default options are
                                       key,summary,status,assignee
                                                         
    -e, --epic <EPIC>...              EPIC name or issue key of epic to filter with.
    -f, --filter <FILTER>...          Filter name or filter id that you saved in JIRA.
    -j, --jql <JQL>                   JQL Query or alias to JQL query to filter with.
    -l, --label <LABEL>...            Search for issues with a label or list of labels.
    -m, --main <PARENT>...            Search for subtask of a particular issue.
    -P, --priority <PRIORITY>...      Search for issues with a particular priority.
    -p, --project <PROJECT>...        Project Code to filter with.
    -r, --reporter <REPORTER>...      Search for issues that were reported by a particular user.
    -s, --sprint <SPRINT>...          Search for issues that are assigned to a particular sprint.
    -S, --status <STATUS>...          Search for issues that have a particular status.
    -T, --text <TEXT>                 This is a master-field that allows you to search all text fields for issues.
    -t, --type <TYPE>...              Search for issues that have a particular issue type. 

```

### Transition

```
jira-terminal-transition 
Transition of ticket across status.

USAGE:
    jira-terminal transition [FLAGS] <STATUS> --ticket <TICKET>

FLAGS:
    -h, --help       Prints help information
    -l, --list       List the possible transitions.
    -V, --version    Prints version information

OPTIONS:
    -t, --ticket <TICKET>    Ticket ID from JIRA.

ARGS:
    <STATUS>    Status or alias of status to move the ticket to.

```


### Alias
```
jira-terminal-alias 
Configuration for alias. One of add,list or remove is required.

USAGE:
    jira-terminal alias [FLAGS] <NAME> --add <add> --list --remove

FLAGS:
    -h, --help       Prints help information
    -l, --list       List the alias saved.
    -r, --remove     List the alias saved.
    -V, --version    Prints version information

OPTIONS:
    -a, --add <add>    Value to associate with provided alias name.

ARGS:
    <NAME>    Name of alias. (Required except for list option)
```

Sample usage:
- `jira-terminal alias -l`
- `jira-terminal alias alias_name -a "Alias Value"`
- `jira-terminal alias -r alias_name` 

### Detail
```
jira-terminal-detail 
Detail of a JIRA tickets..

USAGE:
    jira-terminal detail [OPTIONS] <TICKET>

FLAGS:
    -h, --help       Prints help information
    -V, --version    Prints version information

OPTIONS:
    -f, --fields <fields>    Comma separated lists of fields or alias to show.
                             Possible options are: 
                             key,summary,description,status,issuetype,priority,labels,assignee,components,creator,reporter,project,comment
                             
                             You can use all to show all fields.
                             Default selection are:
                             key,summary,description
                                                 

ARGS:
    <TICKET>    Ticket id for details.

```

### Fields
```
jira-terminal-fields 
List of possible Fields for details...

USAGE:
    jira-terminal fields <TICKET>

FLAGS:
    -h, --help       Prints help information
    -V, --version    Prints version information

ARGS:
    <TICKET>    Ticket id for details.
```

### Update
```
jira-terminal-update 
Update a field for a ticket

USAGE:
    jira-terminal update <TICKET> --field <field> --value <value>

FLAGS:
    -h, --help       Prints help information
    -V, --version    Prints version information

OPTIONS:
    -f, --field <field>    Key of field to update. You can use jira-terminal fields <TICKET> to see possible set of
                           keys.
    -v, --value <value>    Value of the field to update.

ARGS:
    <TICKET>    Ticket ID to update
```


### New
```
jira-terminal-new 
Create a new ticket.

USAGE:
    jira-terminal new [FLAGS] [OPTIONS] --main <main> --project <project>

FLAGS:
    -h, --help       Prints help information
    -M, --mininal    Only summary and description will be asked if not available.
    -q, --quiet      Do not ask for missing options.
    -V, --version    Prints version information

OPTIONS:
    -a, --assignee <assignee>          Assignee email of ticket
    -c, --components <components>      Comma separated list of components of ticket
    -C, --custom <custom>              Comma separated value pair for custom fields. You can use alias in value or key
                                       itself. Example- "customfield_12305:value,alias_to_key:value2. You can use fields
                                       subcommand to check the list of custom fields available. 
    -d, --description <description>    Description of ticket
    -l, --labels <labels>              Comma separated list of labels.
    -m, --main <main>                  Main tiecket to create the sub-ticket.
    -p, --priority <priority>          Priority Of the ticket.
    -P, --project <project>            Project Key to create the ticket.
    -s, --summary <summary>            Summary of ticket
    -t, --type <type>                  Issue type for new ticket.
```
