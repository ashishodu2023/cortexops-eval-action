# Changelog

All notable changes to the CortexOps Eval Gate action. The `v1` tag always points at the latest 1.x release.

## v1.0.0 - 2026-10-10

First standalone release, published from `actions/eval-gate` in
[ashishodu2023/cortexops](https://github.com/ashishodu2023/cortexops) (introduced there in
[#52](https://github.com/ashishodu2023/cortexops/pull/52)).

- Runs `cortexops eval run` against a golden dataset and agent (`dataset`, `agent`, `working-directory`,
  `install`), or a custom `command`.
- Gates on one or more `fail-on` conditions over `task_completion`, `tool_accuracy`, and `pass_rate`
  (default `pass_rate < 1.0`).
- Writes the report to the job summary and keeps one sticky PR comment per `comment-tag` up to date. Fork
  PRs with a read-only token skip the comment with a warning.
- Fails the job only after the summary and comment are written; `fail-job: false` reports without failing.
- Optional LLM-as-judge scoring (`judge`, `openai-api-key`) and upload to CortexOps (`api-key`, `api-url`).
- Outputs: `passed`, `exit-code`, `task-completion`, `pass-rate`, `tool-accuracy`, `mean-score`, `failed`,
  `summary-path`, `report-path`, `junit-path`, `comment-url`.
- Installs `cortexops>=0.6.0,<0.7` from PyPI by default. `cortexops-version` also accepts a version,
  `latest`, any pip specifier, a `git+https://...#subdirectory=sdk` requirement, a local path, or `none`.
  The monorepo-only `bundled` value is not supported and fails with a configuration error.
