[![Work in Repl.it](https://classroom.github.com/assets/work-in-replit-14baed9a392b3a25080506f3b7b6d57f295ec2978f6f33ec97e36a161684cbe9.svg)](https://classroom.github.com/online_ide?assignment_repo_id=3989353&assignment_repo_type=AssignmentRepo)
# CMPS 2200  Recitation 01

**Names (Team Members):** Marisa Long, Ila Keshishian, Sebastian Rouse, Jake Johnston, Kelsey Peltz

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`.


## Setup
- Make sure you have a Github account.
- Login to Github.
- Login to repl.it, using "sign in with github"
- Click on the assignment link sent through canvas and accept the assignment. 
- Click on your personal github repository for the assignment (e.g., https://github.com/allan-tulane/recitation-01-your_username).
- Click on the "Work in Repl.it" button. This will launch an instance of `repl.it` initialized with the code from your repository.
- You'll work with a partner to complete this recitation. To do so, we'll break you into Zoom rooms. You will be able to code together in the same `repl.it` instance. You can choose whose repl.it instance you will share. This person will click the "Share" button in their repl.it instance and email the lab partner.

## Running and testing your code
- In the command-line window, run `./ipy` to launch an interactive IPython shell. This is an interactive shell to help run and debug your code. Any code you change in `main.py` will be reflected from this shell. So, you can modify a function in `main.py`, then test it here.
  + If it seems things don't refresh, try running `from main import *`
- You can exit the IPython prompt by either typing `exit` or pressing `ctrl-d`
- To run tests, from the command-line shell, you can run
  + `pytest main.py` will run all tests
  + `pytest main.py::test_one` will just run `test_one`
  + We recommend running one test at a time as you are debugging.

## Turning in your work

- Once complete, click on the "Version Control" icon in the left pane on repl.it.
- Enter a commit message in the "what did you change?" text box
- Click "commit and push." This will push your code to your github repository.
- Although you are working as a team, please have each team member submit the same code to their repository. One person can copy the code to their repl.it and submit it from there.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

- [ ] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`. 

- [ ] 2. Test that your function is correct by calling from the command-line `pytest main.py::test_binary_search`

- [ ] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [ ] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`? 

**TODO: your answer goes here**
The worst case for 'linear_search' would occur if the key did not exist in the list. In this case, 'linear_search' would check each value of the list in order and compare it to the key. It would do this until it reached the end of the list where it would return -1. The runtime would be O(n).
The worst case for 'binary_search' would also occur if the key did not exist in the list. In this case, 'binary_search' would check the middle value of the list, and then keep splitting the list and checking the middle value against the key until only one value was left. The runtime of this would be O(log_2 n).

- [ ] 5. Describe the best case input value of `key` for `linear_search`? for `binary_search`? 

**TODO: your answer goes here**
The best case for 'linear_search' would occur if the key was the first value checked by linear search. This means that the key would be the first value in the list becuase 'linear_search' checks the values against the key in order from first to last until they match. The runtime would be O(1).
The best case for 'binary_search' would also occur if the key was the first value check by 'binary_search'. This means that the key would be located at the middle value of the list located at (right+left)//2. 'binary_search' would compare the key with that value first, so the runtime would also be O(1).

- [ ] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [ ] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest main.py::test_compare_search`, which contains some simple checks.

- [ ] 8. Call `print_results(compare_search())` and paste the results here:

**TODO: add your timing results here**
|        n |   linear |   binary |
|----------|----------|----------|
|       10 |    0.002 |    0.003 |
|      100 |    0.009 |    0.009 |
|     1000 |    0.066 |    0.005 |
|    10000 |    1.057 |    0.010 |
|   100000 |    8.092 |    0.029 |
|  1000000 |  186.792 |    0.023 |
| 10000000 | 1817.750 |    0.049 |

- [ ] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

**TODO: your answer goes here**
The theoretical running times for linear search and the emperical results do appear to match each other becuase each time that n increases by a factor of 10, the runtime for linear search also increases by approximately a factor of 10. This means that it aligns with a runtime of O(n) for n elements. The theoretical running times for binary search and the emperical results also appear to align. Each time that n increases by a factor of 10, the binary search time increases by a factor of approximately log_2 10. This means that it alighs witha runtime of O(log_2 n) for n elements.

- [ ] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times. 
  + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search? **TODO: your answer goes here**
	The worst-case complexity would be k*O(n) = O(k*n) because you need to multiply the time for linear search by the number of times you use linear search.
  + For binary search? **TODO: your answer goes here**
	The worst-case complexity would be k*O(log_2 n) + Theta(n^2) = O(k*log_2 n + n^2) becuase you would need to add the runtime of binary search multiplied by k (the number of times you use binary search) and then add the sorting time.
  + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting? **TODO: your answer goes here**
	If k=1, then it would be more efficient to use linear search without sorting because it will take at worst O(n), which is still faster than sorting which takes Theta (n^2) and binary search (which takes O(log_2 n).  Otherwise, it's more efficient to first sort and use binary search than to use linear search when the worst-case runtime for binary search and sorting is less than the worst-case runtime for linear search. This can be written. k*log_2 n + n^2 < k*n. Then, this is simplified to log_2 n + n^2/k < n simplified to n^2/k < n - log_2 n simplified to k > (n^2)/(n-log_2 n). So for these values of k binary search and sort are more efficient.