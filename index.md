
# Accessing SimSpace and Exploring the Virtual Network

## Introduction

SimSpace is a service that is used for conducting simulations of cyber warfare and training cyber security students. This lab introduces SimSpace and gives instruction over a few of the various ways one can interface with virtual machines. Most of the lab is interacting with a Windows virtual machine and running network scans with basic parameters followed by analysis of the results. The lab then concludes with running a Kali Linux virtual machine and executing three of its installed cyber security applications.

## Opening SimSpcae and Accessing the Virtual Machine

I begin this lab by logging into SimSpace and familiarizing myself with its user interface. I read over the guide a few times in order to have a better understanding of the program. In this case, my only concern was the “events” pane. From there, I navigated under the “live action events panel” since this event is intended to be interactive. After selecting my course’s class range under the “virtual machines” tab, I was given a large list of all the virtual machines that were running in the network. After some scrolling, I found the virtual machines running windows, which are named with the convention “win-hunt-##,” were located nearer to the bottom of the list.

Before I began launching the Windows virtual machine, I noticed that the lab instructions did not specify a specific machine that was to be used. Therefore, I arbitrarily chose the machine win-hunt-10. Using the provided password, I logged into the machine and waited for it to take me to the desktop. Once everything had loaded up, I was then ready to open a PowerShell window and begin my scans with Nmap.

## Interfacing with the win-hunt-10 Virtual Machine and Running the First Nmap Scan

Through the start menu, I located PowerShell. According to Microsoft’s official website, PowerShell is a cross-platform task automation and configuration management framework that utilizes the command line and is built with the .NET Common Language Runtime in mind (PowerShell Overview). As such, this software is a suitable platform for running Nmap. Upon opening the command prompt, I type in the command “nmap” and hit enter. The console then returns a whole array of information that includes target specification, host discovery, scan techniques, port specification and scan order, service/version detection, script scan, OS detection, timing and performance, firewall/IDS evasion and spoofing, output, miscellaneous, and examples. A quick run-through of the information reveals that this is a command list, and all the entries are ways Nmap can be used and manipulated. For this lab, I am only focused on commands under host discovery, scan techniques, and output. With my commands laid out before me, I am now ready to begin the first scan.

I initiate the first scan by typing “nmap -v 172.16.3.0/24.” Based on the information given from the “nmap” command, this iteration of “nmap” initiates the scan while the “-v” command increases the verbosity level. That is, the verbosity level influences how much additional information is provided throughout the scan including side notes, the number of hosts and ports scanned, and whether each port is opened or closed (Command-line Flags). Lastly, based on the network map, the IP address at the end is concerned with the host for 236 IP addresses. Upon hitting enter, the scan begins.

Two things that are immediately apparent upon the conclusion of the scan is the length of time the scan took, and the amount of information it output. Based on the information at the end of the output, the scan took approximately three minutes and forty seconds. It appears to have swept through each of the IP addresses within the host subnet and given information about each one including its status and MAC address. As thorough and useful as that may be, I must suggest that this is not an efficient method for scanning data especially since the prompt froze and stuttered multiple times throughout the scan. I imagine that in a real-world setting, this period of inactivity would be a major cause of concern as information could potentially be outdated by the time the scan finishes. Moreover, the log is totally flooded with information that only clutters what the user is looking for. The other logs may be good to know, but they are not necessary and therefore only draw down the efficiency of scans. With only bearing this section of the lab in mind, I would think that running a scan with specific and concise parameters would be a far more suitable method for meeting the data analyst’s needs. Nevertheless, the information from the scan is not easily decipherable as there were vast amounts of logs that were spat out. In order to better understand the results of this scan, the directions of the lab suggest “piping” the output to a .txt file.

## Initiating the Second Scan and Analyzing the Output Text File

The second scan is initiated in a fashion similar to the first. The command for this scan was “nmap -v 172.16.3.0/24 > bicescan1.txt.” Like the first scan, the first half of this command will once again provide verbose information about every IP address it can ping within the host subnet. The second half, however, is what I assume “piping” to be. That is, using the prompt to automatically write the output of a command into an automatically generated .txt file. So, then, the output of the network scan will be written into a .txt file titled “bicescan1.txt.” Once again, I hit “enter” and commence the second scan. This time around, I noticed a large amount of information regarding “Nsock.” Security engineer Fotis Chantzis describes Nsock as a library of parallel sockets that acts as an abstraction layer and specializes in handling multiple sockets (sock_raw sic.). These are in place so that a more efficient means of generating input and output can be used.  In tandem with the piping command, the information about the scan is now stored in an easily accessible text file and I am now better able to analyze what, exactly, my machine just spat out at me.

With the second scan complete, the output has now been written to the text file. The lab suggests I still view this file within the PowerShell command prompt. Using the command “ls,” which tells the prompt to list the files within a given directory (MSQL Tips), I am able to see all the files under C:\Users\Administrator:

- <i>Figure 1</i>: The output the command prompt gives after typing the “ls” command. It displays all of the contents within the administrator directory in chronological order including the newly generated bicescan1.txt file which is found at the very bottom.

<p align="center">
  <img width="352" height="276" src="assets/fig1.png">
</p>

Now that I have located the directory in which my file is located, I can now use a command to view its contents.

With my target in sight, I type the command “cat bicescan1.txt.” The “cat” command is used to concatenate, or link, files together and print them as an output onto the command prompt (ShellHacks). After hitting “enter,” the output logs of the second scan are once again called forth. The final few entries in the scanning output explain that 256 IP addresses have been scanned in the 172.16.3.0/24 subnet and of those 256, 95 of the IP addresses are considered “up” or “running.” The figure below shows this snippet of the output:

- <i>Figure 2</i>: The final few lines of the scanning output. Points of interest include the number of IP addresses scanned and the number that are up. Also, and perhaps less significantly, this scan took approximately seven seconds longer.

<p align="center">
  <img width="610" height="54" src="assets/fig2.png">
</p>


## Header 2

> This is a blockquote following a header.
>
> When something is important enough, you do it even if the odds are not in your favor.

### Header 3

```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)

### Large image

![Branching](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
