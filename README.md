# Golden_Ratio_gif
gif created by plotting multiples of golden ratio on unit circle

```
# The following code will produce 50 png files.
# After installing imagemagick, opend command prompt.
# Navigate to location of png and run command below.
# magick convert *.png -delay 3 -loop 0 binom.gif

frames = 50
points <- 5000
tt <- 1.1*(1:points)

for(i in 1:frames){
  
  # angle <- i * pi/180
  angle <- i*pi*(3 - sqrt(5))
  t <- (1:points)*angle
  x <- sin(t)
  y <- cos(t)
  df <- data.frame(tt, t, x, y)
  
  # creating a name for each plot file with leading zeros
  if (i < 10) {name = paste('000',i,'plot.png',sep='')}
  if (i < 100 && i >= 10) {name = paste('00',i,'plot.png', sep='')}
  if (i >= 100) {name = paste('0', i,'plot.png', sep='')}

  #saves the plot as a .png file in the working directory
  ggplot(df, aes(x*t, y*t)) + 
    geom_point(aes(x*t, y*t, size = tt), alpha = .1, color = 'magenta4', shape = 1) +
    theme(panel.grid = element_blank()) +
    theme(panel.background = element_rect(fill = "white")) +
    theme(axis.title = element_blank()) +
    theme(axis.ticks = element_blank()) +
    theme(axis.text = element_blank()) +
    theme(legend.position = 'none')
  ggsave(name)
}

```
