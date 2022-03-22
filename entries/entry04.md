# Entry 4
##### 3/21/22

Over the past few weeks, I have worked more on the movement system and added features like running, gravity, and jumping. Making the character run was simple and just changed the speed at which the player moves. By watching the previous [video](https://www.youtube.com/watch?v=_QajrabyTJc&t=1085s), I was able to learn how to implement gravity using the velocity of the character. Jumping on the other hand was harder because it would interact with gravity. I learned how to do the running and jump by following [Unity's Documentation](https://docs.unity3d.com/Manual/index.html) and experimenting with different lines of code. 

The running mechanic was relatively easy to implement because it was a simple if statement that would change the speed of the player. Speed was already a set variable and all that would change was to increase the speed when the condition was true. The condition was if "Left Shift" was pressed the speed would be set to a higher number. Otherwise, if the wasn't pressed the speed would be set back to its original number. 
```
  if(Input.GetKey("left shift")){
      speed = 20f;
      Debug.Log("SPEED!");
  } else {
      speed = 12f;
  }
```

The gravity system itself was a little more challenging it involved math equations that would calculate the velocity at which the player fell. One other condition that I needed to add was to check if the player was already on the ground. This is important because the velocity will constantly increase even if there isn't space below it to fall. First, I create a Boolean isGrounded by creating an invisible sphere at the bottom of the player. If this sphere is touching objects with the ground tag it will be set to true. The final condition would be if isGrounded is true the velocity would be set to 0 else the velocity would be set to the acceleration of gravity * time. 
```
  control.Move(velocety * Time.deltaTime);
  isGrounded = Physics.CheckSphere(groundCheck.position, groundDistance, groundMask);

  if(isGrounded){
      velocety.y = 0f;
  } else {
      velocety.y += gravity * Time.deltaTime;
  }
```

The jumping mechanic was a little weird to set up because it overlaps/utilizes the gravity system. Since I wanted the character to be able to jump and double jump(a second jump when mid-air) I need to create a boolean value for both of them. To make the player jump the condition requires that the space button is pressed and that the canJump condition is true. This condition also extends to the doubleJump condition. When either of the conditions are true the gravity is inverted in a way so that the player goes up for a brief moment. This simulates the movement of jumping because after the initial jump the gravity system recognized the player is off the ground and immediately starts to inflict gravity on the player. 
```
  if(Input.GetKeyUp("space") && canJump){
      // rb.AddForce(jump * jumpForce, ForceMode.Impulse);
      velocety.y += 10f;
      Debug.Log("JUMP!");
  } else if(Input.GetKeyUp("space") && doubleJump){
      velocety.y = 0f;
      velocety.y += 10f;
      doubleJump = false;
      Debug.Log("DOUBLE JUMP!");
  }

  if(isGrounded){
      velocety.y = 0f;
      canJump = true;
      doubleJump = true;
  } else {
      canJump = false;
      velocety.y += gravity * Time.deltaTime;
  }
```

My Engineering Design Process is at 5(Create) and 6(Test). I'm at the point in my project where I feel confident that I can code the rest of the project if needed. I'm also starting to tweak the values of certain settings to make the player feel smother to control and play. I'm close to finished and the next step I want to work on is the creation of the maps. 

Skills I learned were Embracing failure and Time management. Though I didn't elaborate on it, I had a lot of problems with the jump mechanic. At one point the jump statement would not work at all. I looked for solutions online and checked what others did that worked. However, looking at others ended up complicating the statement even more. Eventually, I came up with a simple solution that worked well with the code I already had. The other thing I learned or found myself doing was managing my time and working on the freedom project. I found myself working on the project every once in a while determined to get certain pieces of code to work. over time I found myself completing a lot of the work after just curiously coding away. 

[Previous](entry03.md) | [Next](entry05.md)

[Home](../README.md)
