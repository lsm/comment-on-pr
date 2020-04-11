# Comment on PR via GitHub Action

A GitHub action to comment on the relevant open PR when a commit is pushed.

## Usage

- Requires the `GITHUB_TOKEN` secret.
- Set message content by:
  - providing the `msg` parameter.
  - setting the `COMMENT_PR_MESSAGE` env variable when `msg` parameter is not provided.
- Supports `push` and `pull_request` event types.

### Sample workflow

```yaml
name: comment-on-pr example
on: pull_request
jobs:
  example:
    name: sample comment
    runs-on: ubuntu-latest
    steps:
      - name: comment PR
        uses: unsplash/comment-on-pr@master
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          COMMENT_PR_MESSAGE: "Conent of the message" // Used when `msg` is not provided. This value can be picked up from previous steps.
        with:
          msg: "Check out this message!"
          check_for_duplicate_msg: false  # OPTIONAL 
```
