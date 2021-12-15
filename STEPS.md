These are the steps I followed to complete the Chaincode Labs Residency Application. This may be excessively verbose but 
that is to assist in my learning. Much of this process was near the edge of my comfort and was a tremendous learning 
process.

This was my first time compiling bitcoin core from source on my own. I have installed many node software packages and 
have simply downloaded bitcoin core in the past. I decided to setup dual RasPi’s in case I had issues and set one up 
pruned and the other full node, secure copying a local version of the blockchain.

As I began playing with the tests on my headless pis, I was very out of my element as I rarely run python scripts from 
terminal. I was struggling with understanding the output and finding the logs/useful information. I then decided to 
compile another copy of bitcoin core what I had it currently running (with QT). I shut down that version and compiled a 
third copy (without QT) and made use of the existing database & config files.

This made a tremendous difference as I could now use PyCharm for viewing the code and running the tests. Initially I 
believed I was going to import classes/functions from the mining_basic.py and/or test_framework.py. This was beginning to 
feel beyond my ability as there is a lot of code I did not understand. I was worried I was not ready for this residency…

I then committed to reading through the code as many times as needed until I understood where the mining was happening. 
Upon doing so I realized what was occurring in run_test method in the ExampleTest class. I originally thought getblocks 
meant getting the database but the comments at line 170 made me realize they were actually being generated here. I knew 
there were 11 total blocks created so the for loop with range of 10 did not stand out until I realized one was created in 
IBD to get the test going.

I then ran a test after I modified the for loop to have a range of 15 and waitforblockheight() to 16 along with comments 
and a counter within the for loop. I ran with the —-nocleanup flag and my counter confirmed I had increased the block 
count. Looking through the test_framework.log and the node2 debug logs I confirmed that my changes worked.

I have included the example_test.py with the changes to generate 12 blocks and the test_framework logs and node logs to 
show this is true.
