# toy_ds_project
Owen P. Elliot "Runs with the Eagles" Moose Knuckle Bateman helped me make this document
author = "naman"
import altair as alt
import pandas as pd


should_have_bought_butter = pd.DataFrame({
    "margarine_consumption": [8.2, 7, 6.5, 5.3, 5.2, 4, 4.6, 4.5, 4.2, 3.7],
    "maine_divorce_rate": [5, 4.7, 4.6, 4.4, 4.3, 4.1, 4.2, 4.2, 4.2, 4.1],
    "year": [2000, 2001, 2002, 2003, 2004, 2005, 2006, 2007, 2008, 2009]
})

marg_vs_time = alt.Chart(should_have_bought_butter).mark_line(color="steelblue").encode(
    x=alt.X("year").title("Year"),
    y=alt.Y("margarine_consumption")
        .title("Margarine consumption (lbs per capita)")
        .scale(zero=False)
).properties(
    height=250
)


divorce_rate_vs_time = marg_vs_time.mark_line(color="coral").encode(
    y=alt.Y("maine_divorce_rate")
        .title("Divorce rate in Maine (per 1000")
        .scale(zero=False)
)

(marg_vs_time | divorce_rate_vs_time).properties(
    title="Divorce rate in Maine correlates with margarine consumption"
)
