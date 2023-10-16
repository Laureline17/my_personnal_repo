# Testing

The practical exercise in week 6 involved competitive testing. For this practical exercise, I worked in pair programing.

## First example of test code 

This is my first test code :

```
﻿using Xunit;
using Hangman;

namespace UnitTestProject
{
    public class TestsResetDisplay
    {
        [Fact]
        public void TestResetDisplay()
        {
            GamePage gamepage = new("Easy");
            string word = "testing";

            gamepage.ResetDisplay(word);

            for (int i = 0; i < 12; i++)
            {
                char letter = i < word.Length ? word[i] : ' ';
                Label letterLabel = gamepage.FindByName<Label>("Letter" + (i + 1));
                Assert.Equal(letter.ToString(), letterLabel.Text);
            }

        }
    }
}
```

This code is made to test the function "resetDisplay()". 
The purpose of this code is to reset the word of the game.

In this test, we created an instance of the GamePage.
We define a string "word" with the value "testing". 
Then we call our function ResetDisplay passing the word as an argument.
To see if our function actually works we created a for loop witch check if there are the appropriate number of visible labels.
If there are the appropriate number of visible labels it's means that the function ResetDisplay works.
This is important to test this part of the code beacause if this one didn't works, the game cannot be played.


## Second example of test code

```
public void ResetDisplay(string word)
    {

        // Reset hangman image and update UI for hidden word and remaining attempts.

        for (int i = 0; i < 12; i++)
        {
            if (i < word.Length)
            {
                char letter = word[i];
                Label letterLabel = this.FindByName<Label>("Letter" + (i + 1));
                letterLabel.Text = char.IsWhiteSpace(letter) ? " " : letter.ToString();
            }
            else
            {
                Label letterLabel = this.FindByName<Label>("Letter" + (i + 1));
                letterLabel.Text = " ";
            }
        }

        RemainingAttemptsLabel.Text = $"Remaining Attempts: {remainingAttempts}";
    }

```
This code test the same code, it's also for the function ResetDisplay.
This code also have a for loop.
Within each iteration of the loop, 
the test checks whether the text displayed in the Label control named "LetterX" matches the expected character in the "testing" word at the same position.
It also handles the case of displaying spaces when the word length is less than 12.
