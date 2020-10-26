# Shell Command Test
The `shellcommand_test` is intended to allow for the collection and evaluation of standard output information following the execution of read-only commands and command pipelines.  The test extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references a `shellcommand_object` and the optional state element specifies the metadata to check.

## Example
```
<shellcommand_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd" id="oval:org.cisecurity.benchmarks.o_amazon_amazon_linux:tst:7697100" check="at least one" check_existence="at_least_one_exists" comment="Ensure kernel module cramfs is not loadable" version="1">
	<object object_ref="oval:org.cisecurity.benchmarks.o_amazon_amazon_linux:obj:7697100"/>
	<state state_ref="oval:org.cisecurity.benchmarks.o_amazon_amazon_linux:ste:7697100"/>
</shellcommand_test>
```

# Shell Command Object
The `shellcommand_object` defines the command or command pipeline to be executed as well as any standard output line selection criteria, allowing content authors to apply regular expressions to each line of standard output (stdout) in order to enhance collection.

## Object Elements
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| command | EntityObjectStringType | The full shell command or command pipeline to execute|
| line_selection | EntityObjectStringType | The regular expression outlining which lines of command output are collected.|

## Example
```
<shellcommand_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd" id="oval:org.cisecurity.benchmarks.o_amazon_amazon_linux:obj:7697100" comment="Ensure kernel module cramfs is not loadable" version="1">
	<command>modprobe -n -v cramfs</shell:command>
	<line_selection operation="pattern match">.+</shell:line_selection>
</shellcommand_object>
```

# Shell Command State
The `shellcommand_state` defines the criteria against which collected command/command pipeline output is evaluated in order to determine compliance to an expected configuration.

## State Elements
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| command | EntityStateStringType | The full shell command or command pipeline to execute|
| line_selection | EntityStateStringType | The regular expression outlining which lines of command output are collected.|
| exit_status | EntityStateIntType | The exit status value from the command|
| stdout_line | EntityStateStringType | A line of standard output from the shell command/command pipeline|
| stderr_line | EntityStateStringType | A line of error output from the shell command/command pipeline|

## Example
```
<shellcommand_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd" id="oval:org.cisecurity.benchmarks.o_amazon_amazon_linux:ste:7697100" comment="Ensure kernel module cramfs is not loadable" version="1">
	<stdout_line entity_check="at least one" operation="pattern match">^install +/bin/true *$</stdout_line>
</shellcommand_state>
```

# Shell Command Item
A `shellcommand_item` represents the system characteristics collected when executing a particular command/command pipeline, and applying the line selection criteria.  Because many standard output or standard error lines could be returned when executing a command or command pipeline, in a `shellcommand_item` the `stdout_line` and `stderr_line` elements allow for an unbounded number of entries.

## Item Elements
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| command | EntityItemStringType | The full shell command or command pipeline to execute|
| line_selection | EntityItemStringType | The regular expression outlining which lines of command output are collected.|
| exit_status | EntityItemIntType | The exit status value from the command|
| stdout_line | EntityItemStringType | Each line of standard output from the shell command/command pipeline (0..unbounded)|
| stderr_line | EntityItemStringType | Each line of error output from the shell command/command pipeline (0..unbounded)|
