---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---


# Productive Numbers
What's your favorite prod?



Set-up code (ignore)

```{code-cell} ipython3
:tags: [hide-input]

import plotly.graph_objects as go  
import networkx as nx
import sympy
from sympy.ntheory import factorint
primes = list(sympy.primerange(1, 100))

def d_to_p(x):
    if x == 0: return 0
    if x == 1: return ()
    
    factors = factorint(x)
    
    max_prime = max(factors.keys())
    mp_index = primes.index(max_prime)
    y = [0] * (mp_index + 1)
    
    # key recursive step
    for p, e in factors.items():
        i = primes.index(p)
        y[i] = d_to_p(e)
    
    return tuple(y)


def draw_tree_plotly(tree, root_pos=(0, 0), parent_pos=None, fig=None, pos=None, level=0):
    """Recursively draw a tree using Plotly, differentiating black and white dots."""
    if fig is None:
        fig = go.Figure()
    if pos is None:
        pos = {}

    # Assign a unique label to each node
    node_label = f"node_{len(pos)}"
    pos[node_label] = root_pos

    # Draw edge to parent if exists
    if parent_pos:
        fig.add_trace(go.Scatter(
            x=[parent_pos[0], root_pos[0]],
            y=[parent_pos[1], root_pos[1]],
            mode="lines",
            line=dict(color="black")
        ))

    # Determine color based on whether it's a zero or an internal node
    is_leaf = (tree == 0)
    node_color = "white" if is_leaf else "black"
    border_color = "black"  # White dots should still have a black border
    size = 15  # Make dots larger

    # Draw the node (black or white dot)
    fig.add_trace(go.Scatter(
        x=[root_pos[0]],
        y=[root_pos[1]],
        mode="markers",
        marker=dict(size=size, color=node_color, line=dict(color=border_color, width=2)),
        name=node_label
    ))

    # Base case: If tree is just a leaf (zero), stop recursion
    if is_leaf:
        return fig

    # Recursively add children
    n = len(tree)
    for i, child in enumerate(tree):
        offset = i - n // 2  # Spread children symmetrically
        new_pos = (root_pos[0] + offset, root_pos[1] - 1)
        draw_tree_plotly(child, new_pos, root_pos, fig, pos, level + 1)

    return fig

def d2tree_plotly(n):
    """Generate and plot the tree for a given integer n."""
    tree = d_to_p(n)  # Convert n into a tree representation
    fig = draw_tree_plotly(tree)
    fig.update_layout(
        showlegend=False,
        xaxis=dict(visible=False),
        yaxis=dict(visible=False),
        paper_bgcolor="rgba(0,0,0,0)",  # Transparent background
        plot_bgcolor="rgba(0,0,0,0)"  # Transparent plot area
    )
    fig.show()
```

```{code-cell} ipython3

import ipywidgets as widgets
from IPython.display import display
 
def update_plot(n):
    d2tree_plotly(n)

slider = widgets.IntSlider(value=5, min=1, max=50, step=1, description="n:")
widgets.interactive(update_plot, n=slider)
```