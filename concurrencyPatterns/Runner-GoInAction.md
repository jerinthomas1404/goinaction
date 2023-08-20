### Runner

> It shows how channels can be used to monitor the amount of time for a program is running and terminate the program if it runs too long.

##### Things worth to remember
- The *interrupt channel* is initialized as a buffered channel with buffer of 1. This gurantees at least one os.Signal value
received from the runtime. The runtime sends this value event in nonblocking way. If a goroutine isn't ready to receive this value, the value is thrown away. 
> It will recieve only one event, for instance in the case of repeatedly pressing ^C only one event will be captured.

- The *gotInterrupt* method shows a classic use of the select statement with a default case. The code attempts to receive on the interrupt channel. Normally that would block if there was nothing to receive, but we a default case which in turns attempt to receive on the interrupt channel into a nonblocking call. 
> If there is an interrupt to receive, then it's received and processed. If there's nothing to receive, the default case is then executed.
