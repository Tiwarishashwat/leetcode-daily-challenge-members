```java
class Solution {

    public List<String> braceExpansionII(String expression) {
        Deque<Character> operator = new ArrayDeque<Character>();
        Stack<Set<String>> stack = new Stack<Set<String>>();

        for (int i = 0; i < expression.length(); i++) {
            // check star precedence
            if (expression.charAt(i) == ',') {
                while (!operator.isEmpty() && operator.peek() == '*') {
                    evaluate(operator, stack);
                }
                operator.push('+');
            } else if (expression.charAt(i) == '{') {
                // add star if needed, then push { into the operator 
                if (
                    i > 0 &&
                    (expression.charAt(i - 1) == '}' ||
                        Character.isLetter(expression.charAt(i - 1)))
                ) {
                    operator.push('*');
                }
                operator.push('{');
            } else if (expression.charAt(i) == '}') {
                // pop till we find '{'
                while (!operator.isEmpty() && operator.peek() != '{') {
                    evaluate(operator, stack);
                }
                operator.pop();
            } else {
                // add star if needed, then push word into stack
                if (
                    i > 0 &&
                    (expression.charAt(i - 1) == '}' ||
                        Character.isLetter(expression.charAt(i - 1)))
                ) {
                    operator.push('*');
                }
                Set<String> set = new TreeSet<>();
                set.add(String.valueOf(expression.charAt(i)));
                stack.add(set);
            }
        }

        while (!operator.isEmpty()) {
            evaluate(operator, stack);
        }
        return new ArrayList<String>(stack.peek());
    }

    // Pop the operator at the top of the stack and perform the calculation
    private void evaluate(Deque<Character> operator, Stack<Set<String>> stack) {
        if(stack.size()<2){
            return;
        }
        Set<String> right = stack.pop();
        Set<String> left = stack.pop();

        if (operator.peek() == '+') {
            // UNION
            left.addAll(right);

        } else {
            // CONCATENATION
            Set<String> result = new TreeSet<>();
            for (String l : left) {
                for (String r : right) {
                    result.add(l + r);
                }
            }
            left = result;
        }
        operator.pop();
        stack.push(left);
    }
}
```


```cpp
class Solution {
public:

    vector<string> braceExpansionII(string expression) {
        stack<char> op;
        stack<set<string>> st;

        for (int i = 0; i < expression.length(); i++) {

            // check * precedence
            if (expression[i] == ',') {

                while (!op.empty() && op.top() == '*') {
                    evaluate(op, st);
                }

                op.push('+');
            }

            else if (expression[i] == '{') {

                // add * if needed, then push { into operator
                if (i > 0 &&
                    (expression[i - 1] == '}' ||
                     isalpha(expression[i - 1]))) {

                    op.push('*');
                }

                op.push('{');
            }

            else if (expression[i] == '}') {

                // pop till we find {
                while (!op.empty() && op.top() != '{') {
                    evaluate(op, st);
                }

                op.pop();
            }

            else {

                // add * if needed, then push word into stack
                if (i > 0 &&
                    (expression[i - 1] == '}' ||
                     isalpha(expression[i - 1]))) {

                    op.push('*');
                }

                set<string> s;
                s.insert(string(1, expression[i]));

                st.push(s);
            }
        }

        while (!op.empty()) {
            evaluate(op, st);
        }

        vector<string> result(
            st.top().begin(),
            st.top().end()
        );

        return result;
    }


private:

    void evaluate(stack<char>& op, stack<set<string>>& st) {

        if (st.size() < 2) {
            return;
        }

        set<string> right = st.top();
        st.pop();

        set<string> left = st.top();
        st.pop();

        if (op.top() == '+') {

            // UNION
            left.insert(right.begin(), right.end());

        } else {

            // CONCATENATION
            set<string> result;

            for (string l : left) {
                for (string r : right) {
                    result.insert(l + r);
                }
            }

            left = result;
        }

        op.pop();
        st.push(left);
    }
};
```

```python
class Solution:

    def braceExpansionII(self, expression: str) -> list[str]:

        operator = []
        stack = []

        for i in range(len(expression)):

            # check * precedence
            if expression[i] == ',':

                while operator and operator[-1] == '*':
                    self.evaluate(operator, stack)

                operator.append('+')

            elif expression[i] == '{':

                # add * if needed, then push { into operator
                if i > 0 and (
                    expression[i - 1] == '}' or
                    expression[i - 1].isalpha()
                ):
                    operator.append('*')

                operator.append('{')

            elif expression[i] == '}':

                # pop till we find {
                while operator and operator[-1] != '{':
                    self.evaluate(operator, stack)

                operator.pop()

            else:

                # add * if needed, then push word into stack
                if i > 0 and (
                    expression[i - 1] == '}' or
                    expression[i - 1].isalpha()
                ):
                    operator.append('*')

                s = set()
                s.add(expression[i])

                stack.append(s)

        while operator:
            self.evaluate(operator, stack)

        return sorted(stack[-1])


    def evaluate(self, operator, stack):

        if len(stack) < 2:
            return

        right = stack.pop()
        left = stack.pop()

        if operator[-1] == '+':

            # UNION
            left.update(right)

        else:

            # CONCATENATION
            result = set()

            for l in left:
                for r in right:
                    result.add(l + r)

            left = result

        operator.pop()
        stack.append(left)
```


