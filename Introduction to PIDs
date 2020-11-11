#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <sys/wait.h>
#include <unistd.h>

int main(int num, char *n[])
{
    int N = atoi(n[1]);
    if (num == 1)
    {
        printf("\nERROR: No Parameters is specified.\nUsage: ./filename <int parameter>\n");
        exit(1);
    }
    else if (num > 2)
    {
        printf("\nERROR: There are too many Parameters.\nUsage: ./filename <int parameter>\n");
        exit(1);
    }
    else if (N == 0)
    {
        printf("\nERROR: Invalid Parameter.\nUsage: ./filename <int parameter>\n");
    }
    else
    {
        pid_t ppid = getpid();
        for (int i = 0; i < N; i++)
        {
            for (int k = 0; k < 3; k++)
            {
                pid_t pid = fork();
                if (pid > 0)
                {
                    if (getpid() == ppid) //Is the Parent Process
                    {
                        printf("This is the main process, my PID is: %d\n", ppid);
                        sleep(2);
                    }
                }
                else
                {
                    if (getppid() == ppid) //Is the child process
                    {
                        printf("This is a child process, my PID is: %d, my parent PID is: %d\n", getpid(), getppid());
                        sleep(2);
                    }
                }
            }
        }
    }
}
