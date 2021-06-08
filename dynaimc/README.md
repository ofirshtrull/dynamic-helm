## Extra Objects

This chart can deploy extra Kubernetes objects (assuming the role used by Helm can manage them).

```yaml
extraObjects:
  - apiVersion: batch/v1beta1
    kind: CronJob
    metadata:
      name: "{{ .Release.Name }}-somejob"
    spec:
      schedule: "*/10 * * * *"
      concurrencyPolicy: Forbid
      jobTemplate:
        spec:
          template:
            spec:
              containers:
              - name: myjob
                image: ubuntu
                command:
                - echo
                args:
                - hello
              restartPolicy: OnFailure
```
