Download Link: https://assignmentchef.com/product/solved-comp1020-assignment3-advanced-topics-in-oop
<br>
You will implement seven classes which form the basis for a simple game simulation. A <strong>World</strong> will contain several <strong>Clans</strong>. A <strong>Clan</strong> will contain a number of <strong>Citizens</strong>. There will be two types of <strong>Citizens</strong>: <strong>Civilians</strong> and <strong>Fighters</strong>. There will be two types of <strong>Fighters</strong>: <strong>Archers</strong> and <strong>Barbarians</strong>. The simulation starts with several clans in the world, each containing random citizens. Repeatedly, one clan will attack another one. The civilians are not affected (unlike in real life), but the fighters damage or kill each other. When a clan loses all its fighters, it is removed from the world. The attacks continue until only one clan is left.

In this assignment you will practice how to implement concepts such as defining hierarchies of classes, abstract classes, and polymorphism. Please keep all of your methods short and simple. Make sure to call methods already created when appropriate, instead of duplicating code for no reason. Unless specified otherwise, all instance variables must be <strong>private</strong>, and all methods should be <strong>public</strong>.  Also, unless specified otherwise, there should be <strong><em>no </em>println</strong> statements in your classes. Objects usually do not print anything; they only return <strong>String</strong> values from methods. Make sure the outputs of the methods, including toString methods, in your classes, are exactly the same as the outputs explained in the instructions.

<h1>Instructions</h1>

A java file, TestA3.java, will be given to you which contains a main program which will control the overall simulation. You must write all of the following classes for this game.

1: The <strong>Citizen</strong> class:

Create an abstract Citizen class. Since it will not be possible to create an object of this class, its methods will be very simple. There are no instance variables. This class exists only to allow polymorphism to occur later.

<ul>

 <li>Implement a <strong>String toString()</strong> method which returns “<strong>Citizen</strong>“.</li>

 <li>Implement <strong>randomCitizen() </strong>method<strong>, </strong>that is a <strong>static</strong> method which will return a random <strong>Citizen</strong>. It should return a Civilian, Archer, or Barbarian, at random. (You will need to implement those classes first.)</li>

</ul>

2-The <strong>Civilian</strong> class:

Create a <strong>Civilian</strong> class as a subclass of the <strong>Citizen</strong> class.

Implement a <strong>String toString()</strong> method which returns “<strong>Civilian</strong>“.

<ul>

 <li>This class must have no instance variables, and no other methods. 3-The <strong>Fighter</strong> class:</li>

</ul>

Create an <strong>abstract Fighter</strong> class as a subclass of the <strong>Citizen</strong> class.

<ul>

 <li>Fighters have two private <strong>int</strong> instance variables: the “<strong>currentHealth</strong>”, and the <strong>“currentAttack”</strong>. When fighters attack each other, each one’s attack power is used to decrease the other one’s health. When a fighter’s health reaches 0, it dies.</li>

 <li>Create a custom constructor with two parameters which initializes both the health and the attack power. The first input parameter of your constructor should be currentHealth and the second one should be currentAttack.</li>

 <li>Implement a <strong>String toString()</strong> method which returns <strong>“Fighter”</strong> followed by the values of health and attack power.

  <ul>

   <li><strong>Fighter: health=100 attack=15</strong> o <strong>Fighter: health=116 attack=10</strong></li>

  </ul></li>

 <li>Provide accessor (get) methods only if needed by other classes.</li>

 <li>Do not provide any mutator (set) methods. The instance variables must be strictly private! These values are changed only by the following methods.</li>

 <li>Write a method <strong>decreaseHp(int) </strong>which will reduce the health of this fighter by the given amount. Health should not go below 0.</li>

 <li>Write a method <strong>boolean isDead()</strong> which will detect when the fighter is dead (health is zero).</li>

 <li>Write a method <strong>void gainPower()</strong> which does nothing. But subclasses of this class will use this method, and so the superclass must also have one to allow polymorphism.</li>

 <li>Write a method <strong>void gainPower(int)</strong> which increases the attack power by the given amount. Survivors of a fight will gain attack power, and this can be useful in the subclasses to override the gainPower() method.</li>

 <li>Note that health only goes down, never up, and attack power only goes up, never down. “What doesn’t kill you makes you stronger.” 4-The <strong>Archer</strong> class:</li>

</ul>

Create an <strong>Archer</strong> class as a subclass of the <strong>Fighter</strong> class.

<ul>

 <li>Archers always start with 100 health and 15 attack power. Provide a constructor with no parameters which does this.</li>

 <li>Implement a <strong>String toString()</strong> method which returns the String produced by the <strong>Fighter</strong> superclass, with <strong>“(Archer)”</strong> added to the end.

  <ul>

   <li><strong>Fighter: health=100 attack=15 (Archer)</strong></li>

  </ul></li>

 <li>Write a method <strong>void gainPower()</strong> which adds 10 to the archer’s attack power. 5-The <strong>Barbarian</strong> class:</li>

</ul>

Create a <strong>Barbarian</strong> class as a subclass of the <strong>Fighter</strong> class.

<ul>

 <li>Barbarians always start with 200 health and 20 attack power. Provide a constructor with no parameters which does this.</li>

 <li>Implement a <strong>String toString()</strong> method which returns the String produced by the <strong>Fighter</strong> superclass, with <strong>“(Barbarian)”</strong> added to the end.

  <ul>

   <li><strong>Fighter: health=145 attack=110 (Barbarian)</strong></li>

  </ul></li>

 <li>Write a <strong>method void gainPower()</strong> which adds 15 to the barbarian’s attack power. 6-The <strong>Clan</strong> class:</li>

</ul>

Create a Clan class.

<ul>

 <li>A clan must have a name, and a list of <strong>Citizens</strong>.</li>

</ul>

Provide a constructor with the header <strong>public Clan(String clanName, int clanSize</strong>) which will create a clan with the given name, and the given number of citizens. The number of citizens will never change later, although some of them (the fighters) may become dead. The constructor should create and store the correct number of random citizens, using the <strong>randomCitizen</strong> method of the Citizen class.

<ul>

 <li>Since a clan will be deleted from the game when it has no fighters left, it is important that the clan has at least one to start with. Make sure the first citizen is an Archer or Barbarian.</li>

 <li>Provide a <strong>getName()</strong> accessor method.</li>

 <li>Write a private <strong>int totalAttackPower()</strong> method which will find the total attack power of all Fighters in this clan who are not dead (sum of all attack power of all Fighters).</li>

 <li>Write a private <strong>int numFightersAlive()</strong> method which will count the number of Fighters in this clan who are not dead.</li>

 <li>Write a method with the header <strong>public void attack(Clan others)</strong> which will cause two clans to fight each other (this clan, and the others). When clan A attacks clan B, the maximum possible damage to members of clan B is the total attack power of clan A divided by the number of living fighters in clan B. The health of each living fighter in clan B should be reduced by a random value between 0 and this maximum value. This should be done in <strong>both</strong> directions as if both clans are attacking each other <strong>at the same time</strong> (this clan attacks the others, but the others attack this clan, too.)</li>

 <li>Write <strong>a boolean isDead() </strong>method which will return true if there are no living fighters in this clan.</li>

 <li>Write a <strong>void gainPower()</strong> method which will increase the attack power of every living fighter in this clan. This will be called (in the World class, below) to increase the power of the survivors of a fight. Don’t increase the attack power of dead fighters!</li>

 <li>Provide the usual <strong>String toString()</strong> method, which will return a multi-line String showing the information on the whole clan:

  <ul>

   <li>The first line should give the clan’s name. o The second line should give the clan’s total attack power. o The remaining lines should list the citizens, one per line, using the Strings provided by their toString methods. Do not list dead fighters, only living ones.</li>

   <li>Follow the example here:</li>

  </ul></li>

</ul>

<strong>Clan Raiders: </strong>

<strong>Total attack power: 440 </strong>

<strong>Fighter: health=87 attack=110 (Barbarian) </strong>

<strong>Fighter: health=145 attack=110 (Barbarian) </strong>

<strong>Civilian </strong>

<strong>Fighter: health=116 attack=110 (Barbarian) </strong>

<strong>Fighter: health=134 attack=110 (Barbarian) </strong>

<strong>  </strong>

7-The <strong>World</strong> class:

Create a <strong>World</strong> class. The world will contain a list of all of the clans, and provide a few methods that will complete the functionality of the game.

<ul>

 <li>A <strong>World</strong> must have instance variable(s) that store a list of <strong>up to 10 Clans</strong>. The number of clans will change during the game.</li>

 <li>Provide a constructor (no parameters) that creates a world containing no clans.</li>

 <li>Provide a <strong>void</strong> <strong>addClan(Clan c)</strong> method to add a new clan to the world. You do not need to check to see if the maximum number of clans has been exceeded.</li>

 <li>Provide an <strong>int</strong> <strong>getNumClans()</strong> method which will return the current number of clans in the world.</li>

 <li>The most important method is<strong> void attack(int clan1, int clan2)</strong> which will cause the two clans to attack each other. (The clans are identified by index number, not by name.) It should print a message indicating that this is happening, including the names of the two clans. Surviving fighters in each clan should gain power. If either (or both) clans no longer have any living fighters, they should be deleted from the world. A message should also be printed when a clan is deleted. You may want to write additional private methods to support this method.</li>

</ul>

Provide a <strong>String toString()</strong> method that will return a multi-line String listing the entire world, and all the clans in it. It should give the number of clans in the world, and then list each clan. Add some sort of dividing line to separate the clans and make them more visible. See the sample output that follows.

<strong>There are 3 clans in the world. </strong>

<strong>—– </strong>

<strong>Clan Settlers: </strong>

<strong>Total attack power: 65 </strong>

<strong>Fighter: health=200 attack=20 (Barbarian) </strong>

<strong>Fighter: health=100 attack=15 (Archer) </strong>

<strong>Civilian </strong>

<strong>Civilian </strong>

<strong>Fighter: health=100 attack=15 (Archer) </strong>

<strong>Fighter: health=100 attack=15 (Archer) </strong>

<strong>—– </strong>

<strong>Clan Raiders: </strong>

<strong>Total attack power: 80 </strong>

<strong>Fighter: health=200 attack=20 (Barbarian) </strong>

<strong>Fighter: health=200 attack=20 (Barbarian) </strong>

<strong>Civilian </strong>

<strong>Fighter: health=200 attack=20 (Barbarian) </strong>

<strong>Fighter: health=200 attack=20 (Barbarian) —– </strong>

<strong>Clan Hordes: </strong>

<strong>Total attack power: 75 </strong>

<strong>Fighter: health=200 attack=20 (Barbarian) </strong>

<strong>Fighter: health=200 attack=20 (Barbarian) </strong>

<strong>Civilian </strong>

<strong>Civilian </strong>

<strong>Fighter: health=200 attack=20 (Barbarian) </strong>

<strong>Civilian </strong>

<strong>Fighter: health=100 attack=15 (Archer) </strong>

-The <strong>TestA3</strong> class:

This class is provided for you to test Assignment 3. It creates a world containing 3 clans, and then causes pairs of these clans to attack each other until only 1 (or perhaps 0) clans remain in the world.

See the Sample output on the last page. Your output should be similar to this, but it does not have to match it exactly. Every time the program runs, the output will be different, because the game is random. Choose a test run that is not too large, but shows that your program works as it should. Put the output from that test run into a text file, and hand it in with your assignment. Name the file YourNameA3output.txt.