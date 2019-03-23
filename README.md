# Mordor Gates

The Mordor project provides pre-recorded security events generated by simulated adversarial techniques in the form of JavaScript Object Notation (JSON) files for easy consumption. The pre-recorded data is categorized by platforms, adversary groups, tactics and techniques defined by the Mitre [ATT&CK Framework](https://attack.mitre.org/wiki/Main_Page). The pre-recorded data represents not only specific known malicious events but additional context/events that occur around it. This is done on purpose so that you can test creative correlations across diverse data sources, enhancing your detection strategy and potentially reducing the number of false positives in your own environment.

The name **Mordor** comes from the awesome book/film series "[The Lord of the Rings](https://en.wikipedia.org/wiki/The_Lord_of_the_Rings_(film_series))", and it was a place where the evil forces of [Sauron](https://en.wikipedia.org/wiki/Sauron) lived. This repository is where data generated by known "malicious" adversarial activity lives, hence the name of the project.

![alt text](docs/source/_static/mordor-gate-main.jpg "Mordor-Gates")

# Goals

* Provide free portable malicious datasets to expedite the development of data analytics.
* Facilitate adversarial techniques simulation and output consumption.
* Allow security analysts to test their skills with real known bad data.
* Improve the testing of hunting use cases and data analytics in an easier and more affordable way.
* Enable data scientists to have semi-labeled data for initial research.
* Map threat hunter playbooks to their respective pre-recorded data for validation purposes.
* Contribute to the [ATT&CK framework](https://attack.mitre.org/wiki/Main_Page) **Data Sourcess** section of each technique and sub-technique.
* Ingest known bad data samples for training and capture the flag (CTF) events.
* Learn more about red team simulation exercises and technology such as Kafkacat, Kafka and Jupyter Notebooks.

# Why Mordor?

Think about an attack that you want to test in your lab environment.
Let's say we want to emulate an adversary using a non-domain-controller-account abusing the use of Active Directory replication services to optain the NTLM hash of user.
What do we do if we want to automate and expedite the emulation process? Usually the following might happen:

* Google for "DCSync" to look for the right script or red team simulation toolkit/project to execute the attack.
* Find that it can be done via several programming languages and several tools out there.
* Pick a "variant". In this case let's say I pick the Invoke-Mimikatz script from Powershell Empire.
* Test the adversarial technique.
* Document, at the endpoint level, that part of the main behavior is captured by specific Windows Security events (Event ID 4662).
* Consider other variants and I try another way to accomplish the main adversarial objective.
* Test another basic variant via another atomic red teaming toolkit, and get the same Windows Security events (Events ID 4662).
* Learn and test new ways to execute an attack (i.e .NET) and try to run DCSync again.
* Yup, I get the same Windows Security events (Events ID 4662) activity.

In my basic DCSync test I was using a user with replication permissions to initiate an ad replication operation.
The user name was ``Mmidge``.
I was getting one of the following events:

![alt text](docs/source/_static/event-log-dcsync-one.png "Event 4662")

## What is going on here?

Most of the time, depending on the detection goal, it does not matter what tool or programming language I use to emulate the adversarial technique or how many times I execute the attack, I still get the same event logic, pattern or relevant data.

From my basic example, I ask myself these question:

* What is my main goal?
* Do I want to primarily detect .NET behavior or the behavior of a non-domain-controller account abusing ad replication services?.

Do not get me wrong, the extra context of the execution method or the technique enabler is also valuable.
However, I believe that we can expedite the emulation of an adversarial technique by giving you the relevant data and pattern directly and go straight to the analysis phase of your threat detection strategy.

## Do I get only the events related to the adversarial techniques?

* You get the potential relevant events and the extra context produced by other security events that get created during the time window of the log collection.
* This is valuable if you want to explore other ways to enrich your data analytic and use extra context from events from different data sources.
* For example, you also get events of the command and control communication from the endpoint which can then be mapped to the specific adversarial technique you are analyzing.
* One specific example could be that if ``wmiprvse.exe`` as a parent creating processes is normal in your environment, ``wmiprvse.exe`` as a parent and creating a process that subsequently makes a network connection to an external entity, might not be. You get that extra context too with mordor data.

# Getting Started

* Mordor Environments
    * [Available Networks]()
* Mordor Categorization
    * [Small Datasets]()
    * Large Datasets
* Mordor Data Consumption
    * [Kafkacat Style]()
    * [Jupyter Notebooks Style]()

# Projects Using Mordor

* [ThreatHunter-Playbook](https://github.com/Cyb3rWard0g/ThreatHunter-Playbook)
* [HELK](https://github.com/Cyb3rWard0g/HELK)

# Authors

* Roberto Rodriguez [@Cyb3rWard0g](https://twitter.com/Cyb3rWard0g)
* Jose Luis Rodriguez [@Cyb3rPandaH](https://twitter.com/Cyb3rPandaH)

# Contributors

# Contributing

There are a few things that we would like to accomplish with this repo as shown in the To-Do list below. Share your pre-recorded data with us following our same setup (working on a standard setup..), and help others in the Cyber community to validate their detection use cases in a faster and easier way.  

# License: GPL-3.0

[ Mordor's GNU General Public License](https://github.com/Cyb3rWard0g/Mordor/blob/master/LICENSE)

# To-Do

- [ ] Dynamically generate mordor datasets readme files in restructuredtext
- [ ] Release environment scripts
- [ ] Add OSquery to endpoints for Linux/macOS
- [ ] Share Terraform & Packer config files to deploy the same environment in the cloud
- [ ] Add a Bro sensor
- [ ] Multiple custom network setup for contributions
- [ ] Prepare Large Dataset ;)
- [ ] Logo

More coming soon...