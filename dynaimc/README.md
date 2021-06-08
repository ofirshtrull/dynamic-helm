## Extra Objects

This chart can deploy extra Kubernetes objects (assuming the role used by Helm can manage them). For Astronomer Cloud and Enterprise, the role permissions can be found in the [Commander role](https://github.com/astronomer/astronomer/blob/master/charts/astronomer/templates/commander/commander-role.yaml).

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
