# Linux-System-Administrator-Technical-Assessment

# These instructions are applicable for the linux command line

Task 1: Acquire the plain log-text from the downloaded access file
# The access log is gzipped, so this command allows you to access and read the access log
1. gzip -d usask_access_log

Task 2: Determine how many requests were received from mpngate1.ny.us.ibm.net
# This creates a separate file from the larger usask_access_log file to ease this process
1. grep -R "mpngate1.ny.us.ibm.net" usask_access_log > mpn.txt
# Since mpngate1.ny.us.ibm.net will only appear once per request and each request only takes up one line, the number of lines will equal the number of requests from mpngate1.ny.us.ibm.net
2. wc -l mpn.txt
# The total number of requests should be 1586

Task 3: determine how many unique servers have made requests
# Once again, create a new file to separate the usask.ca requests from the rest
1. grep -R "usask.ca" usask_access_log > usask.txt
# Create a separate file the contains all isntances of non-unique requests
2. uniq -D usask.txt > notuniq.txt
# Find the the total number of requests in usask.txt
3. wc -l usask.txt
# Find the number of non-unique requests from notuniq.txt
4. wc -l notuniq.txt
# From here, all that is needed is to subtract number of lines from notuniq.txt from the number of lines in usask.txt, leaving only the first instances of a server's request
# From doing this math, you should get around 664,152 unique servers
