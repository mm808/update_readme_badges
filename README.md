# update_readme_badges

A reuseable workflow to update readme status badges. The workflow here is to be called from repos that have set up badge links from shields.io for version per environment. The calling repo's readme must include env section headings and references to the badge files like in `samples/samplereadme.md`. The calling workflow must set `repo_name`, `repos_branch` and `vers` values as GIHUB_OUTPUTs.  
The workflow here will check out the main branch of the calling repo, update the badge files and check in the updates so that when viewing the main/default page of the repo the latest statuses are displayed.

ToDo: make an input for `default_branch` which will be found and passed from a step in the calling repo.

---

### Example call

The calling workflow should include the following:

```yaml
edit-vers-badge:
  if: always()
  needs: run-script
  uses: mm808/update_readme_badges/.github/workflows/edit_vers_badge.yml@dev
  with:
    repo_name: ${{needs.run-script.outputs.repo_name}}
    repo_branch: ${{needs.run-script.outputs.repo_branch}}
    vers: ${{needs.run-script.outputs.vers}}
```
