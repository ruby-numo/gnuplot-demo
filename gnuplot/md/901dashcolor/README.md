## line styles
[Original Demo](http://gnuplot.sourceforge.net/demo_4.6/dashcolor.html)

### 1

```ruby
# # Demonstrate explicit choice of both dot/dash pattern (linetype) and color (linecolor).
# #
# set termoption dash
#
# reset
# set xrange [-0.5:3.5]
# set yrange [-1:1.4]
# set bmargin 7
# unset ytics
# unset xtics
# #
# set title "Independent colors and dot/dash styles"
# unset colorbox
# #
# # define line styles using explicit rgbcolor names
# #
# set style line 1 lt 2 lc rgb "red" lw 3
# set style line 2 lt 2 lc rgb "orange" lw 2
# set style line 3 lt 2 lc rgb "yellow" lw 3
# set style line 4 lt 2 lc rgb "green" lw 2
# #
# set label 1 'set style line 1 lt 2 lc rgb "red" lw 3'    at -0.4, -0.25 tc rgb "red"
# set label 2 'set style line 2 lt 2 lc rgb "orange" lw 2' at -0.4, -0.35 tc rgb "orange"
# set label 3 'set style line 3 lt 2 lc rgb "yellow" lw 3' at -0.4, -0.45 tc rgb "yellow"
# set label 4 'set style line 4 lt 2 lc rgb "green" lw 2'  at -0.4, -0.55 tc rgb "green"
# set label 5 'plot ... lt 1 lc 3 ' at -0.4, -0.65 tc lt 3
# set label 6 'plot ... lt 3 lc 3 ' at -0.4, -0.75 tc lt 3
# set label 7 'plot ... lt 5 lc 3 ' at -0.4, -0.85 tc lt 3
# #
# set xlabel "You will only see dashed lines if your current terminal setting permits it"
# #
# show style line
# #
# # draw some plots
# #
# plot cos(x)     ls 1 title 'ls 1',   \
#      cos(x-.2)  ls 2 title 'ls 2',\
#      cos(x-.4)  ls 3 title 'ls 3',\
#      cos(x-.6)  ls 4 title 'ls 4', \
#      cos(x-.8)  lt 1 lc 3 title 'lt 1 lc 3',  \
#      cos(x-1.)  lt 3 lc 3 title 'lt 3 lc 3',  \
#      cos(x-1.2) lt 5 lc 3 title 'lt 5 lc 3'

Numo.gnuplot do
  set :termoption, :dash
  reset
  set xrange:-0.5..3.5
  set yrange:-1..1.4
  set bmargin:7
  unset :ytics
  unset :xtics
  set title:"Independent colors and dot/dash styles"
  unset :colorbox
  set :style, :line, 1, lt:2, lc_rgb:"red", lw:3
  set :style, :line, 2, lt:2, lc_rgb:"orange", lw:2
  set :style, :line, 3, lt:2, lc_rgb:"yellow", lw:3
  set :style, :line, 4, lt:2, lc_rgb:"green", lw:2
  set :label, 1, 'set style line 1 lt 2 lc rgb "red" lw 3', at:[-0.4,-0.25], tc_rgb:"red"
  set :label, 2, 'set style line 2 lt 2 lc rgb "orange" lw 2', at:[-0.4,-0.35], tc_rgb:"orange"
  set :label, 3, 'set style line 3 lt 2 lc rgb "yellow" lw 3', at:[-0.4,-0.45], tc_rgb:"yellow"
  set :label, 4, 'set style line 4 lt 2 lc rgb "green" lw 2', at:[-0.4,-0.55], tc_rgb:"green"
  set :label, 5, 'plot ... lt 1 lc 3 ', at:[-0.4,-0.65], tc_lt:3
  set :label, 6, 'plot ... lt 3 lc 3 ', at:[-0.4,-0.75], tc_lt:3
  set :label, 7, 'plot ... lt 5 lc 3 ', at:[-0.4,-0.85], tc_lt:3
  set xlabel:"You will only see dashed lines if your current terminal setting permits it"
  show :style, :line
  plot ["cos(x)", ls:1, title:'ls 1'],
    ["cos(x-.2)", ls:2, title:'ls 2'],
    ["cos(x-.4)", ls:3, title:'ls 3'],
    ["cos(x-.6)", ls:4, title:'ls 4'],
    ["cos(x-.8)", lt:1, lc:3, title:'lt 1 lc 3'],
    ["cos(x-1.)", lt:3, lc:3, title:'lt 3 lc 3'],
    ["cos(x-1.2)", lt:5, lc:3, title:'lt 5 lc 3']
end
```
![901dashcolor/001](https://raw.githubusercontent.com/ruby-numo/numo-gnuplot-demo/master/gnuplot/md/901dashcolor/image/001.png)

### 2

```ruby
# unset for [i=1:8] label i
# set title "The pointinterval property is another way to create interrupted lines"
# set xlabel "This technique works best for equally spaced data points"
# set bmargin 6
# set offset .05, .05
# set xrange [-0.5:3.3]
# set style func linespoints
#
# plot cos(x)     lt -1 pi -4 pt 6 title 'pi -4',   \
#      cos(x-.8)  lt -1 pi -3 pt 7 ps 0.2 title 'pi -3 pt 7 ps 0.2',  \
#      cos(x-.2)  lt -1 pi -6 pt 7 title 'pi -6',\
#      cos(x-.4)  lt -1 pi -3 pt 4 title 'pi -3',\
#      cos(x-.6)  lt -1 pi -5 pt 5 title 'pi -5', \
#      cos(x-1.)  with line lt -1 notitle,  \
#      cos(x+.2)  with line lt -1 lw 2 title 'lw 2'

Numo.gnuplot do
  unset "for [i=1:8] label i"
  set title:"The pointinterval property is another way to create interrupted lines"
  set xlabel:"This technique works best for equally spaced data points"
  set bmargin:6
  set offset:[0.05,0.05]
  set xrange:-0.5..3.3
  set :style, :func, :linespoints
  plot ["cos(x)", lt:-1, pi:-4, pt:6, title:'pi -4'],
    ["cos(x-.8)", lt:-1, pi:-3, pt:7, ps:0.2, title:'pi -3 pt 7 ps 0.2'],
    ["cos(x-.2)", lt:-1, pi:-6, pt:7, title:'pi -6'],
    ["cos(x-.4)", lt:-1, pi:-3, pt:4, title:'pi -3'],
    ["cos(x-.6)", lt:-1, pi:-5, pt:5, title:'pi -5'],
    ["cos(x-1.)", with:"line", lt:-1, notitle:true],
    ["cos(x+.2)", with:"line", lt:-1, lw:2, title:'lw 2']
end
```
![901dashcolor/002](https://raw.githubusercontent.com/ruby-numo/numo-gnuplot-demo/master/gnuplot/md/901dashcolor/image/002.png)
