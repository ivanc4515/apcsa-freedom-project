# Entry 2
##### 12/18/21

For the past month, I have been working on my APCSA Freedom Project and watching a [guide](https://www.youtube.com/playlist?list=PLPV2KyIb3jR53Jce9hP7G5xC4O9AgnOuL) on where to start. Last time I focused on the Physical aspects of [Unity](https://unity.com). This includes the world and the objects in it. Since then I have simplified the world to only have the ground, player, and 3 objects to interact with. That's great and all but the focus of my work was on the code itself. Unity primarily uses C# as its coding language but when you download Unity it doesn't have a place for you to write code. Instead, you need to download an external program, in my case Visual Studio Code. 

When you first create the new script file(file that contains the code) you will be greeted with a start function and an update function. As suggested by the name, the start function will run the code once when the world is played. the update function is a little different on the other hand. Its job is to constantly run code that will update/affect the world as it is played.

```
using UnityEngine;

public class PlayerMovement : MonoBehaviour{

    // Start is called before the first frame update
    void Start(){
        Debug.Log("hello"); //will print "hello" in the console 
    }

    // Update is called once per frame
    void Update(){
    
    }
}
```

Once I got understood how the script works I started to add the player movement commands into the code. To do this I need to add a force to the Rigidbody component. This component is added onto objects to give them the physics engine. By doing ```Rigidbody.AddForce(x, y, z);``` we can apply a force in any direction. To detect an input I can use ```Input.GetKey(Letter)``` I can find the respective letter and use it to do a certain action. in the following code, I set the movement controls to WASD. 

```
void FixedUpdate(){

        if(Input.GetKey("w")){
            rb.AddForce(0, 0, force);
        }

        if(Input.GetKey("a")){
            rb.AddForce(-force, 0, 0);
        }

        if(Input.GetKey("s")){
            rb.AddForce(0, 0, -force);
        }

        if(Input.GetKey("d")){
            rb.AddForce(force, 0, 0);
        }
    }
```

The Engineering Design Process is a 2 and 3 at the moment. Right now I'm barely scratching the surface and following the video guide as a start. The next steps are for me to implement mouse inputs, in other words how the player will look around. 

Some skills I used are How to learn and Time Management. the videos are a great way for me to get started and make learning the tool a lot simpler than reading pages of documentation. I have been managing my time pretty well and worked on this problem a couple of times a week to get some progress done. 

[Previous](entry01.md) | [Next](entry03.md)

[Home](../README.md)
