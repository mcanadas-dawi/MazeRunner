# MazeRunner
### Kata kyu 6 CodeWars
Recorre el laberinto sin tocar los muros. Se le dará una matriz 2D del laberinto y una serie de direcciones.
Su tarea es seguir las instrucciones dadas. Si llegas al punto final antes de que se hayan realizado todos tus movimientos debes devolver "Finish". Si golpeas alguna pared o sales del borde del laberinto, deberías devolver "Dead".
Si todavía te encuentras en el laberinto después de usar todos los movimientos, debes devolver "Lost".
maze = [[1,1,1,1,1,1,1],
        [1,0,0,0,0,0,3],
        [1,0,1,0,1,0,1],
        [0,0,1,0,0,0,1],
        [1,0,1,0,1,0,1],
        [1,0,0,0,0,0,1],
        [1,2,1,0,1,0,1]]

      0 = Safe place to walk
      1 = Wall
      2 = Start Point
      3 = Finish Point

direction = {"N","N","N","N","N","E","E","E","E","E"} == "Finish"

### Reglas:
##### 1. La matriz Maze siempre será cuadrada, es decir, N x N, pero su tamaño y contenido variarán de una prueba a otra.

##### 2. Las posiciones de salida y llegada cambiarán para las pruebas finales.

##### 3. La matriz de direcciones siempre estará en mayúsculas y tendrá el formato N = Norte, E = Este, W = Oeste y S = Sur.

##### 4. Si llegas al punto final antes de que se hayan realizado todos tus movimientos, debes regresar a Finalizar.

##### 5. Si golpeas alguna pared o sales del borde del laberinto, deberías regresar Muerto.

##### 6. Si te encuentras todavía en el laberinto después de usar todos los movimientos, debes regresar a Lost.


```java
public class MazeRunner {
  public static String walk(int[][] maze, String[] directions) {
   //Inicio variables para los ejes
    int x = 0;
    int y = 0;
    //Recorro el laberinto y asigno coordenadas
    for (int i = 0; i < maze.length; i++) {
      for (int j = 0; j < maze.length; j++) {
        if (maze[i][j] == 2) {
          x = j;
          break;
        }
      }
      if (maze[i][x] == 2) {
        y = i;
        break;
      }
    }
    //Movimiento del runner
    for (int mov = 0; mov < directions.length; mov++) {
      if (directions[mov] == "N") {
        y--;
      }
      if (directions[mov] == "S") {
        y++;
      }
      if (directions[mov] == "W") {
        x--;
      }
      if (directions[mov] == "E") {
        x++;
      }
      // Devuelvo los valores correspondientes
      if (x == -1 || y == -1 || y == maze.length || x == maze.length) {
        return "Dead";
      }
      if (maze[y][x] == 3) {
        return "Finish";
      }
      if (maze[y][x] == 1) {
        return "Dead";
      }
    }
	return "Lost";  
	}
	}
```

