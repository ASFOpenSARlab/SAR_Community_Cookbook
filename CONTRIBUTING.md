# ASF Cookbook Contributor's Guide
<br>

We welcome contributions!
<br>

Please read our [Code of Conduct](https://github.com/ASFOpenSARlab/ASF_SAR_Community_Cookbook/blob/main/CODE_OF_CONDUCT.md) before contributing.

This project uses the standard **fork → branch → pull request** workflow. 

## 1. View current [issues](https://github.com/ASFOpenSARlab/ASF_SAR_Community_Cookbook/issues) and engage in discussions
See if the bug or feature you plan to work on is already under discussion or. If it's not, start a discussion by raising an [issue](https://github.com/ASFOpenSARlab/ASF_SAR_Community_Cookbook/issues).

## 2. Develop a notebook in your own GitHub repository

Develop the notebook in your own repository and import it into this cookbook (covered in Steps 7-9). 

Use the [notebook template in this cookbook](notebooks/notebook-template.ipynb) as a starting point when developing your workflow.

## 3. Fork the repository
Click the **Fork** button at the top-right of the [SAR_Community_Cookbook GitHub page](https://github.com/ASFOpenSARlab/SAR_Community_Cookbook) to create your own copy of the repo.

## 4. Clone your fork
```bash
git clone https://github.com/<your-username>/SAR_Community_Cookbook.git
cd SAR_Community_Cookbook
```

## 5. Create a feature branch
```bash
git checkout -b feature/my-change
```

## 6. Add the upstream remote
This lets you pull updates from the main project.
```bash
git remote add upstream https://github.com/ASFOpenSARlab/ASF_SAR_Community_Cookbook.git
git remote -v
```

## 7. Add the url for your notebook to `cookbook_sources.yml`

All notebook additions are synced from their source repos. Adding the GitHub url of your notebook to `cookbook_sources.yml` will pull a freshly synced copy of your notebook into this cookbook each night.

Example:
```
sources:
  - url: https://github.com/ASFOpenSARlab/NISAR_Cookbook/blob/main/notebooks/GSLC_Faraday_Rotation_Estimation.ipynb

```

This cookbook's automated notebook syncing script attempts to discover and copy any additional images, scripts, and files that your notebook uses. If you need to include additional files that were not automatically discovered, use the following syntax in `cookbook_sources.yml`:
```
sources:
  - url: https://github.com/ASFOpenSARlab/NISAR_Cookbook/blob/main/notebooks/GSLC_Faraday_Rotation_Estimation.ipynb
    include:
      - path/in/repo/to/extra/required/file_1.txt
      - path/in/repo/to/extra/required/file_2.txt
```

## 8. Manually run the `.github/scripts/sync_external_notebooks.py` script once to populate the imported notebooks

Run the following in a terminal:
```
cd SAR_Community_Cookbook
pixi run python .github/scripts/sync_external_notebooks.py  
```

## 9. Update `myst.yml` so your notebook appears in the correct chapter

After running the  `.github/scripts/sync_external_notebooks.py` script, you will notice a new `Imported Notebooks` section at the bottom of `myst.yml`:

```
# >>> external notebooks: managed by .github/scripts/sync_external_notebooks.py. Manually move files to an existing TOC section or leave here.
- title: "Imported Notebooks"
    children:
    - file: external/path/to/notebook.ipynb
# <<< external notebooks
```

Move `- file: external/path/to/notebook.ipynb` from its default location into an appropriate Cookbook chapter. The updated location in the table of contents will be retained during nightly updates.

## 10. Add any new dependencies to a new or existing Pixi environment
If you add dependencies, you will need to update the `pixi.toml` to add them to the [Pixi](https://rse-guidelines.readthedocs.io/en/latest/fundamentals/computing-development-environments/pixi/#:~:text=packages%20go%20here-,3.%20Adding%20Dependencies,-Add%20conda%20packages) environment.

## 11. Add and commit your changes
Commit in small, focused steps.
```bash
git add path/to/file1 path/to/file2
git commit -m "Describe your change"
```

## 12. Keep your branch up to date with the upstream cookbook
```bash
git fetch upstream
git merge upstream/main
# or
git rebase upstream/main
```

## 13. Push your branch
```bash
git push origin feature/my-change
```

## 14. Open a Pull Request
Go to your fork on GitHub and click **Compare & pull request**.

Please include a detailed description of your updates and the motivation behind them.
