## Find clock reversals and gaps in an audit export

Returns [gap count, nonadvancing IDs, backward clock steps, first reversed row, clean flag]. Preserve original receipt order; a gap is an observation for investigation. Invalid arguments and nonfinite results return an empty vector.

1. Open an empty file named `barnowl-demo.blyx`.
2. Type `blyx-barnowl-demo` and select **Barnowl — runnable example**. You can also use **Snippets: Fill File with Snippet**.
3. Choose **Blyx: Run File** from the command palette. Change an argument near the end of `fn main()` to try another input.

Expected output

```text
1
1
1
2
0
```

[Work through the example in the browser](https://www.blyx-lang.space/play?example=package-barnowl)
