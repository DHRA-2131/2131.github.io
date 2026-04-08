---
description: 'Description: Compiled Cherno videos for you to learn from!'
---

# Variables

***

### Variable Video Explanation:

{% embed url="https://youtu.be/zB9RI8_wExo?si=o5xWbY4ifzo7mDBl" %}
Variables in C++ - The Cherno
{% endembed %}

***

### Simplified Variable Reference Sheet:

<table><thead><tr><th width="110.66668701171875">Type Name:</th><th width="296.6666259765625">Keyword:</th><th width="103.7332763671875">Size (Bytes)</th><th width="233.7332763671875">Size (Numerical)</th><th width="214.66650390625">Operations:</th><th width="325.5999755859375">Conventional interpretation</th></tr></thead><tbody><tr><td><p>Void,</p><p>Null,</p><p>None</p></td><td><code>void</code></td><td>0</td><td>0</td><td>None</td><td><p>The idea of nothing in code form. </p><p>Ex: Function should return nothing</p><p><code>void functionName(/*params*/);</code></p></td></tr><tr><td>Integer</td><td><code>int</code></td><td>4 Bytes</td><td><p>Max: <code>21474836487</code></p><p>Min: <code>-21474836487</code></p></td><td><code>*, / (not 0), +, -, %</code></td><td>Analogous to an integer in mathematics (Numbers without decimals) </td></tr><tr><td>Floating Point Number</td><td><code>float</code></td><td>4 Bytes</td><td><p>Max: <code>3.40282347e+38</code></p><p>Min (Non-Zero / Negative): <code>1.17549435e-38</code></p><p>Other: <code>inf, -inf, NaN</code></p></td><td><code>*, /, +, -, %</code></td><td>Floats are your numbers with decimals. <em>Note: A vex brain is built to work with floats and you probably don't need the precision of a</em> <code>double</code></td></tr><tr><td>Character</td><td><code>char</code></td><td>1 Byte</td><td><code>0 to 255</code></td><td><code>*, / (not 0), +, -, %</code></td><td>Conventional interpretation is as a letter or symbol. You can think of this as an index to a character set like <a href="https://en.wikipedia.org/wiki/Extended_ASCII">ASCII</a>.</td></tr></tbody></table>

***

### Constant Keyword (`const`):

{% embed url="https://www.youtube.com/watch?index=33&list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb&v=4fJBrditnJU" %}
CONST in C++ - The Cherno
{% endembed %}

### Example of the `const` keywords in a Vex Project!

Source can be found [here](https://github.com/MerpCat500/Fun-Project-of-Doom/blob/main/include/2131H/Chassis/DifferentialChassis.hpp).&#x20;

{% code title="include/2131H/Chassis/DifferentialChassis.hpp" lineNumbers="true" %}
```cpp
// Structure that stores physical properties about a robot (These don't normally change)
struct PhysicalProperties
{
  // Note: full variable names!
  //* Physical Size of robot
  const float drivelength;  // In inches
  const float drivewidth;   // In inches
  
  //* Useful Physical Information
  const float trackwidth;   // In inches
  const float tracklength;  // In inches

  //* Important Wheel Characteristics
  const float gearing;        // Scalar
  const float wheelDiameter;  // Diameter of wheel

  // Total Amount of Motors on Drivetrain
  const float motorWattage;  // Wattage of motors

  // Theoretical maximum values 
  // (These can be computed from the variables, but are commonly used so it's worth caching them)
  const float maxVelocity;  // Max Velocity of Drivetrain
  const Angle<Radians> maxAngularVelocity;  // Max angular velocity of drivetrain
  
  /* Constructor Omitted to Shorten Codeblock */
  // This would assign values to the variables inside the struct
};
```
{% endcode %}

***

### `static` Keyword:

{% embed url="https://www.youtube.com/watch?index=21&list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb&v=f3FVU-iwNuA" %}

{% embed url="https://www.youtube.com/watch?index=48&list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb&v=f7mtWD9GdJ4" %}

***

_Not an AD: Please add more to these things, people be confused. Contribute today!_ :smile:
