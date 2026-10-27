# NOTES: Three Layers

Your name: Nicholas Candanoza

Fill each TODO. Write plain, short sentences. Do not delete the headings.

## Part 1. Predict, then find [S1]

Write your prediction before you open any code. Then search. In the last column, write each file the search finds and what that file does.

| Action | Search word | My prediction (file) | Files found and what each does |
|---|---|---|---|
| Prints "Not yet. Try again." | `Not yet` | `app.py` | `app.py` prints the message to the player. |
| Decides that the second miss shows the answer | `reveal` | `dataman/logic.py` | `dataman/logic.py` handles the reveal rule. `app.py` displays the revealed answer. `tests/test_logic.py` tests the behavior. |
| Saves one attempt | `save_attempt` | `dataman/store.py` | `dataman/store.py` defines attempt storage. `dataman/logic.py` calls the storage method. |
| Refuses the 11th problem | `SetFull` | `dataman/logic.py` | `dataman/logic.py` enforces the 10-problem limit. `exercise/bank.py` contains the exercise rule. `exercise/test_bank.py` tests the exercise. `tests/test_logic.py` tests the real library rule. `app.py` imports and handles `SetFull`. |

Search command: `grep -rn "SEARCH WORD" --include=*.py .`

## Part 2. What the program remembered [S1]

After the restart, what did the program remember? After the restart, what did the program remember? It remembered that I had already made one attempt, so the next practice prompt showed Try 2.

Which file made that possible? Which file made that possible? dataman_store.json saved the attempt information so it could be loaded after restarting.

## Part 3. The interface change [S1]

What did you change in `app.py`? I changed the message shown when the answer is incorrect.

Why did no test need to change? The change only affected the interface text, not the business rules or data storage.

## Part 4. The rule in the real library [S2]

The same 10-problem rule exists in the real library. Write the file and the function name. The file is `dataman/logic.py`, and the function is `add_problem()`."

## Part 5. The red test [S2]

With the rule removed from the library, what did the screen show? The program did not refuse the 11th problem because the limit rule was disabled.

With the rule removed, which test failed? `tests/test_logic.py::test_eleventh_problem_is_refused` failed because it expected `SetFull` to be raised, but it was not.

## Part 6. The data swap [S2]

A real database would replace which file? `dataman/store.py`

Which file holds the rules and does not change when the database changes? `dataman/logic.py`

## Reflection [S2]

Write 3 to 5 sentences. Pick one layer. Say what you changed in it. Say what stayed the same in the other two layers. I changed `app.py` to use JSON storage by default instead of memory storage. The business rules in `dataman/logic.py` stayed the same. The data layer in `dataman/store.py` continued to handle saving and loading data.

## Beta feedback (optional)

This bonus is a beta test. Which step took longer than its time? What confused you? Write it here. Your answer helps the next class.
The data swap and testing steps took longer than expected. I was confused about how to change the default storage from memory to JSON and how to temporarily disable the 10-problem rule to see which test failed. Step-by-step instructions helped me understand how the three layers work together.