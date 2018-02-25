---
title: "Post: Future Date"
date: 9999-12-31
categories:
  - Post
---


Hallo neuer Post with python
{% highlight python %}
import pandas as pd
pd.DataFrame([12,3,])
{% endhighlight %}
This post lives in the future and is dated {{ page.date | date: "%c" }}. When building Jekyll with the `--future` flag it should appear.
