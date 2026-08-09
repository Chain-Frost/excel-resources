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

## GitHub connection

The repository's GitHub remote is:

<https://github.com/Chain-Frost/excel-resources>

Confirm that a checkout is linked to the expected repository with:

```powershell
git remote -v
```

If `origin` is missing, add it with:

```powershell
git remote add origin https://github.com/Chain-Frost/excel-resources.git
git fetch origin
```

## Making changes

When this repository is checked out as a submodule, Git may report `HEAD detached at origin/main`.
This is normal: the parent repository records a specific `excel-resources` commit rather than a branch.

Before editing or committing, create a working branch from the current GitHub `main` branch. Use a short
branch name that describes the change:

```powershell
git fetch origin
git switch -c add-ifd-workbook origin/main
```

Add, commit, and publish the change:

```powershell
git add workbooks/format_IFD_CC.xlsx
git commit -m "Add IFD climate change workbook"
git push -u origin add-ifd-workbook
```

Open <https://github.com/Chain-Frost/excel-resources/pulls> and create a pull request from the published
branch into `main`.

The workbook files are tracked by Git LFS through `.gitattributes`. Check that an added workbook will be
stored through LFS with:

```powershell
git check-attr filter -- workbooks/format_IFD_CC.xlsx
```

The result should include `filter: lfs`.

## Updating the parent repository

After the change is merged into `excel-resources`, update the submodule reference from the root of the
parent `ryan-tools` checkout:

```powershell
git submodule update --remote excel-resources
git add excel-resources
git commit -m "Update excel-resources submodule"
```

Review the recorded submodule commit before pushing the parent-repository change:

```powershell
git diff --submodule=log HEAD~1
```
