# Databricks Sparse Repo Example

This example repository demonstrates how to use cone patterns in sparse checkout mode.  Sparse checkout mode is useful when your git repository conflicts with the [limits](https://docs.databricks.com/en/repos/limits.html#file-and-repo-size-limits).  If you are running into the file and repo size limits it's likely you have some large files in your repo or your code is stored in a [monorepo](https://en.wikipedia.org/wiki/Monorepo).

## Example Scenerio

This repo stores both the `finacial_forecast` and the `marketing_mix_model`.  We want to develop these projects inside of Databricks and version our code using Repos but we are getting the following error 

``` error
Error creating repo
Timed out while performing operation.  This may be due to a remote repo that is too large or a slow network.  We do not recommend having more than 10000 notebooks in a repo.
```

Note: This repo won't actually hit the file or repo size limitation

## Enabling Sparse Checkout Mode and Using Cone Patterns

In our scenerio, we want to add the `finacial_forecast` project as repo inside Databricks. In order to stay under the repo limit and avoid the above error we need to just pull in files from the project folder.  [Cone patterns](https://git-scm.com/docs/git-sparse-checkout#_internalscone_mode_handling) come from git's sparse-checkout function and allow you to specify which directories to include.

### Adding Cone Patterns
The cone patterns themselves are 