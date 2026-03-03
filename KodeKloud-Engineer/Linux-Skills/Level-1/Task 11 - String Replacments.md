# String Replacements
## Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> Within the Stratos DC, the backup server holds template XML files crucial for the Nautilus application. Before utilization, these files require valid data insertion. As part of routine maintenance, system admins at xFusionCorp Industries employ string and file manipulation commands.
>
> Your task is to substitute all occurrences of the string 'String' with 'Architecture' within the XML file located at /root/nautilus.xml on the backup server.

## Solution
**Important -** While there are more exact commands to make this as quick as possible, I will be as expressive as possible to show a step by step guide with optional verification steps.

1. Connect to target server, login details found in the 'company' wiki. (In a real world this would be in a vault,or you be accessing via your own assigned identity, not a shared identity.)

    ssh clint@stbkp01

2. backup the file you are going to be changing locally

    cp /root/nautilus.xml /root/nautilus.xml.bak

3. check file for current number of instances of 'String' and 'Architecture'

    sudo grep -o "String" /root/nautilus.xml | wc -l
    sudo grep -o "Architecture" /root/nautilus.xml | wc -l

5. (opt) manually check file

    sudo cat /root/nautilus.xml

4. change all instances of 'String' to 'Architecture' within the target file

    sudo sed -i 's/String/Architecture/g' /root/nautilus.xml

5. validate original string 'String' is gone and 'Architecture' has increased by expected amount

    sudo grep -o "String" /root/nautilus.xml | wc -l
    sudo grep -o "Architecture" /root/nautilus.xml | wc -l

6. submit

7. (outside of lab) I would have deleted the backup file once confirmed its working as expected for end users.

## My Comments
Its been awhile since I used Sed, had some issue id the command in my notes or with apropos, so did a google search. reviewed its man page and uses on Stackoverflow to build the correct command I needed.


