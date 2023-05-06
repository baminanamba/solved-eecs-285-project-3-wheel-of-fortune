Download Link: https://assignmentchef.com/product/solved-eecs-285-project-3-wheel-of-fortune
<br>
For this project, you will implement a version of the popular game show “Wheel of Fortune” including a graphical user interface (GUI) using the Swing toolkit. Details of the gameplay will follow.

<strong>Authors</strong>

The original project was written by Andrew M. Morgan for EECS 285.

<h1>Table of Contents</h1>

<h1>Project Roadmap</h1>

This is a big-picture view of what you’ll need to do to complete this project. Most of the pieces listed here also have a corresponding section later on in the spec that goes into more detail.

Since this is a GUI project, we will not be able to autograde it for correctness. Instead, we will grade your submission by hand for both correctness and for <a href="https://eecs285.github.io/eecs285.org/style.html">programming practices</a>. We will also run automated style and programming-practice checks on your code.

The following is a tentative grade breakdown for this project:

80% hand-graded correctness

10% automated style and programming practices

10% hand-graded style and programming practices

You may work alone or with a partner. Please see the syllabus for partnership rules.

<h2>Download the starter code</h2>

The starter code is available at <a href="https://eecs285.github.io/p3-wheel/starter-files.zip">https://eecs285.github.io/p3-wheel/starter-files.zip</a><a href="https://eecs285.github.io/p3-wheel/starter-files.zip">.</a> The following files are included:

<table width="613">

 <tbody>

  <tr>

   <td width="218"><strong>File(s)</strong></td>

   <td width="395"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="218">WheelOfFortune.java</td>

   <td width="395">Command-line interface for the game</td>

  </tr>

  <tr>

   <td width="218">WheelOfFortuneFrame.java</td>

   <td width="395">Implements the GUI for the game</td>

  </tr>

  <tr>

   <td width="218">images/</td>

   <td width="395">Images corresponding to spaces on the game wheel</td>

  </tr>

 </tbody>

</table>

Extract the files to a temporary directory.

<h2>Set up your project</h2>

Follow the <a href="https://eecs285.github.io/p1-sentiments/setup.html">Project 1 setup tutorial</a> to set up your project. Use the package name described below.

Your Java files should all be in a package with the structure eecs285.proj3.&lt;uniqname&gt; , where

&lt;uniqname&gt; is your uniqname. <strong>If you are working in a partnership, then use both of your uniqnames, in alphabetical order, separated by an underscore.</strong> For example, if I am working alone, I would put the following package directive at the top of each .java file: <strong>package</strong> eecs285<strong>.</strong>proj3<strong>.</strong>akamil<strong>;</strong>

If I am working with schatzju , then I would use the following: <strong>package</strong> eecs285<strong>.</strong>proj3<strong>.</strong>akamil_schatzju<strong>;</strong>

<h2>Familiarize yourself with the game rules below</h2>

Read through and make sure you understand the rules for Wheel of Fortune before writing any code.

<strong>Familiarize yourself with the GUI design specification </strong>Your GUI should look and behave as described below.

<h2>Design, implement, and test your classes</h2>

Implement your GUI in the WheelOfFortuneFrame class that is part of the starter code. The starter code also makes use of a WheelSpace class for which you need to provide the implementation. Define any other classes you need and place them appropriately as standalone classes in their own .java files, nested classes, or anonymous classes.

<h2>Submit</h2>

Submit the following files to the autograder.

WheelOfFortuneFrame.java any other .java files you write

Do <strong>not</strong> submit WheelOfFortune.java . We will use our own version of this file, so make sure that your implementation does not require it to be modified.

As per course policy, we will grade your last submission to the autograder. It is your responsibility to ensure that your last submission is complete.

<h2>Early Submission Bonus</h2>

If your final submission occurs at least two days before the due date (at or before 11:59pm two days before the due date), you will receive bonus points calculated at 5% of your overall score for the project (including both autograder tests and hand grading). In other words, if your overall score is <em>N</em>, it will be <em>1.05 * N</em> after the bonus is applied.

If your final submission occurs on the day before the due date (by 11:59pm), you will receive bonus points calculated at 2.5% of your overall score for the project. In other words, if your overall score is <em>N</em>, it will be <em>1.025 * N</em> after the bonus is applied.

<h1>How the Game Works</h1>

Wheel of Fortune has been a popular televised game show for over 30 years. The game centers around a word puzzle that the players have to solve. Initially, the puzzle is presented as a series of blank spots, one per letter of the puzzle. Punctuation, such as spaces, commas, etc., are displayed directly and do not need to be guessed during gameplay by the players. Players fill in the puzzle by one of two ways.

For consonants, players spin a large wheel made up of spaces of varying monetary amounts, along with some “bad” spaces, such as “Lose a Turn” and “Bankrupt”. If the spin results in a monetary amount, the player must guess a consonant. If the guessed letter exists in the puzzle, all instances of the letter are displayed, and the player is awarded an amount of money equal to the number of instances of the letter times the monetary amount resulting from the wheel spin. Once the player chooses to spin the wheel, they must guess a consonant – they may not “change their mind” and decide instead to buy a vowel or solve the puzzle.

For vowels, the player does NOT spin the wheel. Instead, the player announces they wish to “buy a vowel”. A set amount (typically $250, which should be what your program uses, but make this a named constant so its easy to change if the rules change) is deducted from their account and the player selects a vowel (vowels can’t be bought if the player has less than the required cost of a vowel). If the vowel is in the puzzle, all instances are illuminated. No money is awarded for illuminating vowels, and the cost of buying a vowel is the same regardless of the number of instances of the vowel illuminated. Once a player chooses to buy a vowel, they must guess a vowel – they may not “change” their mind and decide instead to spin the wheel or solve the puzzle.

Regardless of consonant or vowel, if the letter chosen by the player is in the puzzle, the player’s turn continues, otherwise, the player’s turn ends and play moves to the next player.

If the player spins the wheel and lands on the “Lose A Turn” space, the player is not able to guess a letter, and play advances to the next player. If the player’s spins lands on “Bankrupt”, any money the player has accumulated is lost (their accumulated winnings are set to 0), and play advances to the next player.

At any time, the active player may choose to solve the puzzle rather than spinning or buying a vowel. The player is given the chance to say what they believe the full puzzle is. In our implementation of the game, the guess is made by typing the guess, and it must be typed exactly correct, including punctuation and characters that are automatically displayed; however case (i.e. upper case vs. lower case) is not considered when determining whether the typed guess was correct or not. If correct, the player wins the full amount of money they have accumulated, and all other players win nothing, regardless of how many letters they have guessed correctly and how much money they have accumulated. If the guess is incorrect, the player loses their turn, and play advances to the next player.

Players must be careful, though, because once they opt to try to solve the puzzle, they must make a guess – they may not “change their mind” and spin the wheel or buy a vowel instead.

<h1>Simulation Overview</h1>

Your implementation of the popular game show will use a graphical user interface written using Swing components in Java. The game will be implemented as a Java application (as opposed to an applet). When a new game is first started, it will first prompt the user for the number of players. The user will then be prompted to enter each player’s name. While the real game show is always played with three players, your implementation will allow for any number of players greater or equal to 1 (playing with only 1 player isn’t much fun though). During grading, we will expect your GUI to look “nice” for a number of players between 1 and 5 inclusive. Do NOT limit the number of players to 5 or fewer, but if your GUI starts to look a little funny with more than 5 players, that’s fine – there’s only so much room in the interface. We will test more than 5 players to make sure it is supported, but we will not be overly concerned with the look of the GUI when the number of players gets large. Finally, the puzzle to be solved is prompted for, and will be input as well. During actual gameplay, the puzzle would be input by someone who is not one of the players, but during testing, you’ll enter the puzzle just like the other inputs. After this, the game is displayed, and play commences as described.

To make the game a little more “realistic”, your implementation will display an image of the wheel space resulting from a spin. The wheel is generally made up of 24 equally sized spaces (that is a spin result is determined by a uniform random draw of 24 possibilities). The images for the board spaces will be provided to you, and the names of the images are in the format

&lt;spaceNumber&gt;_&lt;spaceLabel&gt;.jpg . For example, if space number 5 is a $700 space, the image will be named 5_700.jpg . The labels loseATurn and bankrupt correspond to the “Lose A Turn” and “Bankrupt” spaces.

Since we want to keep this project focused on Swing GUI development, we expect you to only implement the rules described in this spec. The real game show has many many quirks that we will not be implementing for this project. Instead, you are to implement the very basic version of a single round of Wheel of Fortune described here.

<h1>User-Interface Requirements</h1>

For a typical GUI project in industry, the design of the interface would be done by UI/UX (userinterface/user-experience) specialists, who would then pass on mockups and wire-frame diagrams to the programmers to implement. For this project, we will use the screenshots below in lieu of mockups. Your program should mimic the look as closely as possible. Nontrivial departures from the given design will result in your submission losing points.

<strong>Note:</strong> The screenshots below were taken on a Mac. If you are developing on another platform, expect some elements to look a little different. In particular, the top portion of the window will be platform-dependent, and buttons will also look different on other platforms. If you are working on Windows, you can find some selected screenshots <a href="https://eecs285.github.io/p3-wheel/windows_ui.html">here</a><a href="https://eecs285.github.io/p3-wheel/windows_ui.html">.</a> <strong>You can also find instructions there for fixing UI scaling on high-density displays for Windows.</strong>

<h2>Game Setup</h2>

When the program is started, it should display a modal for the number of players:

Your program should validate the input to make sure it is a positive integer. If it isn’t, the program should inform the user that their entry was invalid with a dialog. It should then prompt them again when the dialog is dismissed.

After the number of players has been entered, the program should ask for the names of each player in turn. Display a zero-based index as part of the prompt (“player #0”, “player #1”, and so on):

Then the program should prompt a non-player to enter a puzzle:

The setup modals should not be closable by the user by clicking on the “X” at the top of the window. See the documentation for <a href="https://docs.oracle.com/javase/8/docs/api/javax/swing/JFrame.html#setDefaultCloseOperation-int-">setDefaultCloseOperation()</a> for how to enforce this.

<h2>Main Game View</h2>

After setup, the program should display the main view of the game. At the top are the players, with their names and scores. The current player should be highlighted with a red border, and the other players should have black borders:

The middle of the game view has three buttons, for buying a vowel, spinning the wheel, and solving the puzzle. To the right is a display of the current wheel space. Initially, it should just show the image corresponding to space 0. After that, it should always show the result of the most recent wheel spin.

The game buttons should only be enabled if the user is allowed to perform that action. Specific cases where you should disable a button:

If the user has insufficient money to buy a vowel, then that button should be disabled.

If all five vowels have already been guessed, then the button to buy a vowel should be disabled.

If all 21 consonants have already been guessed, then the button to spin the wheel should be disabled.

If the user clicks on an action button, the action buttons should be disabled until the action is completed. For instance, if the user clicks on “Buy a Vowel”, then the three middle buttons should be disabled until they click on a vowel button.

The bottom portion of the game display has buttons for vowels and consonants. These should only be enabled when the player needs to guess a letter after buying a vowel or spinning the wheel.

Beneath the letter buttons is the puzzle display. There should be an extra space between each letter of the puzzle. Letters should be hidden by being replaced with a dash ( – ), until they are guessed. Guessed letters should displayed as capital letters. Punctuation and numbers should always be displayed.

<h2>Spinning the Wheel and Buying a Vowel</h2>

If the user clicks on “Spin the Wheel”, then the wheel space should show the image for the result.

If a numerical value comes up, the buttons for consonants should be enabled:

If the player guesses a consonant that is in the puzzle, then all instances of that consonant should be revealed, and the player’s score should be updated:

Now that the player has sufficient money, they are able to buy a vowel, which results in the vowel buttons being enabled:

If they guess a vowel in the puzzle, all instances should be revealed, and the player’s turn should continue:

If the player elects to buy another vowel, they should only be given the option of selecting a vowel that has not already been guessed:

If they guess a vowel that is not in the puzzle, they lose their turn:

If the wheel is spun a second time, the player should only be allowed to select a consonant that has not already been guessed:

Once all five vowels have been guessed, the player should not be allowed to guess a vowel:

<h2>Solving the Puzzle</h2>

If a player elects to attempt to solve the puzzle, a modal should be displayed for them to enter their guess:

A guess is only correct if it exactly matches the puzzle, including punctuation but excluding case (in other words, the game makes no distinction between lower-case and capital letters). An incorrect guess should result in a dialog with an error message:

An example of entering a correct guess:

This should result in an informational dialog displaying which player and how much money they won:

Your program should quit when the game-ending dialog closes. See the <a href="https://docs.oracle.com/javase/8/docs/api/java/awt/Window.html#dispose--">dispose()</a> method for reference.

<h2>Full Gameplay Video</h2>

The following are sample videos of playing a full game.

<h2>More Players and Long Names</h2>

Your interface should support at least five players while still looking nice:

Your implementation must support more than five players, but it is fine if the interface doesn’t look as nice or behaves strangely for larger numbers of players.

It is fine if your interface cuts off names if they are too long:

<h1>Loading Images</h1>

The wheel-space images are read from an images subdirectory in the same directory as your

.java source files. Your code should read in the images with the specifically expected names described above and set up each space based on the filename of the image. In other words,

2_800.jpg will represent space number 2 and a money value of 800 dollars. Rather than hardcode that space 2 is an 800 dollar space, parse the filename to determine this. You need to make sure this works as expected, because during testing, we will almost certainly change the names of the images and expect your program to handle things appropriately.

You may assume there are exactly 24 spaces on the wheel for the purposes of this project.

The starter code in WheelOfFortuneFrame.java provides a method loadImages() that reads images from the images directory. The code will ignore files that do not follow the naming scheme above. You will need to replace &lt;uniqname&gt; in the definition for the UNIQNAME constant with your uniqname(s) (using the same format as the directory for your project). You will also need to provide a definition for the WheelSpace class, as well as the implementation of the

getSpaceValue() method in the WheelSpaceImageFilter class.

<h1>Spinning the Wheel</h1>

Your implementation <strong>must</strong> spin the wheel in the order determined by the Random object provided to the WheelOfFortuneFrame constructor. Use the <a href="https://docs.oracle.com/javase/8/docs/api/java/util/Random.html#nextInt-int-">nextInt()</a> method as follows to determine the index of the next wheel space: <strong>int</strong> index <strong>=</strong> generator<strong>.</strong>nextInt<strong>(</strong>NUM_WHEEL_SPACES<strong>);</strong>

The command-line interface in WheelOfFortune.java takes an optional argument for the random seed value. See the <a href="https://eecs285.github.io/p1-sentiments/setup.html#setting-command-line-arguments">setup tutorial</a> for how to set command-line arguments in IntelliJ.

<h1>Clarifications, Resources, and Advice</h1>

The following are a few clarifications on gameplay and the requirements for this project:

In order to win the game, a player must solve the puzzle. This is the case even if all letters are revealed – they must still choose to solve the puzzle and type it in correctly.

It is expected behavior for the modals requiring input to pop up at the top-left of the screen, even if the main frame is elsewhere. On the other hand, the dialogs following a correct or incorrect guess at solving the puzzle should appear centered over the main frame.

Your program should not accept empty input for any modal. If the input is empty, selecting OK should do nothing, and the modal should stay open so the user can still enter input.

We will not manually resize your windows when we test your program.

Since the computation required by the game should not be time consuming, you are free to do it all in the Event Dispatch Thread. In other words, you are not required to use SwingWorker s.

In order to get your interface to look like the screenshots, you will need to use many different types of layouts, including BorderLayout , Box / BoxLayout , FlowLayout , and GridLayout . It will likely require trial and error with nesting different layouts in order for the result to look the way you want.

In addition to the lecture slides, you may find the following Java tutorials useful:

<a href="https://docs.oracle.com/javase/tutorial/uiswing/layout/box.html">BoxLayout </a><a href="https://docs.oracle.com/javase/tutorial/uiswing/components/border.html">borders </a><a href="https://docs.oracle.com/javase/tutorial/uiswing/components/dialog.html">dialogs</a>

You may also find the <a href="https://docs.oracle.com/javase/8/docs/api/java/awt/Component.html#repaint--">repaint()</a> method useful to update a UI component after making a change.