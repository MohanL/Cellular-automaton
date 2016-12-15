# Cellular-automaton

## Implementation Details.

In side the origin folder is the Cellular-automaton game in single thread mode, and in the executorversion folder, is the game implemented in executor, and the one is threadversion folder is simply implemented in threads.

## How to validate correctness

I ran the executorversion, the threadversion and the original version, generated their panel state in matrix and compared the graphs.

Comparing the executor.txt file under executorversion folder and thread.txt file under threadversion folder, these are the panel state in matrix after each repaint cycle. They are exactly the same and they are the same as the original game.

## Potential improvements
Using executorService is cool, but in this case, there are new tasks keeping adding into the servicepool, therefore, the simple shutdown doesn't workmore,
maybe it is my Implementation, I used cyclicbarrier to solve it. It can also be solved by CompletionService combined with future object to check if the certain patch of tasks are finished.

## Running speed analysis

##### Different strategies on improving the speed
The best result was achieved when i set the thread number equals to the number of core on the machine.
so in my testcode which is not included here:

```int cores = Runtime.getRuntime().availableProcessors();``

I tried to get the cores before I set up how many threads I need for this program,
and test out threadnumber = 1/2/3/4*cores and it improves the running speed significantly on different machines, the evidence shows that 3/4*cores doesn't improve much.


##### Executor VS threads VS no threads

Also the change of speed for the program in its own Implementation doesn't improve much after the threads number rises to 30.

1. Fewer threads will leave CPUs unutilized, too many will add overhead
2. Single threaded performance was the worst in any case.
3. Parallel streams are not stable.
