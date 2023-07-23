# matplotlib-better-practice

## Save without unnecessary margins

By default, matplotlib inserts unnecessary margins when saving figures. To avoid this, use

```python
fig.tight_layout()
fig.savefig("out.pdf", bbox_inches="tight", pad_inches=0)
```
