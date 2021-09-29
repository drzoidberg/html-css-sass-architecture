<!-- css grid rationale -->

in order to figure out the column/row amount, try to think in terms FIRST of fixed width/height columns/rows and then (if that amount has to centered) surrond them with fractional units. That way you achieve CENTERED fixed widths.

most of the time, you main focus is the rows, so you even not name your rows.

<!-- when you use the -1 in grid-column & grid-row... -->
when you use the -1 in grid-column & grid-row, you are saying: "'til the end of the EXPLICIT GRID"

take into account the 'align-items' property, because is set to stretch by 'default'

grid-items will try to fit its entire area, but not images, because they have an intrinsic aspect-ratio attached to them. So, the images try to keep its aspect ratio before trying to fit in the grid. Use align-items: center to circumvent this.

<!-- how to create complex grids (for a gallery, for example) -->
usually is by trial and error, based on the sources and amount of grid-items you have to place


<!-- other comments -->
look how the **ROW GAP** is more affected depending on the viewport height than it is on COLUMN GAP

<!-- if you plan tu use grid on responsive layouts using media queries -->
please name you grid-templates!