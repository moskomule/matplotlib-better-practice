# matplotlib-better-practice

## Useful resources

* [Official cheet sheets](https://github.com/matplotlib/cheatsheets)
* [Official examples](https://matplotlib.org/stable/gallery/index)

* [Rougier's tutorial](https://github.com/rougier/matplotlib-tutorial)

## Save without unnecessary margins

By default, matplotlib inserts unnecessary margins when saving figures. To avoid this, use

```python
fig.tight_layout()
fig.savefig("out.pdf", bbox_inches="tight", pad_inches=0)
```

## Legend outside of axes

```python
fig, ax = plt.subplots(...)
...
handles, labels = ax.get_legend_handles_labels()
fig.legend(handles, labels, loc='center', bbox_to_anchor=(0.5, -0.2), ncol=2, borderpad=0.3, labelspacing=1, fontsize=11)
fig.tight_layout()
```

## Draw Circles


```python
from matplotlib.patches import Circle

ax.add_patch(Circle((0, 0), # center
                    1, # radius
                    facecolor='none', edgecolor="gray", linestyle="dashed", linewidth=2, alpha=0.5)
)
```

## Figure in Figure


```python
# add a child ax in a parent ax
ax.plot(...)

axins = ax.inset_axes([0.6, 0.15, 0.32, 0.6])
axins.plot(...)
axins.set_xlim(...)
axins.set_ylim(...)
# with zoom
ax.indicate_inset_zoom(axins)
```


![da_effect](https://github.com/moskomule/matplotlib-better-practice/assets/11806234/f2ffb602-311e-4f25-ade1-b9cc6d4de2a5)


## Nested Figure

```python
fig = plt.figure(figsize=(12, 4))
gs_base = GridSpec(1, 3)
nest_gses = [GridSpecFromSubplotSpec(2, 2, width_ratios=(4, 1), height_ratios=(1, 4),
                      wspace=0.05, hspace=0.05, subplot_spec=gs_base[i]) for i in range(3)]

for gs, indices in zip(nest_gses, [a, b, c]):
    ax = fig.add_subplot(gs[1, 0])
    ax_histx = fig.add_subplot(gs[0, 0], sharex=ax)
    ax_histy = fig.add_subplot(gs[1, 1], sharey=ax)
    _scatter_hist(points, points[indices], ax, ax_histx, ax_histy)

fig.tight_layout()

```

![image](https://github.com/moskomule/matplotlib-better-practice/assets/11806234/7ad33490-ac44-4b9f-9e2d-4513b8ef0503)
