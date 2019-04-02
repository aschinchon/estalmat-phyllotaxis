
# Generative coding con R (6/4/2019)
## ESTALMAT Madrid

### Cargamos la libreria

EXPLICACION

```r
library(ggplot2)
```

### Pintamos unos puntos en un circulo de radio 1

EXPLICACION

```r
t <- seq(0, 2*pi, length.out = 50)
x <- sin(t)
y <- cos(t)
df <- data.frame(t, x, y)

ggplot(df, aes(x, y)) +
  geom_point() + 
  coord_equal()
```

<img src="img/plot1.png" width="450" height="450" />


### Introducimos el Golden Angle

EXPLICACION

```r
points <- 10 # No. de puntos
angle <- pi * (3 - sqrt(5)) # golden angle

t <- (1:points)
x <- sin(t * angle)
y <- cos(t * angle)
df <- data.frame(t, x, y)

ggplot(df, aes(x*t, y*t)) +
  geom_point() + 
  coord_equal() + 
  geom_text(aes(label=t), vjust = -1, size = 5)
```
<img src="img/plot2.png" width="450" height="450" />

### Pintamos mas puntos y quitamos los ejes

EXPLICACION

```r
points <- 200 # No. de puntos
angle <- pi * (3 - sqrt(5)) # golden angle
t <- (1:points)
x <- sin(t * angle)
y <- cos(t * angle)
df <- data.frame(t, x, y)

ggplot(df, aes(x*t, y*t)) +
  geom_point() +
  coord_equal() +
  theme(panel.background = element_rect(fill="white"),
        panel.grid=element_blank(),
        axis.ticks=element_blank(),
        axis.title=element_blank(),
        axis.text=element_blank())
```

<img src="img/plot3.png" width="450" height="450" />

### Cambiamos los colores y el tama�o de los puntos

EXPLICACION

```r
ggplot(df, aes(x*t, y*t)) +
  geom_point(size=8, alpha=0.5, color="darkgreen") +
  coord_equal() + 
  theme(panel.background = element_rect(fill="white"),
        panel.grid=element_blank(),
        axis.ticks=element_blank(),
        axis.title=element_blank(),
        axis.text=element_blank())
```
<img src="img/plot4.png" width="450" height="450" />

### El diente de le�n

EXPLICACION

```r
ggplot(df, aes(x*t, y*t)) +
  geom_point(aes(size=t), alpha=0.5, shape=8)+
  coord_equal() + 
  theme(legend.position="none",
        panel.background = element_rect(fill="white"),
        panel.grid=element_blank(),
        axis.ticks=element_blank(),
        axis.title=element_blank(),
        axis.text=element_blank())
```

<img src="img/plot5.png" width="450" height="450" />


### Usar un shape raruno

Meter el dibujo de los shapes

For shapes that have a border (like 21), you can colour the inside and outside separately. Use the stroke aesthetic to modify the width of the border

```r
ggplot(mtcars, aes(wt, mpg)) +
geom_point(shape = 21, colour = "black", fill = "white", size = 5, stroke = 5)
```

```r
ggplot(df, aes(x*t, y*t)) +
  geom_point(size=8, alpha=0.5, color="darkgreen") +
  coord_equal() + 
  theme(panel.background = element_rect(fill="white"),
        panel.grid=element_blank(),
        axis.ticks=element_blank(),
        axis.title=element_blank(),
        axis.text=element_blank())
```


### Cambiamos colores

EXPLICACION

```r
ggplot(df, aes(x*t, y*t)) +
  geom_point(aes(size=t), alpha=0.5, shape=17, color="yellow")+
  coord_equal() +
  theme(legend.position="none",
        panel.background = element_rect(fill="darkmagenta"),
        panel.grid=element_blank(),
        axis.ticks=element_blank(),
        axis.title=element_blank(),
        axis.text=element_blank())
```

<img src="img/plot6.png" width="450" height="450" />

### Modificamos el angulo

EXPLICACION

```r
angle <- 2
points <- 1000

t <- (1:points)*angle
x <- sin(t)
y <- cos(t)

df <- data.frame(t, x, y)

ggplot(df, aes(x*t, y*t)) +
  geom_point(aes(size=t), alpha=0.5, shape=17, color="yellow")+
  coord_equal() +
  theme(legend.position="none",
        panel.background = element_rect(fill="darkmagenta"),
        panel.grid=element_blank(),
        axis.ticks=element_blank(),
        axis.title=element_blank(),
        axis.text=element_blank())
```

<img src="img/plot7.png" width="450" height="450" />

### Cambiando todo

```r
library(ggplot2)
angle <- 13*pi/180
points <- 2000

t <- (1:points)*angle
x <- sin(t)
y <- cos(t)

df <- data.frame(t, x, y)

ggplot(df, aes(x*t, y*t)) +
  geom_point(size=80, alpha=0.1, shape=1, color="magenta4")+ 
  coord_equal() +
  theme(legend.position="none",
        panel.background = element_rect(fill="white"),
        panel.grid=element_blank(),
        axis.ticks=element_blank(),
        axis.title=element_blank(),
        axis.text=element_blank())

```

<img src="img/plot8.png" width="450" height="450" />

### Reglas del concurso

xxxxxxxxxxxx

Referencias

+ Colores: http://www.stat.columbia.edu/~tzheng/files/Rcolor.pdf
+ Puedes guardar los dibujos lanzando `ggsave("elige_un_nombre.png", width = 3, height = 3, dpi = 600)`

