# Mod Release CI Integration

This project uses a GitHub Action as part of its CI (Continuous Integration) process to automatically package and upload a release ZIP whenever a new version is tagged and released.

---

## Create a Git Tag

To trigger the action, you need to create a Git tag following the `vX.Y.Z` format.

**Example:**

```bash
git tag v1.0.0
git push origin v1.0.0
```

You can also create a tag directly on GitHub via the "Releases" tab.

---

## Create a GitHub Release

Once the tag is pushed:

- Go to your repository on GitHub
- Click on **"Releases" > "Draft a new release"**
- Select the tag you created (e.g., `v1.0.0`)
- Fill in release notes if needed
- Click **"Publish release"**

Alternatively, using the GitHub CLI:

```bash
gh release create v1.0.0 --title "v1.0.0" --notes "First release"
```

---

## What the GitHub Action Does

After the release is published, the GitHub Action will automatically:

### Update Version in `fomod/Info.xml`

It updates the `<Version>` field in the `fomod/Info.xml` file to match the current release tag (e.g., `v1.0.0`).

### Zip Folders

It compresses the `data/` and `fomod/` directories into a single ZIP file named:

```
ClanCenturioEquipmentProgression-v1.0.0.zip
```

### Upload Release Asset

It uploads the ZIP file to the GitHub Release page. You'll find the file ready to download in the release assets section.

✅ That's it! After creating a release, everything else is automated.
