# How to prepare figures

Based on our year-long experience in preparing scientific publications
we suggest the following guidlines for preparing figures:

1. Each figure is generated by one python script.
2. The basename of the generated figure is the same as the one of the python script generating it.
3. The python script only generates the figure, it does not do any computations.
4. The data needed for plotting are available as numpy `.npz` files or `.csv` tables,
   do not use pickles (`.pkl`) for storing data.
6. Have a single central python module that defines basic figure layout settings.
7. No manual postprocessing by whatever graphics software.


## Why?

There are a number of good reasons for these rules.

The primary reason is: *figures always change*.

As long as you work on a manuscript you will always, or your
supervisor wants you to, or journal regulations require you to modify
your figure. Modifying a figure is a hassle if
- it takes some effort to find the spot where to edit the script,
- running the script takes a lot of time because data are computed,
- manual postprocessing is required.

Having small scripts (1.) that are simple to find (2.) and run quickly
(3.) without any manual postprocessing (7.) significantly lowers the
effort to actually modify a figure.

If you decide to change, for example, the fontsize or the colors in
all your figures, then it is really annoying and time consuming to go
through all your scripts and adapt these settings in every file. If
instead a single module takes care about these general issues (6.),
they can be modified in no time. The modules provided by the
`plottools` package aim at such a separation of content and design.

The second reason is: *figures want to be used*.

Ideally, the figures you generate are not only used for that
particular manuscript you are currently writing. You yourself or your
college, or your supervisor might want to use your figures in a
different context, like a poster, a talk, or another manuscript, a
review paper, a book chapter. Particularly for the latter, chances for
your figure to be used are dramatically increased, if the figure can
be easily modified. For this it is not sufficient to provide the pdf
(or even worse, a pixel file) of the figure. Rather, a simple
dedicated script (1.) with all necessary data (3.) that are readable
even ten years later (4.) that produces the complete figure (7.)
ensures that the figure can be easily adapted to another context as
needed.

The third reason is: *you need to provide the data of the figures anyways*.

Many journals nowadays require you to upload the data that were used
to generate the figures. Not the raw data, but the ones displayed in
the figure. So you need to store this data in files using formats that
can be read by others on whatever platform (4.). Storing the processed
data into files for direct plotting has the additional advantage, that
it reduces the dependencies of the code on external packages needed
for the computations. This also makes your figure code more easily
usable later on.

