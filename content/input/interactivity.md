## CLI Guidelines

* Prompt for missing values. 👩 
* Do not prompt if `stdin` isn't an interactive terminal. 💻
* Do not prompt if the `--no-input` option has been provided

```python
@app.command()
def create(
    id_option: str = typer.Option(
        None,
        "--id",
        help="Unique ID for the code snippet. Can contain letters, numbers, - and _.",
    ),
    description_option: str = typer.Option(
        None,
        "--description",
        help="Ca. 1 sentence description.",
    ),
    interactive_flag: bool = typer.Option(
        True,
        "--interactive/--no-interactive",
        "--input/--no-input",
        help="Switch whether interactive prompts are shown. Use `--no-input` when you call this command from scripts.",
    ),
):
    interactive = sys.stdin.isatty() and interactive_flag

    id_ = id_option or interactive and Prompt.ask("ID")
    description = description_option or interactive and Prompt.ask("Description")
```

## More Info

* [CLI Guidelines / Interactivity](https://clig.dev/#interactivity)
* [Rich: Prompt docs](https://rich.readthedocs.io/en/latest/prompt.html)