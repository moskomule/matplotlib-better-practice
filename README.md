# matplotlib-better-practice

## Useful resources

* [Official cheet sheets](https://github.com/matplotlib/cheatsheets)
* [Official examples](https://matplotlib.org/stable/gallery/index)

## Save without unnecessary margins

By default, matplotlib inserts unnecessary margins when saving figures. To avoid this, use

```python
fig.tight_layout()
fig.savefig("out.pdf", bbox_inches="tight", pad_inches=0)
```
