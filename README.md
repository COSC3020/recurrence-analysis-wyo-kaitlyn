[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-718a45dd9cf7e7f842a935f5ebbe5719a5e09af4491e668f4dbf3b35d5cca122.svg)](https://classroom.github.com/online_ide?assignment_repo_id=12109379&assignment_repo_type=AssignmentRepo)
# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)
        return;
    else {
        mystery(n / 3);
        var count = 0;
        mystery(n / 3);
        for(var i = 0; i < n*n; i++) {
            for(var j = 0; j < n; j++) {
                for(var k = 0; k < n*n; k++) {
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);
    }
}
```

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

$T(n) = 1 if n \leq 1$

$T(n) = 3T(n/3) + n^5 if n > 1$

Next, substitute iterations to find a pattern.

$T(n) = 3T(n/3) + n^5$

= $3(3T(n/3/3) + (n/3)^5) + n^5 $

= $9T(n/9) + 3n^5/3^5) + n^5 $

.

.

.

= $3^iT(n/3^i) + \sum\limits_{j=0}^{i} 3^j/{3^j}^5 + n^5$

let $i = log_3n$ for the base case

= $3^{log_3n}T(n/3^{log_3n}) + \sum\limits_{j=0}^{log_3n-1} 3^j/{3^j}^5 + n^5$

$3^{log_3n}$ and $3^j/{3^j}^5$ are constants, so it can be reduced to

= $nT(1) + n^5\sum\limits_{j=0}^{log_3n-1} 3^j/{3^j}^5$

and then 

= $\in \Theta(n^5log_3n)$



