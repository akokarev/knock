# knock.su

The GitHub Pages root (`index.html`) is intentionally the PowerShell source.
This makes `irm "https://knock.su" | iex` return executable PowerShell text.

## First run

```powershell
& ([scriptblock]::Create((irm "https://knock.su")))
```

With no parameters the script copies this exact launch prefix (including the
final space) to the clipboard and prints an example plus short help.

## Second remote run without parameters

The first no-argument remote run stores a process-environment marker.
The second no-argument remote run saves the full script as `knock.ps1` in the
current directory and copies an ExecutionPolicy command to the clipboard.

A remote run **with parameters** clears the marker and only executes the
requested algorithm; it never saves the script locally.

A local `./knock.ps1` run never triggers the remote-save workflow.

## Examples

```powershell
& ([scriptblock]::Create((irm "https://knock.su"))) 1.1.1.1 tcp 443 ping 32
& ([scriptblock]::Create((irm "https://knock.su"))) 1.1.1.1 tcp 1234 delay 1000 ping 31 udp 4321
```

## GitHub Pages

Set the repository as the GitHub Pages source and configure the custom domain
`knock.su`. Keep `.nojekyll` so `index.html` is served as the exact file.
