# assignment2-amanchi
# i am a full stack developer.
# Shiva Kumar Amanchi.
###### I like Agra in India very much.

Its also known for the Taj Mahal.
Taj Mahal is the symbol of **love** and Agra is also known for its **white marble** sculputures.

---
 Travel to Taj Mahal from maryville on Airbus
 1. drive from maryville to kansas city airport
 2. board flight to delhi
    1. kansas to chicago
    2. chicago to delhi
3. Arrived at delhi international airport
4. take a ride from delhi airport to tajmahal.

* Taj mahal
* symbol of love
* White marble

[AboutMe](https://github.com/shivaamanchi/assignment2-amanchi/blob/main/AboutMe.md)

--- 
| Food | Place | Price |
| ---| ---| ---: |
| Biryani | Hyderabad | 12$ |
| Gulab Jamun | Mumbai | 3$ |
| Samosa | Hyderabad | 8$ |
| Chicken Fry | Hyderabad | 18$ |

---

### Quotes written by socrates

> “The only true wisdom is in knowing you know nothing.”
> -*Socrates*
>
> “The unexamined life is not worth living.”
> -*Socrates*

---

> One of the most common data wrangling challenges involves extracting numeric data contained in character strings and converting them into the numeric representations required to make plots, compute summaries, or fit models in R. Also common is processing unorganized text into meaningful variable names or categorical variables. Many of the string processing challenges a data scientist faces are unique and often unexpected. It is therefore quite ambitious to write a comprehensive section on this topic.
>
> NextStep https://rafalab.github.io/dsbook/string-processing.html.

---
```
bool delim(char c) {
    return c == ' ';
}

bool is_op(char c) {
    return c == '+' || c == '-' || c == '*' || c == '/';
}

int priority (char op) {
    if (op == '+' || op == '-')
        return 1;
    if (op == '*' || op == '/')
        return 2;
    return -1;
}

void process_op(stack<int>& st, char op) {
    int r = st.top(); st.pop();
    int l = st.top(); st.pop();
    switch (op) {
        case '+': st.push(l + r); break;
        case '-': st.push(l - r); break;
        case '*': st.push(l * r); break;
        case '/': st.push(l / r); break;
    }
}

int evaluate(string& s) {
    stack<int> st;
    stack<char> op;
    for (int i = 0; i < (int)s.size(); i++) {
        if (delim(s[i]))
            continue;

        if (s[i] == '(') {
            op.push('(');
        } else if (s[i] == ')') {
            while (op.top() != '(') {
                process_op(st, op.top());
                op.pop();
            }
            op.pop();
        } else if (is_op(s[i])) {
            char cur_op = s[i];
            while (!op.empty() && priority(op.top()) >= priority(cur_op)) {
                process_op(st, op.top());
                op.pop();
            }
            op.push(cur_op);
        } else {
            int number = 0;
            while (i < (int)s.size() && isalnum(s[i]))
                number = number * 10 + s[i++] - '0';
            --i;
            st.push(number);
        }
    }

    while (!op.empty()) {
        process_op(st, op.top());
        op.pop();
    }
    return st.top();
}

```

to be continued <https://cp-algorithms.com/string/expression_parsing.html>