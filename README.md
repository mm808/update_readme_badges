# update_readme_badges

A reuseable workflow to update readme custom status badges. The workflow here is to be called from repos that have set up custom svg files for build status and version per environment. The calling repo must have an assets directory as shown in the samples directory in this repo and the readme must include references to the badge files.  
The workflow here will check out the main branch of the calling repo, update the badge files and check in the updates so that when viewing the main/default page of the repo the latest statuses are displayed.
ToDo: make an input for `default_branch` which will be found and passed from a step in the calling repo.

---

### Example call

The calling workflow should include the following:

```yaml
edit-badges:
  if: always()
  needs: run-script
  uses: mm808/update_readme_badges/.github/workflows/edit_badges.yml@dev
  with:
    repo_name: ${{needs.run-script.outputs.repo_name}}
    repo_branch: ${{needs.run-script.outputs.repo_branch}}
    vers: ${{needs.run-script.outputs.vers}}
    env_name: ${{needs.run-script.outputs.env_name}}
    job_status: ${{needs.run-script.outputs.job_status}}
```
