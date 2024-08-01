<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>

<h1>🌐Network Sniffer</h1>

<p>Sniffers, also known as network analyzers, are tools used to monitor, capture, and analyze data packets transmitted over a network in real-time. When data travels over the internet, it is broken into small packets that pass through various network nodes. Sniffers intercept and analyze these packets as they traverse the network.</p>

<ul>
  <li>Analyze and improve network performance.</li>
  <li>Monitor employee activity on a corporate network.</li>
  <li>Detect and prevent cyber attacks.</li>
  <li>Monitor data packets for management and troubleshooting purposes.</li>
</ul>

<h2>🦈Wireshark</h2>
<div align="center"><img src="https://static-00.iconduck.com/assets.00/wireshark-alt-icon-2048x2048-4ex8a9zk.png" width="250px" alt="Wireshark Icon"></div>

<br>

<strong>Wireshark</strong> is a free and open-source tool for network traffic analysis. It allows capturing and examining data in transit, breaking down the packets to see their detailed content. This is especially useful for network troubleshooting and security.

<p>To start using Wireshark, you can <a href="https://www.wireshark.org/download.html">download it here</a></p>

<h2>🔎HTTP Packet Analysis and Capture with Wireshark</h2>

Once Wireshark is downloaded into our work environment, we can open it to get familiar with the basic elements needed to complete the practice. We can start the program from the terminal with the command <code>wireshark</code> or by double-clicking the icon from the graphical interface. Upon opening it, we will see the main window of the program with a list of available network interfaces.

<dl>
    <dt>Network interface.</dt>
    <dd><em>It is a component that allows a device to connect to a network either through cables, Wi-Fi, or virtually.</em></dd>
</dl>

In our case, we are using a virtual machine (<em>VirtualBox</em>), and the network interface showing signal is <strong>eth0</strong>. The signal will vary depending on the network traffic occurring at that moment.

<img src="https://github.com/antonimodev/network-sniffing/blob/main/Wireshark%20-%20English%20Screenshots%20Github/0%20START%20WIRESHARK.png?raw=true" alt="Start Wireshark">

Once we select the network interface we want to monitor, we will access the main panel, where we can observe various interface elements. It is essential to understand some basic concepts before diving into more details. In this context, it is important to know: What are network packets?

<dl>
    <dt>Network packets</dt>
    <dd><em>They are units of data sent across a network. Each packet contains information about its origin, destination, and other instructions to ensure the information is delivered correctly.</em></dd>
</dl>

Next, you will find some basic functions in Wireshark:
<ul>
    <li><strong>Start packet capture:</strong> Begins capturing data traffic on the selected network interface. This allows observing and analyzing packets in real-time.</li>
    <li><strong>Stop packet capture:</strong> Stops data capture. This is useful when enough information has been collected or you want to analyze already captured data.</li>
    <li><strong>Restart packet capture:</strong> Stops the current capture and starts a new capture session. It is useful for starting to capture data from a clean point, without previous data.</li>
</ul>

<img src="https://github.com/antonimodev/network-sniffing/blob/main/Wireshark%20-%20English%20Screenshots%20Github/1%20INIT%20ICONS.png?raw=true" alt="Wireshark Menu">

In addition to the basic buttons, Wireshark allows filtering packets according to various criteria in the search filter bar. You can use filters for protocols, IP addresses, ports, MAC addresses, among others, depending on what you are looking for.

<img src="https://github.com/antonimodev/network-sniffing/blob/main/Wireshark%20-%20English%20Screenshots%20Github/2%20SEARCH%20FILTER.png?raw=true" alt="Filter">

Once familiar with the basic interface, we will press the button to start packet capture. Next, we will see the capture window, where Wireshark will start showing network packets in real-time, organized into three different panels:

<ul>
    <li><strong>Central Panel:</strong> Shows the list of packets captured in real-time. Here you can see a summary of each packet, including information such as packet number, capture time, source and destination IP address, and the protocol used.</li>
    <li><strong>Bottom Left Panel:</strong> Provides a detailed breakdown of the packet selected in the central panel. It shows packet data broken down into different levels, such as the network layer, transport layer, and application layer.</li>
    <li><strong>Bottom Right Panel:</strong> Displays the raw content of the packet selected in hexadecimal and ASCII format. Here you can examine the exact data that make up the packet.</li>
</ul>

This panel organization allows you to analyze each captured packet in detail and better understand the information flowing through the network.

<img src="https://github.com/antonimodev/network-sniffing/blob/main/Wireshark%20-%20English%20Screenshots%20Github/3%20CAPTURED%20PACKETS.png?raw=true" alt="Packet info">

It may appear differently to you, showing packets of different colors. These colors have a meaning that helps us classify each packet according to its parameters. To see what each packet corresponds to and familiarize ourselves visually, we can go to the section: <pre>View > Coloring Rules</pre>

<img src="https://github.com/antonimodev/network-sniffing/blob/main/Wireshark%20-%20English%20Screenshots%20Github/4%20VIEW-COLORING%20RULES.png?raw=true" alt="View Coloring rules">

In this section, you can see how the nature of the packets is classified according to their color. Although for this practice we will not delve too much into the coloring rules, it is useful to know them to maintain a certain level of organization in packet analysis.

<img src="https://github.com/antonimodev/network-sniffing/blob/main/Wireshark%20-%20English%20Screenshots%20Github/5%20COLORING%20RULES.png?raw=true" alt="Coloring rules">

For the current project, we are going to explore the security of HTTP network protocols. We will navigate to a web page that uses the "http" protocol and offers a login form. We will enter random credentials to observe how the data is transmitted. Nowadays, most websites use the HTTPS protocol, which encrypts the packets and makes it difficult to access their content.

<dl>
    <dt>Network protocol</dt>
    <dd>A set of rules and standards that define how devices should communicate on a network.</dd>
    <dt>HTTP Protocol</dt>
    <dd><em>Hypertext Transfer Protocol, used for transmitting unencrypted data between the browser and the web server. Data is sent in plain text, making it vulnerable to interception and analysis.</em></dd>
    <dt>HTTPS Protocol</dt>
    <dd><em>Hypertext Transfer Protocol Secure, which uses SSL/TLS encryption to protect data during transmission. It ensures that communication between the browser and the web server is encrypted and more secure against attacks.</em></dd>
</dl>

In less technical words, we could say that an HTTP protocol dictates the rules that data packets must follow to be transmitted efficiently. The main difference with HTTPS is that HTTPS adds encryption to that data, ensuring that communication is much more secure and difficult to intercept.

<img src="https://github.com/antonimodev/network-sniffing/blob/main/Wireshark%20-%20English%20Screenshots%20Github/6%20LOGIN%20PAGE.png?raw=true" alt="login page">

Once we have identified the network protocols we are going to use, we can filter the packets by HTTP in the Wireshark search bar. This will allow us to focus solely on the packets containing information related to the login process on the HTTP domain.

<img src="https://github.com/antonimodev/network-sniffing/blob/main/Wireshark%20-%20English%20Screenshots%20Github/7%20HTTP%20PROTOCOL%20FILTERED.png?raw=true" alt="HTTP Protocol Filtered">

Once the packet containing the login is located, we should do the following: <pre>Right click > Follow > HTTP Stream</pre>
This action will allow us to see all the information for a specific HTTP session, facilitating the identification of problems and the review of data.

<img src="https://github.com/antonimodev/network-sniffing/blob/main/Wireshark%20-%20English%20Screenshots%20Github/8%20FOLLOWING%20HTTP%20STREAM.png?raw=true" alt="HTTP STREAM">

A window will open with all the information of the HTTP session. Here, we can observe the client's (ours) and the server's responses, differentiated by colors:

- Client: Red 🔴
- Server: Blue 🔵

Eureka! We have captured the credentials, in this case, the username is <strong><em>antonimodev</em></strong> and the password is <strong><em>github42</em></strong>.

<img src="https://github.com/antonimodev/network-sniffing/blob/main/Wireshark%20-%20English%20Screenshots%20Github/9%20EUREKA!.png?raw=true" alt="Credentials">

<h2>📖Conclusion</h2>
<p>In this practice with Wireshark, I learned how to use this tool to capture and analyze network traffic, with a specific focus on the HTTP protocol. I also explored different types of protocols and further strengthened my understanding of network security. These steps allowed me to:</p>

- <strong>Get familiar with Wireshark</strong>: I started the program, selected the appropriate network interface, and explored the basic interface, understanding its organization into panels for data visualization.
- <strong>Apply Search Filters</strong>: I learned how to use the filter bar to focus on specific HTTP packets, which facilitates the analysis of relevant data and improves the efficiency of information capture.
- <strong>Analyze HTTP Packets</strong>: By following a specific HTTP session, I saw how data is transmitted between the client and the server, identifying server and client responses through colors and filters.
- <strong>Understand Data Transmission Security</strong>: I explored the difference between HTTP and HTTPS protocols, understanding how HTTPS encryption protects communication from potential interceptions and attacks.
- <strong>Capture and Analyze Sensitive Data</strong>: Finally, I observed how credentials are transmitted in plain text over the HTTP protocol, highlighting the importance of using HTTPS to protect sensitive information on the web.

In summary, this practice gave me a clearer view of how network traffic works and why it is crucial to maintain security in communications.

</body>
</html>
