## Available pipeline variables

For information on how these pipeline variables would be used in your configuration see [the overview of pipline variables](pipeline_variables_overview.md).


(THIS LIST IS UNDER DESIGN - FEEDBACK WELCOMED.)

First batch:
```
pipeline.id
pipeline.number
pipeline.project_slug
pipeline.created_timestamp
```

Second batch:
```
pipeline.trigger.branch
pipeline.trigger.rerun_of
pipeline.trigger.tag
pipeline.trigger.actor
pipeline.trigger.end_sha
pipeline.trigger.begin_sha
```

Other potential variables:
```
pipeline.pull_request.draft (boolean)
pipeline.pull_request.source_branch
pipeline.pull_request.source_repo
pipeline.pull_request.target_branch
pipeline.pull_request.target_repo

pipeline.project.default_branch
pipeline.project.repo_name
pipeline.project.organization_name
pipeline.project.type (upstream VCS)

(Speculative): pipeline.project.settings.*
```