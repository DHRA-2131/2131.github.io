---
description: 'Description: These group variables together.'
---

# Vectors and Arrays

***

### Array Video Explanation:

{% embed url="https://www.youtube.com/watch?index=30&list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb&v=ENDaJi08jCU" %}
Arrays - The Cherno
{% endembed %}

***

### Vector Video Explanation: (Resizable Arrays)

{% embed url="https://www.youtube.com/watch?index=46&list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb&v=PocJ5jXv8No" %}
Dynamic Arrays in C++ (std::vector) - The Cherno
{% endembed %}

### Example Usage for Vex!

Source can be found [here](https://github.com/DHRA-2131/2024-25-2131H/blob/main/Rewrite%203/src/2131H/Systems/Screen.cpp). This is not the cleanest implementation of an autonomous route selector but it's kind of waste full to spend too much time on making a pretty selector.

Definition of the vector:

{% code title="src/2131H/Systems/screen.cpp" lineNumbers="true" %}
```cpp
// Creating a vector of displayable "AutonCards" that can be shown on the brain screen.
std::vector<AutonCard> Cards = {
    {"NO AUTO", "", NULL_AUTON}, // Note: this is using the {} constructor and auto deducing the type
    AutonCard("DEBUG", "", Autonomous::debug), // This method is also useable
    {"GOAL SIDE (QUAL)", "", Autonomous::goalSide},
    {"RING SIDE (QUAL)", "", Autonomous::ringSide},
    {"SOLO AWP (QUAL)", "[Profanity]", Autonomous::soloAWP},
    {"5 Ring Side (ELIMS)", "I Quit", Autonomous::ringSideFive},
    {"5 Goal Side (ELIMS)", "I'm Done", Autonomous::goalSideFive},
    {"GOAL RUSH (ELIMS)", "", Autonomous::goalRush}};
```
{% endcode %}

Draw Logic:

<pre class="language-cpp" data-title="src/2131H/Systems/screen.cpp" data-line-numbers><code class="lang-cpp"><strong>// If ScreenDetector detects the button changed from released to pressed
</strong>// or it's the inital loop (Basically if screen pressed)
if (ScreenDetector.getChanged() &#x26;&#x26; ScreenDetector.getValue() || initial)
{
  // Increment Index (This is the index that gets shown to the brain)
  index++;                    
  if (index >= Cards.size())  
  { 
    // If Index is too large, then rollover to the start (Prevents index going out of range)
    index = 0;
  }
  
  // Draw the card (This calls the function to draw the card information
  // This draws the selected autonomous route's name and description
  Cards[index].draw(redTeam);  
}
</code></pre>

***

_Not an AD: Do you think that learning pointers should come before learning arrays? Feel free to contribute!_ :smile:
