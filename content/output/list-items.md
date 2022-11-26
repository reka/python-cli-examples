## List Items in Plain and Wrap Format

```python
@app.command()
def ls(
    plain: bool = typer.Option(False, help="Display 1 talk per line."),
):
    result = conference.next_talks()
    console = Console()
    for talk in result:
        console.print(str(talk), soft_wrap=plain)
```

## More Info

* [Rich docs of `soft_wrap`](https://rich.readthedocs.io/en/latest/console.html#soft-wrapping)