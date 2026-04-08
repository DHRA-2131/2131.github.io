---
description: 'Description: Recursion!'
---

# Loops

***

### Loops Video Explanation:

{% embed url="https://www.youtube.com/watch?v=_1AwR-un4Hk" %}

***

### Range Based For-Loop

{% code title="include/2131H/Localization/WheelOdometry.hpp" lineNumbers="true" %}
```cpp
// Resets the Odometry's Position and Tracking Wheels.
void reset() override
{
  // Lock the update mutex to stop race conditions
  std::lock_guard<pros::Mutex> lock(updateMutex);
  
  // Reset Current Position and Last Position.
  currentPose = Pose::zero();
  lastPose = Pose::zero();

  // Reset Current Velocity (local space and global)
  currentVelocity = {0, Angle<Radians>::fromRadians(0.0f)};
  globalVelocity = Pose{0, 0, 0}; 

  // Update last time
  lastUpdateTime = pros::micros();

  // linearWheels is a vector of AbstractTrackingWheel
  // Go through each wheel in the vector. Grab an instance (wheel)
  // and call AbstractTrackingWheel::reset() 
  for (auto& wheel : linearWheels) { wheel->reset(); }
  for (auto& wheel : lateralWheels) { wheel->reset(); }
};
```
{% endcode %}

***

### Continue, Break, Return:

{% embed url="https://youtu.be/a3IZ8WaIFAA?si=-9u1o0T7xTvMVK_j" %}
Control Flow in C++ - The Cherno
{% endembed %}

### Example Control Flow:

{% code title="include/2131H/Localization/WheelOdometry.hpp" lineNumbers="true" %}
```cpp
void update_() override
{
  // Lock a mutex to stop potential data race
  std::lock_guard<pros::Mutex> lock(updateMutex);
  
  // If you didn't add any wheels or inertial sensors this will not work
  // Return to avoid code problems! 
  if (linearWheels.size() == 0 || inertialSensors.size() == 0) return;
  
  // Calculate average heading from all the IMU Sensors
  Angle<Radians> heading = 0.0f;
  
  // Range Based For-Loop
  for (auto& sensor : inertialSensors)
  {
    // * -sensor->get_heading() to convert from clockwise positive to
    // counterclockwise positive
    heading = heading + Angle<Radians>::toRadians(Angle<Degrees>(
                            360.0f - sensor->get_heading()));
  }
  
  // If the heading is infinite or Not a Number it's probably bad data 🤔
  if (std::isinf(heading.getValue()) || std::isnan(heading.getValue()))
    return;
  
  heading = Angle<Radians>(
      heading.getValue() / static_cast<float>(inertialSensors.size()));
  
  // Calculate change in heading
  Angle<Radians> deltaHeading = heading - lastPose.getAngle<Radians>();
  
  // Average heading during the last 10ms (in radians)
  float averageHeading = lastPose.getAngle<Radians>().getValue() +
                         (deltaHeading.getValue() / 2.0f);
  
  // Calculate the delta time since last update
  auto currentTime = pros::micros();
  float deltaTime = static_cast<float>(currentTime - lastUpdateTime) /
                    1000000.0f;  // in seconds
  
  // If the change of in time is zero (or less than zero???) then return to avoid div! by 0.
  if (deltaTime <= 0.0f)
    return;  // Prevent division by zero or negative time
    
  /* Rest Ommited to Shorten Codeblock */
```
{% endcode %}

***

_Not an AD: Want to add examples of using a while loop? Contribute today!_ :smile:

