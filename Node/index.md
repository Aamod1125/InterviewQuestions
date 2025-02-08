## what are the file upload module
    1. Multer
    2. busboy
    3. formidable 

## process Module Events 
   * exit: Emitted when the process is about to exit.

   ```
    process.on('exit', (code) => {
     console.log(`Process exiting with code: ${code}`);
    });

   ```
   * uncaughtException: Emitted when an exception is not caught by any try...catch block.

   ```
   process.on('uncaughtException', (err) => {
        console.error('Uncaught exception:', err);
    });
   ```
   * warning: Emitted when Node.js issues a warning.
   
   ```pythan
     process.on('warning', (warning) => {
      console.warn(`Warning occurred: ${warning.name} - ${warning.message}`);
    });
   ```

## What are the event when user get sign-out 

```python
    1.  Using JWT for Token Expiration

    2.  Manual Session Destruction Tracking

    app.get('/logout', (req, res) => {
        req.session.destroy((err) => {
            if (err) {
            console.log('Error destroying session:', err);
            return res.status(500).send('Error logging out');
            }
            console.log('User signed out manually');
            res.send('You have been signed out');
        });
    });


    3. Inactivity Timeout

    const INACTIVITY_LIMIT = 5 * 60 * 1000; // 5 minutes
    app.use((req, res, next) => {
        if (req.session) {
            if (!req.session.lastAction) {
            req.session.lastAction = Date.now();
            }

            // If the user is inactive for more than the limit, destroy the session
            if (Date.now() - req.session.lastAction > INACTIVITY_LIMIT) {
            req.session.destroy(() => {
                console.log('User auto signed out due to inactivity');
                return res.status(401).send('Signed out due to inactivity');
            });
            } else {
            req.session.lastAction = Date.now(); // Reset the inactivity timer
            next();
            }
        } else {
            next();
        }
    });

    4. Graceful Shutdown Handling

    // Handle process termination signals like Ctrl+C or `kill`
    const shutdownHandler = () => {
    console.log('Shutting down the server gracefully...');
    server.close(() => {
        console.log('All requests finished, server closed.');
        process.exit(0);
    });

    // Force exit if server does not close within a certain time
    setTimeout(() => {
        console.error('Forcefully shutting down');
        process.exit(1);
    }, 10000); // 10 seconds timeout to force shutdown
    };

    // Listen for termination signals
    
    process.on('SIGTERM', shutdownHandler); // For `kill` signal
    process.on('SIGINT', shutdownHandler);  // For Ctrl+C (on terminal)

    **Description** : - 

    * SIGINT: Sent when the user presses Ctrl + C to interrupt a running process. Use it to handle manual shutdowns.

    * SIGTERM: Sent by external services or the system to request a graceful termination. Use it to manage clean shutdowns initiated by the system or orchestration platforms.
```

### What are the ccommon signal in node js
~Common Signals:~
* SIGINT: Sent when the user interrupts a process (e.g., pressing Ctrl + C in the terminal).
* SIGTERM: Sent by system commands like kill or from process managers (like Docker, Kubernetes) to request the termination of a process.
* SIGHUP: Originally sent when a terminal is disconnected (hangup). It is also used in modern systems to indicate that configuration   changes should be reloaded.
* SIGKILL: This signal immediately kills the process and cannot be caught or ignored.
* SIGUSR1 / SIGUSR2: User-defined signals that can be used for custom behavior in applications.

   
