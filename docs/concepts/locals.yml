locals:
  full-build:
    type: boolean
    condition:
      eq: [<< pipeline.trigger.branch >>, "master"]


workflows:
  foo:
    when: << locals.full-build >>



