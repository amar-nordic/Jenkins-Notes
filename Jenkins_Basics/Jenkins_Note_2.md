# Jenkinsfile

- Jenkins pipelines are written in Groovy
- A Jenkinsfile is a text file written in Groovy that defines the pipeline

# Jenkinsfile - Common Building Blocks (Declarative)
### pipeline { ... }: Top-level block.

1. agent – where our pipeline runs
    - examples:
        - agent any – any node
        - agent none – define per-stage agents only
        - agent { label 'windows' } – specific node label

2. options – pipeline-level settings
Pipeline-level behaviors (timeouts, retry, timestamps, durability hints)
3. stages { ... } and stage('Name'): Logical milestones we see in Blue Ocean/Classic UI
4. steps: The actual commands—sh, bat, powershell, checkout, archiveArtifacts, etc.
5. when - Conditional logic (branch, environment, expression)
6. parallel: Run multiple sub-stages concurrently
7. environment: Environment variables for the pipeline or a specific stage.
8. parameters: Inputs when triggering a build (branch names, toggles, versions).
9. triggers: Auto-run conditions (SCM polling, GitHub webhooks, cron)
10. post – notifications & cleanup
11. matrix: run the same pipeline steps across multiple combinations of parameters
like different Operating Systems, JDK versions or browsers in parallel

---

- In a Declarative Pipeline, each stage usually contains a steps { ... } block
- Inside steps, optionally we can have script { ... } block
- script { ... } inside steps is optional and used to run Scripted/Groovy logic
within a Declarative pipeline.
- script { ... } lets us momentarily drop into Scripted Pipeline (Groovy)
inside a Declarative pipeline.
