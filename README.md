# Excel resources

Excel workbooks and supporting notes extracted from
[`Chain-Frost/ryan-tools`](https://github.com/Chain-Frost/ryan-tools).

The repository retains the original file history and commit attribution from `ryan-tools`. It is normally
checked out at `excel-resources/` as a submodule of that repository. Workbooks are managed with Git LFS.

## Layout

- `workbooks/`: reusable workbooks grouped by workflow.

Install Git LFS before cloning, then use:

```powershell
git lfs install
git clone https://github.com/Chain-Frost/excel-resources.git
```

When working through `ryan-tools`, initialise the checkout with:

```powershell
git submodule update --init excel-resources
```
