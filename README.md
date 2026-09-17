# Experiment 1(b): Program to Implement SJF (Shortest Job First) Scheduling

**Royce Niran George A**
**212223060231**

## Aim

To write and execute a C program to implement the Shortest Job First (SJF) CPU Scheduling algorithm and calculate the Waiting Time (WT) and Turnaround Time (TAT) for each process along with their average values.

## Algorithm: SJF (Shortest Job First) Scheduling

1. Start the program.

2. Read the number of processes `n`.

3. Read the Burst Time (BT) of each process and assign process IDs.

4. Sort the processes in ascending order of Burst Time.

5. Assign the Waiting Time of the first process as 0.

6. Calculate the Waiting Time for the remaining processes using:

   `WT[i] = WT[i-1] + BT[i-1]`

7. Calculate the Turnaround Time for each process using:

   `TAT[i] = WT[i] + BT[i]`

8. Display the Process ID, Burst Time, Waiting Time, and Turnaround Time for each process.

9. Calculate the Average Waiting Time and Average Turnaround Time.

10. Display the average values.

11. Stop the program.

## Procedure for Executing the C Program

* Open any C programming environment such as Code::Blocks.
* Create a new C source file.
* Type or paste the SJF scheduling program into the editor.
* Save the file with the `.c` extension.
* Compile the program and check for errors.
* Execute the program.
* Enter the number of processes and their Burst Times.
* Observe the execution order, Waiting Time, Turnaround Time, Average Waiting Time, and Average Turnaround Time displayed on the screen.

## Program

```c
#include <stdio.h>

int main() {
    int n, i, j;
    int bt[20], wt[20], tat[20], p[20], temp;
    float avg_wt = 0, avg_tat = 0;

    printf("Enter number of processes: ");
    scanf("%d", &n);

    for(i = 0; i < n; i++) {
        p[i] = i + 1;
        printf("Enter Burst Time for P%d: ", i + 1);
        scanf("%d", &bt[i]);
    }

    for(i = 0; i < n - 1; i++) {
        for(j = i + 1; j < n; j++) {
            if(bt[i] > bt[j]) {
                temp = bt[i];
                bt[i] = bt[j];
                bt[j] = temp;

                temp = p[i];
                p[i] = p[j];
                p[j] = temp;
            }
        }
    }

    wt[0] = 0;

    for(i = 1; i < n; i++) {
        wt[i] = wt[i - 1] + bt[i - 1];
    }

    for(i = 0; i < n; i++) {
        tat[i] = wt[i] + bt[i];
    }

    printf("\nProcess\tBT\tWT\tTAT\n");

    for(i = 0; i < n; i++) {
        printf("P%d\t%d\t%d\t%d\n",
               p[i], bt[i], wt[i], tat[i]);

        avg_wt += wt[i];
        avg_tat += tat[i];
    }

    printf("\nAverage Waiting Time = %.2f", avg_wt / n);
    printf("\nAverage Turnaround Time = %.2f\n", avg_tat / n);

    return 0;
}
```

## Output

<img width="745" height="397" alt="image" src="https://github.com/user-attachments/assets/27e86463-ab25-46a0-acb1-428fa397ad30" />

## Result

Thus, the C program to implement the Shortest Job First (SJF) CPU Scheduling algorithm was successfully executed. The Waiting Time, Turnaround Time, Average Waiting Time, and Average Turnaround Time were calculated and displayed successfully.
