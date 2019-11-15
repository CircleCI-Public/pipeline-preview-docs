## Using pipeline variables in your configuration
Several useful variables are available to your configuration during pipeline intake. You can use these variables in any job step and/or use them to populate values in other parts of your configuration.

To reference a pipeline variable you use the syntax:

` << pipeline.variable_name >> `

For instance, if you wanted to know the ID of the running pipeline inside your job you could do something like:

```
version: 2.1
jobs:
  build:
    steps:
      - run: echo "The UUID of this pipeline is << pipeline.id >>"
    ...
```


And here's how you can get the `CIRCLE_COMPARE_URL` in v2.1:

```
version: 2.1
jobs:
  my-job:
    environment:
      CIRCLE_COMPARE_URL: << pipeline.project.git_url >>/compare/<< pipeline.git.base_revision >>..<<pipeline.git.revision>>
```

Next step: review [the list of available pipeline variables](pipeline_variables_reference.md)
