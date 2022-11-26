## Show Output in JSON Format

```python
@app.command()
def ls(
    show_json: bool = typer.Option(
        False,
        "--json",
        help="Show the talks in JSON format.",
    ),
):
    """List the next conference talks."""
    talks = conference.next_talks()
    console = Console()
    if show_json:
        talk_dicts = [conference.convert_talk_to_dict(talk) for talk in talks]
        console.print_json(json.dumps(talk_dicts))
        return
```