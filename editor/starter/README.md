# Barnowl starter

Inspect a supplied audit export for sequence gaps, replays and clock reversals.

Open the extracted folder in VS Code. With Blyx 0.2.1 and its host toolchain installed, choose **Terminal → Run Task → Run Barnowl** or run the following command in this directory.

```sh
blyxc native-run main.blyx
```

Expected output

```text
1
1
1
2
0
```

The vendor directory contains the framework source for 0.1.0 and its license texts. [Read the API guide](https://www.blyx-lang.space/packages/barnowl) · [View the release](https://github.com/Rahulchaube1/blyx-barnowl/releases/tag/v0.1.0)
