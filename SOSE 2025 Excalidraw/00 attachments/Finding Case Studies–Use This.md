---
tags:
  - cs
  - csonline
  - git
  - github
  - issues
  - pr
  - pull-requests
  - searching-prs
---
# Search Syntax for Github's issues and pr's

| Qualifier                                       | Description                                    | Example                                                     |
| ----------------------------------------------- | ---------------------------------------------- | ----------------------------------------------------------- |
| `is:pr`                                         | Restricts results to pull requests only        | `is:pr`                                                     |
| `is:open` / `is:closed` / `is:merged`           | Filters PRs by state (open/closed/merged)      | `is:pr is:open`<br>`is:pr is:closed`<br>`is:pr is:merged`   |
| `author:`                                       | PRs created by a specific user                 | `is:pr author:octocat`                                      |
| `assignee:`                                     | PRs assigned to a specific user                | `is:pr assignee:octocat`                                    |
| `commenter:`                                    | PRs where a user has commented                 | `is:pr commenter:octocat`                                   |
| `label:`                                        | PRs with a specific label                      | `is:pr label:bug`                                           |
| `review-requested:`                             | PRs where a user or team’s review is requested | `is:pr review-requested:octocat`                            |
| `reviewed-by:`                                  | PRs reviewed by a specific user                | `is:pr reviewed-by:octocat`                                 |
| `base:`                                         | PRs targeting a specific branch                | `is:pr base:main`                                           |
| `head:`                                         | PRs from a specific branch                     | `is:pr head:feature-branch`                                 |
| `draft:true` / `draft:false`                    | Filters draft or ready-for-review PRs          | `is:pr draft:true`<br>`is:pr draft:false`                   |
| `updated:` / `created:` / `merged:` / `closed:` | PRs within a date/time frame                   | `is:pr updated:>=2025-07-01`<br>`is:pr created:<2025-01-01` |
| `sort:`                                         | Sort PRs by comments, created, updated, etc.   | `is:pr sort:updated-desc`                                   |
| `in:title` / `in:body`                          | Search term in PR title or body                | `is:pr in:title "refactor"`                                 |
| `milestone:`                                    | PRs assigned to a milestone                    | `is:pr milestone:v2.0`                                      |

**Example Combined Search:**  
`is:pr is:open label:bug assignee:octocat base:develop`  
*Open PRs labeled "bug", assigned to "octocat", targeting the "develop" branch.*

**See also:** [GitHub Docs: Searching issues and pull requests](https://docs.github.com/en/search-github/searching-on-github/searching-issues-and-pull-requests#search-by-qualifier)

