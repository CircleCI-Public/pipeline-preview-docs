## Available pipeline variables

For information on how these pipeline variables would be used in your configuration see [the overview of pipeline variables](pipeline_variables_overview.md).

Not all values will be available in all circumstances, for instance, the first push to a repository will not have a `pipeline.trigger.base_revision`.
If a value isn't available it will resolve to an empty string during config expansion, values documented as having a boolean type will resolve to `false`.


(THIS LIST IS UNDER DESIGN - FEEDBACK WELCOMED.)

First batch:
```
pipeline.id
pipeline.number
pipeline.project.name
pipeline.project.git_url
pipeline.project.type _or_ pipeline.project.source

pipeline.trigger.tag
pipeline.trigger.branch
pipeline.trigger.revision
pipeline.trigger.base_revision
```

Second batch:
```
pipeline.project_slug
pipeline.created_timestamp
pipeline.trigger.rerun_of
pipeline.trigger.actor
```

Other potential variables:
```
pipeline.pull_request.draft (boolean)
pipeline.pull_request.number
pipeline.pull_request.url
pipeline.pull_request.source_branch
pipeline.pull_request.source_repo
pipeline.pull_request.target_branch
pipeline.pull_request.target_repo
pipeline.pull_request.fork (boolean - useful, or should we prefer comparing source/target?)

pipeline.project.default_branch
pipeline.project.organization_name

(Speculative): pipeline.project.settings.*
```
