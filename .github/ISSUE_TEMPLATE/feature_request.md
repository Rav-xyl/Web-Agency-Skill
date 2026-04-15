name: 🚀 Feature Request
about: Suggest an idea for a new reference or command.
title: "[FEAT] "
labels: enhancement
assignees: ''

body:
  - type: textarea
    id: feature-description
    attributes:
      label: Description of Feature
      description: What is the new capability you'd like to add?
      placeholder: e.g. Add a reference module for high-converting landing page copy.
    validations:
      required: true
  - type: textarea
    id: why
    attributes:
      label: Why is this needed?
      description: Explain the architectural or business value.
  - type: textarea
    id: examples
    attributes:
      label: Technical Examples (Optional)
      description: Any agnostic patterns or code snippets to share?
      render: markdown
