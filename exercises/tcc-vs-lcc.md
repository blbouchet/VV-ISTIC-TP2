# TCC *vs* LCC

Explain under which circumstances *Tight Class Cohesion* (TCC) and *Loose Class Cohesion* (LCC) metrics produce the same value for a given Java class. Build an example of such as class and include the code below or find one example in an open-source project from Github and include the link to the class below. Could LCC be lower than TCC for any given class? Explain.

## Answer

Dans certaines circonstances, TCC et LCC peuvent produire la même valeur pour une classe Java donnée. Cela se produit lorsque toutes les méthodes de la classe accèdent aux mêmes variables d'instance ou n'accèdent à aucune variable d'instance. Dans les deux cas, il n'y a pas de paires de méthodes qui accèdent à des variables d'instance différentes, de sorte que les métriques TCC et LCC sont équivalentes.

Voici un exemple de code: Dans cette classe, toutes les méthodes accèdent aux mêmes variables d'instance x et y et TCC et LCC sont équivalentes.
public class ExampleClass {
  private int x;
  private int y;
  
  public void setX(int newX) {
    x = newX;
  }
  
  public int getX() {
    return x;
  }
  
  public void setY(int newY) {
    y = newY;
  }
  
  public int getY() {
    return y;
  }
}


Il est possible que LCC soit inférieur à TCC pour une classe donnée. Cela se produit lorsque les méthodes de la classe ne sont pas étroitement liées, mais qu'elles accèdent toujours aux mêmes variables d'instance. Dans ce cas, TCC sera élevé parce que les méthodes accèdent aux mêmes variables, mais LCC sera faible car les méthodes ne sont pas étroitement liées. Cette situation peut se produire lorsqu'une classe a des responsabilités multiples et alors elle viole le principe de responsabilité unique (SRP).
