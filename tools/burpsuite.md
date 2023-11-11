#### Burp Suite

A tool to track all network and proxy traffic.

## You can use the FoxyProxy extension to intercept and modify requests.

# Proxy: Intercepting and Modifying Requests/Responses
Start Burp Suite and configure your browser to use Burp's proxy (typically on localhost and port 8080).
Use the Proxy tab to intercept and modify HTTP requests and responses.
Inspect and manipulate parameters, headers, or cookies before forwarding the request.

# Scanner: Automated Vulnerability Scanning
Navigate to the Target tab and add the target web application.
In the Scanner tab, initiate an automated scan to identify common vulnerabilities like SQL injection or XSS.
Review the scan results and prioritize fixing the identified issues.

# Spider: Automated Crawling and Mapping
In the Target tab, add the base URL of the web application.
In the Spider tab, initiate a crawl to automatically discover and map out the application's structure.
Review the results to understand the relationships between different pages.

# Repeater: Manual Request Testing
Use the Proxy tab to intercept a request of interest.
Right-click on the intercepted request and select "Send to Repeater."
In the Repeater tab, modify the request and resend it to observe the impact on the application.

# Sequencer: Analyzing Token Quality
Capture a token or session identifier from the application.
In the Sequencer tab, configure the analysis and start the sequencer.
Review the results to assess the randomness and quality of the captured tokens.

# Intruder: Automated Attack Testing
Use the Proxy tab to capture a request that includes a parameter you want to test.
Switch to the Intruder tab, load the captured request, and define positions for payload injection.
Configure payload sets and initiate the attack to test the target parameter for vulnerabilities.

# Decoder: Encoding and Decoding Data
In the Decoder tab, paste or type encoded data.
Select the appropriate decoding method (e.g., URL, Base64) and decode the data to reveal the original content.
Similarly, encode data using different methods.

# Comparer: Comparing Requests/Responses
In the Proxy tab, capture two similar requests or responses.
Right-click on one of the captured items and choose "Send to Comparer."
In the Comparer tab, review the differences between the two items.
