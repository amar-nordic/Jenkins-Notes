# Jenkinsfile - Common Building Blocks (Declarative)

1. agent – where our pipeline runs
    - examples:
        - agent any – any node
        - agent none – define per-stage agents only
        - agent { label 'windows' } – specific node label

2. options – pipeline-level settings
3. stages & steps
