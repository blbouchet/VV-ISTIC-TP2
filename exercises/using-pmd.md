# Using PMD

Pick a Java project from Github (see the [instructions](../sujet.md) for suggestions). Run PMD on its source code using any ruleset. Describe below an issue found by PMD that you think should be solved (true positive) and include below the changes you would add to the source code. Describe below an issue found by PMD that is not worth solving (false positive). Explain why you would not solve this issue.

## Answer

* faux positif : PMD nous indique qu’il y a plusieurs return. Cela ne pose pas de souci ici car la méthode est courte et facilement compréhensible.
public int search(final Object object) 
int i = size() - 1; // Current index
int n = 1; // Current distance
while (i >= 0) {
final Object current = get(i);
if (object == null && current == null|
object != null && object.equals(current))
return n;
i–;
n++;

return -1;
}


* vrai positif :
![image](https://user-images.githubusercontent.com/113097128/224299466-c7b53c2b-a22f-46a1-87d0-fceec35d2590.png)

dans classe StandAlone.java
final Instant start = Instant.now();
image.write(algo.cluster(image.getPixels()), out);
//CHECKSTYLE: stop all
System.out.println(“time=” + Duration.between(start, Instant.now()).toMillis());
//CHECKSTYLE: resume all

Au lieu de System.out.println, il vaudrait mieux utiliser un logger pour éviter de “polluer” la sortie dans la console.
