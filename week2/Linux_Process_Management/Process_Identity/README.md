# Task 02: Process Identity (PID and PPID)

## Objective

To understand process identity in Linux by retrieving and examining the Process ID (PID) and Parent Process ID (PPID) of a running process.

Every process in Linux has a unique Process ID (PID). The Parent Process ID (PPID) identifies the process that created the current process. Understanding PID and PPID is useful for process monitoring, system administration, and troubleshooting.

## 1. Creating the C Program

I created a C program using the `getpid()` and `getppid()` functions to retrieve its process identity.

### Source Code

<div align='center'>
<img src='/Linux_Process_Management/Process_Identity/Screen_shots/1.png' alt='source code'/>

**Figure :- Source code**
</div>

### Explanation

- `stdio.h` provides the `printf()` function.
- `unistd.h` provides the `getpid()`, `getppid()`, and `sleep()` functions.
- `pid_t` is a data type used to represent process IDs.
- `getpid()` returns the PID of the current process.
- `getppid()` returns the PID of the parent process.
- `sleep(20)` keeps the process alive for approximately 20 seconds so it can be inspected from another terminal.

## 2. Compiling the Program

I compiled the C source code using GCC.

```bash
gcc source_code.c -o dhiru
```
<div align='center'>
<img src='/Linux_Process_Management/Process_Identity/Screen_shots/2.png'>

**Figure :- Compiling for making execution**
</div>

This command creates an executable file named `dhiru`.

## 3. Running the Program in the Background

I executed the program in the background using `&`.

```bash
./dhiru &
```
<div align='center'>
<img src='/Linux_Process_Management/Process_Identity/Screen_shots/3.png'>

**Figure :-executation of file in the background**
</div>

The program prints its PID and PPID and then sleeps for 20 seconds. During this time, I can inspect the process using another terminal.

## 4. Identifying PID and PPID

The program displays its process identity.

Example output:

```text
My PID is: 75258
My Parent PID is: 69920
Sleeping for 20 seconds...
```

The values above are examples. The actual PID and PPID change each time the program runs.

### PID

The PID is the unique numerical identifier assigned to the running process by the Linux kernel.

### PPID

The PPID identifies the parent process that created the current process. When the program is launched from a terminal, its parent is usually the shell, although it may differ depending on how the program was launched.

## 5. Verifying the Process Using ps

I used the `ps` command to verify the process information.

```bash
ps -p 84838 -o pid,ppid,cmd
```

<div align='center'>
<img src='/Linux_Process_Management/Process_Identity/Screen_shots/4.png'>
</div>

### Command Explanation

- `ps` displays process information.
- `-p` selects a process using its PID.
- `-o` specifies the output columns.
- `pid` displays the Process ID.
- `ppid` displays the Parent Process ID.
- `cmd` displays the command used to start the process.

## 6. Results

The PID displayed by the C program matched the PID reported by the `ps` command.

The PPID displayed by the C program also matched the parent process ID shown by the operating system.

This confirms that the program successfully retrieved its process identity using `getpid()` and `getppid()`.

## Conclusion

In this practical, I learned how to retrieve the PID and PPID of a process using C programming and verify the information using Linux process-monitoring commands.

This knowledge is important for understanding process hierarchy, monitoring running applications, troubleshooting Linux systems, and analyzing process behavior during cybersecurity investigations.
