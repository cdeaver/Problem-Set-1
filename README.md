####Tradd Deaver
####January 19 2016
####CSCI 223 Problem Set 1

####Collaborators: 
1. James Andrus

####Resources:
1. TextBook

####Feedback:
This assignment was easy to understand the concepts, but the implementation proved more difficult than expected.  One problem was creating the array with the percentages, and the other was comparing that to the exact percentages given by the book. 

###Problem Set 1
Creating a simulation experiment of two die being rolled.  The goal is to find the number of rolls required to make the percentages (chances) of rolling a number between 2 and 12 the same as the exact chances given by the book. 

####Full Source Code
[Full Code](https://github.com/cdeaver/Problem-Set-1/blob/master/source%20code)

###Discussion
The purpose of this code is to give the user the amount of rolls required to make an array of simulated percentages to get within .001 of the exact percentages given by the book.  To explain better, the book gave me code that creates an array of exact chances of landing on a number between 2-12 using two die.  I had to create my own code to create an array that also gave me these percentages, but also counted the number of rolls it took to reach these numbers.  In escence, how many times do you have to roll a pair of dice so that your simulated percentages match the exact percentages.

####Testing Output
1.The program prints the exact percentages generated
2.The program prints the simulated percentages generated to within .001 of exact
3.The program prints the number of times required to roll a pair of dice for this to happen

####Partial Testing Code
```javascript
public static void main(String[] args) {
    System.out.println("Exact: ");
    int sides = 6;
    double[] dist = new double[2 * sides + 1];
    for (int i = 1; i <= sides; i++)
	    for (int j = 1; j <= sides; j++)
		    dist[i + j] += 1.0;
    for (int k = 2; k <= sides * 2; k++) {
      dist[k] /= 36.0;
      System.out.println(dist[k]);
    }
    System.out.println();
    System.out.println("Simulated:");
    int rolls = 0;
    double[] simDist = new double[13];
    double[] simProbability = new double[13];
    while (!withinLimit(dist, simProbability)) {
     int result = rollDice();
     rolls++;
     simDist[result] += 1.0;
     for (int i = 2; i < simDist.length; i++) {
	  simProbability[i] = simDist[i] / rolls;
     }
     }
     for(int i = 2; i < simProbability.length;i++){
       System.out.println(simProbability[i]);
     }
     System.out.println();
     System.out.println("It took " + rolls + " rolls to get desired result");
}
```
####Testing Output
```javascript
Exact: 
0.027777777777777776
0.05555555555555555
0.08333333333333333
0.1111111111111111
0.1388888888888889
0.16666666666666666
0.1388888888888889
0.1111111111111111
0.08333333333333333
0.05555555555555555
0.027777777777777776

Simulated:
0.02771339438966636
0.05599057844820026
0.08298983925730108
0.11066564766904294
0.13928110552889736
0.16757081824673942
0.13789042434569077
0.11018955861533257
0.08418006189157698
0.05548943207587356
0.028039139531678716

It took 79817 rolls to get desired result

```
The number of rolls changes every time you run the program. 
