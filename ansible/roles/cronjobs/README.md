### CronJobs renerator

That role creates CronJobs on a target host.
Example:
```
cronjobs:
  - name: test job
    type: special_time
    time: daily
    job: "echo test"
  - name: test job2
    time: "0 22 * * 1-5"
    user: ubuntu
    job: "echo test2"

    # Delete Job
  - name: test job2
    state: absent
```