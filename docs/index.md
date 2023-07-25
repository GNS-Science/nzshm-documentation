{%
    include-markdown "../README.md"
%}

# Test Mermaid

```mermaid
graph TD
A[Client] --> B[Load Balancer]
B --> C[Server01]
B --> D[Server02]
E[Extra blob] -.- D
```