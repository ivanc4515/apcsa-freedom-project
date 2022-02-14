# Entry 3
##### 2/13/22

My goal last time was to implement a mouse movement in my character. This was to allow the mouse to control where the player looks. I was able to do this by following along with [videos](https://www.youtube.com/channel/UCYbK_tjZ2OrIZFBvU6CCMiA). On top of the videos, I used [Unity's Documentation](https://docs.unity3d.com/Manual/index.html) to see the limitations of the code I was typing. The mouse input is thankfully already built into unity. So instead of using an if statement to detect if the mouse moves unity already tracks the position of the mouse on the screen. The way you get the position of the mouse is using the line: 
```
float mouseX = Input.GetAxis("Mouse X") * mouseSensetivity * Time.deltaTime;
//float - variable
//Input.GetAxis() - gets the data from unity
//Time.deltaTime - makes the character move based on the time instead of how may frames your computer displays
```
This line works for both x and y positions. Then in order to move the camera/player we need to change its rotation. For the y coordinates, the player can look as much to the left or right as they want. However, the x coordinates cant because we don't want the character to be able to look all the way behind them. So we implement a clamp on it which limits how high or low the number can go.
```
xRotation -= mouseY;
xRotation = Mathf.Clamp(xRotation, -90f, 90f);
```
One thing I also worked on was the movement system. I did work on one in the last blog but I found out the way I coded it was flawed. In the past, the movement controls I wrote utilized `.AddForce`, this doesn't move the player but instead pushes them. This difference was important because by pushing the character the player could slide or topple over. The new movement control I added uses a similar input method as the mouse control. 
```
//Old Movement
if(Input.GetKey("w")){
  rb.AddForce(0, 0, force);
}

//New Movement
float x = Input.GetAxis("Horizontal");
float z = Input.GetAxis("Vertical");
Vector3 move = transform.right * x + transform.forward * z;
control.Move(move * speed * Time.deltaTime);
```
My Engineering Design Process is at 4(Plan) and 5(Create). I'm starting to plan out the things ai need and will convert the things I've been coding to the final product. The next thing I want to do is work on the things I can do as a player. Right now The player can only walk and look around. I'm planning on creating a terrain that then can traverse and maybe work on some unique movement controls. 

Skills I learned were Embracing failure and Attention to detail. The failure I encountered was when I was changing the old movement system with the new one. I realized that the old one was really simple and was not going to be able to do the things that I had envisioned. Attention to detail also relates to the new movement system. Since I had opted to use the improved system it was a lot more complex than the old one. This new one used a lot of variables and methods with specific cases sensitive methods. 

[Previous](entry02.md) | [Next](entry04.md)

[Home](../README.md)
