tags: #exploiting

# RE Daemons

links: [[911 ED TOC - Remote Exploit|ED TOC - Remote Exploit]] - [[themes/000 Index|Index]]

---

## How Daemons Work

Daemons are background processes that manage services on a server, crucial for remote exploits. They handle client connections continuously and ensure services are available without interruption. Understanding their operation is key to effectively targeting them in remote exploits.

### Daemon Characteristics

- **Run in Background**: Daemons operate continuously, without direct user interaction.
- **Listen on Ports**: They listen on specific network ports for incoming client connections.
- **Forking and Multi-threading**: To handle multiple clients simultaneously, daemons often use forking (creating child processes) or multi-threading.

### Forking Daemons

**Process Creation**: When a client connects, the daemon forks a new process to handle the connection, allowing the parent process to keep listening for new connections.

**Parent Process**: The main server process that waits for connections and forks child processes.

  ```c
  int newServerSocket;
  listen(serverSocket, 5);
  while (1) { 
      newServerSocket = accept(serverSocket, &cli_addr, &clilen); 
      pid = fork(); 
      if (pid == 0) {    
          close(serverSocket); 
          doprocessing(newServerSocket); 
          exit(0); 
      } else { 
          close(newServerSocket); 
      }
  }
  ```
  
  **Child Process**: The forked process that handles client interactions and performs the necessary processing.

  ```c
  void doprocessing (int clientSocket) { 
      char buffer[1024];
      int n;
      printf("Client connected\n"); 
      n = read(clientSocket, buffer, 1024); 
      handleData(buffer); 
  }
  ```

**Advantages of Forking Daemons**

- **Isolation**: Each child process operates independently. If one crashes, it doesn’t affect others.
- **Resource Management**: Child processes inherit resources from the parent, allowing efficient resource use.

### Multi-threading Daemons

- **Threads vs. Processes**: Threads share the same memory space within a process, enabling faster communication than between separate processes.
- **Efficiency**: Threads are lighter and faster to create, making them suitable for handling many simultaneous connections.

## Why Understanding Daemons Matters for Remote Exploits

1. **Entry Points**: Daemons listening on specific ports are potential targets for exploits.
2. **Payload Delivery**: Exploits often involve sending crafted packets to daemons, triggering vulnerabilities in their request handling.
3. **Persistence**: Exploiting a daemon provides persistent access to a server, as daemons typically restart if they crash.
4. **Forking Behavior**: Knowing how daemons fork helps in designing exploits that target child processes, ensuring multiple attempts without affecting the parent process.

**Common Exploits Targeting Daemons**

1. **Buffer Overflow**: Sending oversized input to a daemon can overflow its buffer, allowing arbitrary code execution.
2. **Code Injection**: Malicious code can be injected into the daemon’s process memory, exploiting vulnerabilities in input handling.
3. **Privilege Escalation**: Exploiting a daemon running with elevated privileges can provide higher access levels on the server.

![[remote-exploit_daemon.png]]

---
links: [[911 ED TOC - Remote Exploit|ED TOC - Remote Exploit]] - [[themes/000 Index|Index]]
