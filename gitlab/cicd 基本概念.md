# cicd 基本概念

```mermaid

graph LR
    
    A[cicd] --> B[GitLab Runner]
    A --> C[.gitlab-ci.yml]
    C --> D[pipeline]
    C --> E[stages]
    C --> F[job]
```