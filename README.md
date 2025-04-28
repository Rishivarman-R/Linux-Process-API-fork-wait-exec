# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to print process ID and parent Process ID using Linux API system calls

```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main() {
    int pid = fork();

    if (pid == 0) { 
        printf("I am child, my PID is %d\n", getpid()); 
        printf("My parent PID is: %d\n", getppid()); 
        sleep(2);  // Keep child alive for verification
    } else { 
        printf("I am parent, my PID is %d\n", getpid()); 
        wait(NULL); 
    }

```














## OUTPUT

![438111096-d6e253ff-9ed4-4b69-85fb-7f6fba3d6a37](https://github.com/user-attachments/assets/a0e23aaa-e840-46f5-abf7-bf51ce1af9ed)

![438110023-c699b819-fba8-4cad-8b05-d0f719fa99cf](https://github.com/user-attachments/assets/a0a2a334-a913-4aed-a313-14eaabd7e6b3)



![438111616-bfa38d43-fb29-48a3-a5ed-4839c517c31b](https://github.com/user-attachments/assets/3e3bf8cd-5d1b-49b5-8e5b-4230bb837d4c)


## RESULT:
Thus the program to implement the creation of a process using fork() API is written and verified using C programming.






## C Program to create new process using Linux API system calls fork() and exit()


```
#include <stdlib.h>
#include <sys/wait.h>
#include <sys/types.h>
int main()
{       int status;
        printf("Running ps with execlp\n");
        execl("ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
printf("Running ps with execlp. Now with path specified\n");
        execl("/bin/ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
        exit(0);}

```










## OUTPUT
![438116389-dcda70cf-ef29-49c5-9a90-3746c936b86d](https://github.com/user-attachments/assets/dfb1d5b2-7d38-48bd-a402-db34f9fd6eb4)



![438116212-d42260aa-8a89-45a0-9ea8-1dd076eb9b4f](https://github.com/user-attachments/assets/f9ba9696-f6f2-4a4a-b303-f3bf545942d2)

## RESULT:
Thus the program to implement the creation of a process using exec() API is written and verified using C programming.



## C Program to execute Linux system commands using Linux API system calls exec() family
```
#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>

int main() {
    int status;
    
    printf("Running ps with execl\n");
    if (fork() == 0) {
        execl("ps", "ps", "-f", NULL);
        perror("execl failed");
        exit(1);
    }
    wait(&status);
    
    if (WIFEXITED(status)) {
        printf("Child exited with status: %d\n", WEXITSTATUS(status));
    } else {
        printf("Child did not exit successfully\n");
    }
    
    printf("Running ps with execlp (without full path)\n");
    if (fork() == 0) {
        execlp("ps", "ps", "-f", NULL);
        perror("execlp failed");
        exit(1);
    }
    wait(&status);
    
    if (WIFEXITED(status)) {
        printf("Child exited for execlp with status: %d\n", WEXITSTATUS(status));
    } else {
        printf("Child did not exit successfully\n");
    }
    
    printf("Done.\n");
    return 0;
}

```

























## OUTPUT

![438118446-ba3b10f6-009b-43df-85d5-2e21c83505b8](https://github.com/user-attachments/assets/defd7c59-f1c9-43ce-bd5a-009420f531c1)



![438118554-97fe7275-a2ed-4089-8df4-cbca4a1d4358](https://github.com/user-attachments/assets/08bd96ab-8c2a-4aa8-92d1-ae25bab581bf)



## RESULT:
Thus the program to implement the creation of a process using exit() , wait() API is written and verified using C programming.

## RESULT:
The programs are executed successfully.










# RESULT:
The programs are executed successfully.
