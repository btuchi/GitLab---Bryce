# Quiz questions

This is only a "quiz" in the loosest sense that it's asking questions whose
answers will be part of your grade. Please use *any resources you want*, as
long as you list those resources (e.g. peers, websites, etc.)

## Navigating logs

1. What is the SHA for the last commit made by Prof. Xanda on the branch
xanda_0000_movie_processing?
(For this and future questions, the first 5 characters is plenty - neither
Git nor I need the whole SHA.)

9b257

2. What is the SHA for the last commit associated with line 9 of this file?

b2ed3

3. What did line 12 of this file say in commit d1d83?

it says "2. I should really finish writing this."

4. What changed between commit e474c and 82045?

"gross_sort = lambda x : x["Gross"]" was changed to "gross_sort = lambda x : 
int(x["Gross"])";

and "top_five = rows[:-5:-1]" was changed to top_five = 
rows[:-6:-1]


## Predicting merges

Assume at the start of each of these three questions that your
branch for switching to a top-10 list was called `top_ten`
and your branch generalizing to any number of movies was called `top_N`.
Predict the behavior of these three possible operations - you don't
have to provide a full `diff` but you should describe at a high level
what changes would happen.

These questions are supposed to be separate paths, not cumulative;
for example, you should *not* assume that the operations of 5 were run
before 6. When testing outcomes later in the lab, you should make sure to
revert back to the state of the branch before you started these questions.

5. What do you think would happen if you ran the following commands?
What branches would change, and how?
```
git checkout test
git merge top_N
```
Since we are on the test branch, so the only branch affected is test. This command will merge the change made in branch top_N into branch test. The process_movie_data.py in test branch will be updated to be the same as the process_movie_data.py in top_N branch. They will both have the same find_top_n function.

6. What do you think would happen if you ran the following commands?
What branches would change, and how?
```
git checkout top_ten
git merge test
```
It will only affect the top_ten branch. The changes made in test branch will be merged into test branch. The file name for quiz.md will be changed to answers.md.

7. What do you think would happen if you ran the following commands?
What branches would change, and how?
```
git checkout test
git rebase top_ten
git rebase top_N
```
I think "git rebase top_ten" rebases the 'test' branch onto the 'top_ten' branch. It would apply the changes from the top_ten branch on top of the test branch. 'git rebase top_N' rebase the test branch onto the top_N branch. It would try to apply the changes from the top_N branch on top of the test branch.

Therefore, it would effectively update the test branch to include the changes from top_ten, and it will also try to further update the test branch to include the changes from top_N. The merge conflict happened because it does not know which update does 'test' branch want (from top_N or top_ten). 