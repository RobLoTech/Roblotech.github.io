# Course Objectives

In this course, we are going to focus on:

1. How tcpdump works
    
2. Using tcpdump to capture TCP packets
    
3. Analyze captured packets

# Project Structure

This hands on project is divided into following tasks:


- [Course Objectives](#course-objectives)
- [Project Structure](#project-structure)
	- [Task 1: Overview and Warm up](#task-1-overview-and-warm-up)
	- [Task 2: Create shell script and explore more options](#task-2-create-shell-script-and-explore-more-options)
		- [Building a website traffic monitor](#building-a-website-traffic-monitor)
			- [Create a Packet Capture Script](#create-a-packet-capture-script)
	- [Task 3: Create and Read dump files](#task-3-create-and-read-dump-files)
	- [Task 4: Create Sequence of dump files with size and time limits](#task-4-create-sequence-of-dump-files-with-size-and-time-limits)
				- [Example intervals](#example-intervals)
	- [Task 5: Advanced expressions for more Filtering Options](#task-5-advanced-expressions-for-more-filtering-options)

## Task 1: Overview and Warm up
[^Top](#project-structure)

To capture traffic, launch linux terminal and execute the command:

```
sudo tcpdump
```
To stop, use Ctrl + C

Use [man pages](https://www.tcpdump.org/manpages/tcpdump.1.html) for `tcpdump` to filter and use options for better functionality. 
In this example, we use the ==`-c`== option to specify the ***count*** or number of packets we want to capture. 
```
sudo tcpdump -c 10
```

If you want to view the line number, use the ==`-#`== sign at the end
```
sudo tcpdump -c 10 -#
```

To view packets in ASCI, use ==`-A`==.  
```
sudo tcpdump -c 10 -#A
```

To view packets in hexadecimal format, use ==`-XX`==. 
```
sudo tcpdump -c 10 -#XX
```

To view date in a human-readable format, use ==`-tttt`== option. 
```
sudo tcpdump -c 10 -tttt
```
![Alt text](<../assets/Pasted image 20230803204356.png>)

To get a list of all network interfaces on local workstation, use ==`-D`== option. 
```sh
sudo tcpdump -D
```

![Alt text](<../assets/Pasted image 20230803204554.png>)

With this, we can specify which interface we want to capture packets from with the ==**`-i`**== option.  
```sh
sudo tcpdump -i ens5 -c 10
```
![Alt text](<../assets/Pasted image 20230803205126.png>)

## Task 2: Create shell script and explore more options
[Top](#project-structure)
### Building a website traffic monitor

In this lesson, we start off by capturing traffic to and from a host, or website.  We can specify the host by either the url or IP address.  We use the URL name in this case, and only capture the first 10 packets:
```
sudo tcpdump -#tttt host skyroute66.com -c 10
```

If we want to capture packets from a specific post, we can specify that too:
```
sudo tcpdump -c 10 port 443
```

To capture packets from port 443 ***and*** from a specific host, we can use the ==`and`== option.  Keep in mind, by specifying `host`, you'll see **incoming** and **outgoing** traffic alike. 
```
sudo tcpdump -c 10 port 443 and host skyroute66.com
```

To specify either incoming or outgoing traffic, use either `dst` or `src`
	- `dst` = destination or outgoing traffic
	- `src` = source or incoming traffic
To include one or the other, use the ==`or`== operator. 

Now, we create a packet capture script. 
#### Create a Packet Capture Script

1.  Navigate to VS Code.  Select **'Open Folder'**
![[Pasted image 20230803211343.png]]
2. Select **Desktop** and press **OK**
![[Pasted image 20230803211409.png]]

3.  Create a new file and name it **'watchdog.sh'**
4.  Here's where we start our script. Add the following line of code
```
sudo tcpdump -#XXtttt host skyroute66.com -c 10
```

![[Pasted image 20230803211646.png]]
5.  In the terminal, you can see the files but its not yet an executable
6.  Make the file an executable
```
chmod +x watchdog.sh
./watchdog.sh
```

7.  Launch the file with `./watchdog.sh` 

![Alt text](<../assets/Pasted image 20230803211838.png>)

The output should look something like this:

![Alt text](<../assets/Pasted image 20230803212000.png>)

## Task 3: Create and Read dump files

Previous task, we generated and captured traffic going to a specific site.  Here, we'll learn how to read the contents of the packet capture. 

- First we must dump or save contents of the capture to a dump file.  We can do that with the flag `-w`, which means 'write'.  
```
sudo tcpdump -#XXtttt host skyroute66.com -c 10 -w captured.pcap
```
Here, we simply save the contents of the capture (`-w`) to a file called 'captured.pcap' in the standard format for packet captures. 
Further, we can see the newly generated file within the executed folder:

![Alt text](<../assets/Pasted image 20230806123444.png>)

If you try to open the file, you'll find that nothing is legible.  Instead, use the `-r` flag to read the contents:
```
sudo tcpdump -r captured.pcap
```

If you want to use a more user friendly application, **Wireshark** is the way to go. 

![Alt text](<../assets/Pasted image 20230806124211.png>)


## Task 4: Create Sequence of dump files with size and time limits

Sometimes, we want to capture packets for a certain amount of time.  We can do that with the `-G` flag, which specifies the time in seconds. 

Let's look at our scripts as an example:
```
sudo tcpdump -#XXtttt host skyroute66.com -w captured.pcap -G 15
```
If you noticed, we've removed the count (`-c`) and added `-G 15`, meaning our scripts will ==capture packets every 15 seconds==, wiping the ***captured.pcap*** file and re-writing to it for the specified interval. 
##### Example intervals
- 1 minute = `-G 60`
- 10 minutes = `-G 600`

Now, if we want to specify the ***file size***, we use the `-C` option.  This is represented in millions (1,000,000).  If we use `-C 1`, that means conduct a capture with file size of 1 million bytes. 
```
sudo tcpdump -#XXtttt -w captured.pcap -C 1
```
You'll see that we've removed the `host` portion so we can capture **ALL** traffic.  This will begin capturing packets and writing to the specified file.  However, it will continue to ==capture packets indefinitely==.  To terminate the packet capture, use `CTRL + c`. 

We can also combine options.  Here, we combine the `-C` option with the `-G` option.  The capture will finish whenever the ***first*** option is completed.  
```
sudo tcpdump -#XXtttt host skyroute66.com -w captured.pcap -C 1 -G 600
```
Based on this, the packet capture will terminate as soon as either one of the following is satisfied:
- Filesize reaches 1 million bytes (`-C 1`)
				or
- Time elapsed has been 10 minutes (`-G 600`)

## Task 5: Advanced expressions for more Filtering Options

This is a bit more advanced.  

```
sudo tcpdump -#XXtttt 'tcp[((tcp[12:1] & 0xf0) >> 2):4] = 0x47455420'
```
Let's try to explain the filter step-by-step:

- **`tcp[12:1]`**:      This part looks at the 13th byte of the TCP header, which contains the flags of the TCP packet (e.g., SYN, ACK, FIN).    
- **`& 0xf0`**:    This is a bitwise operation (AND) that isolates the first 4 bits of the flags, discarding the rest. It focuses on the first 4 bits of the flags, which are significant in identifying the type of packet.
- **`>> 2`**:    This shifts the 4 bits two places to the right. It effectively isolates the 4th bit, which corresponds to the ACK flag.
- **`tcp[((tcp[12:1] & 0xf0) >> 2):4]`**:    This part extracts the 4th bit (ACK flag) and the next 4 bytes of the TCP header. It helps us focus on a specific type of TCP packet.
- **`= 0x47455420`**:    This part checks if the extracted 4 bytes (32 bits) of the TCP header match the hexadecimal value "0x47455420". In ASCII, "0x47455420" represents the characters "GET ".

In simple terms, this filter is used to capture TCP packets that contain the "GET " request. In web communication, "GET " is a part of HTTP requests that a client sends to request a web page from a server.

There's many tcpdump expressions to look up from the web.  Here's some resources: