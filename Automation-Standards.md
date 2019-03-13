# EDS test automation suite standards

## Miscellaneous
* Current project structure, with feature / scenarios, step definitions, support
* Decrypt all passwords at start of test execution and cache them to use later as needed
* Tag with RTC # for tech cards, RRC # for story cards, QC # for defects, needs_review, manual, local
* ‘Requires’ statements should be above module/class definitions (at the top of the file)
* Ability to override some fields in the customer model (something like merge_data_into_customer_model)
* Swagger validation features
* Rubocop and reek definitions in CIAM (can copy those into other suites as well)
* Exclusively use element IDs to define elements in the suites
* Ensure that scenarios are only testing what they say they are testing (don’t check random stuff along the way, just get to where you need to go and check what you need to check)
* Prefer ruby 1.9 syntax for hashes when key is a symbol (i.e. {key: ‘value’, next_key: ‘next_value’} instead of {:key => ‘value’, :next_key => ‘next_value’}
* Common environment nomenclature across test suites (e.g. dev vs devl), especially when used as environment variable keys.
* Move preferences into customer_model
* Better page object utilization — page sections, usage of page object methods
* Find other ways to wait than using a sleep
* Risk based testing\
Ensure that we’re automating scenarios that should be regression tested

## Step definitions and scenarios
* Step definition files for step definitions only\
Do not define methods within a step definition file
* Don’t use nested steps, prefer using the steps themselves in the scenario and keep steps as representations of singular user interactions
* Use best judgement when creating step definitions, ensure readability of steps (don’t capture too many variables to the point that the regex step definition is unreadable)\
Same for scenario outlines, if too many variable data points then scenario is unreadable
* Step definitions are intended to delegate to methods and have finite expectations\
Steps should not test anything other than what they’re expected to test\
Probably should not have steps that have 10+ “expect”s
* common_steps/common anything should be suite-wide common, not just used by 2-3 features out of 10\
If you’re making updates to something in common, **make sure that your updates are truly common**. If they’re not, create a new step definition
* Use Given, When, Then, and Ands appropriately to ensure the gherkin is readable

## Action items
* Explore grouping helpers/etc by business functionality to improve folder structure\
potential CI iteration task
* Explore page_object_autoroute for navigation\
potential CI iteration task
* Gem up logging functionality
* Gem up Splunk logging functionality
* Gem up web service calls
* Library use, such as faker — does it allow for enough uniqueness? Do we want to use it?
* Gems in gemfile — do we want to include dev dependencies? Do we want to maintain versions in gemfile?\
	Could try using a hook or pre-start task to bundle update?
* Collapse PCAPI “exceptions” features into swagger validations (API feature organization similar to CIAM)