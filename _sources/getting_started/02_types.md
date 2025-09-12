# Types in C#
Before we get started with the actual coding, and setting the Unity _scene_ up I'll offer a quick overview of the most important things in C# (C-Sharp, not C-Hashtag).

### Access Modifiers
Firstly, we'll go over _**access modifiers**_, we have _private_, _protected_, and _public_. You've all worked through the Space Rescue, and Deepest Dungeon, and hopefully you now know how different classes work, and Object Oriented Programming, (a key concept in Unity / C#). We'll have different classes / scripts, and these _**access modifiers**_ determine how we can edit these. The main two we'll see are private, and public.

#### Private
A _**private**_ variable,  <span class='red'>cannot be accessed by other scripts</span>. The following code is extremely simple and will be a bit different what base Unity scripts look like, but it should give an idea of how these works.

```{code-block} csharp
:linenos:
//A.cs
public class A
{
    private string word;
}

//B.cs
public class B
{
    private int number; 
}
```

_Class A_ cannot access _Class B_'s number, just as _Class B_ cannot access the value of _Class A_'s word. It simply cannot be done, and if you try, you'll recieve the following error. 
![Error Message](../images/02_01.png)

<span class='red'>Red</span> - Where the error occured. <span class='yellow'>Yellow</span>, - the character, then the line. <span class='lime'>Green</span> - the snippet of code causing the issue. <span class='blue'>Blue</span> - telling us that we cannot access A.word due to protection. 

#### Public
A _**public**_ variable is the opposite of a _**private**_ variable. It can be accessed by any other script. However, that doesn't always mean we want to, especially with multiple developers. I'll talk more about this later on.
```{code-block} csharp
:linenos:
//A.cs
public class A
{
    public string word;
}

//B.cs
public class B
{
    public int number; 
}
```

#### Protected
A _**protected**_ variable is a bit different, but its basically a _**private**_ variable with one key distinction. _**Protected**_ variables are mainly used in **inherited** classes, also thought of as subclasses. Below is a simplified example.

```{code-block} csharp
:linenos:
//AI.cs
public class AI
{
    protected int health;
    private int speed;
}

//Ally.cs
public class Ally : AI
{
    private string name;
}

//Enemy.cs
public class Enemy : AI
{
    private int damage;
}
```

_Class AI_ cannot access _Ally_'s name, or _Enemy_'s damage. _Ally_ cannot access _Enemy_'s damage, and we know the rest. However, the little Ally / Enemy : AI, means _Ally_ and _Enemy_ are **derived** of the _AI_ class, they will have the same variables, and the same functions. _**Protected**_ allows _Ally_ / _Enemy_ to access their own health, yet _**private**_ prevents them from accessing their own speed. You don't really need to know this yet as we'll touch more on that when we talk about **inherited / derived** classes.

### Variable types
This shouldn't be that complex, and very similar to Python. In Python we have a few types, int, string, float, bool, list, and dict. These correspond to whole numbers, words, decimal / whole numbers, true / false, a list of items, and key / value pairs. C# has these basically word for word, and you would define them after the private / protected / public. Here is an example of them all below. The highlighted ones are more complex.

```{code-block} csharp
:linenos:
:emphasize-lines: 11, 12, 14
//Types.cs
public class Types
{
    private int health = 7;
    private string name = "Devourer of Souls"; 
    private float = 10.1f;      // The f is required when designating something as a float
    private ascended_to_godhood = true;

    // We didn't need to set the values of the above, and could have left then as their defaults, usually 0, "", and false.

    private List<Followers> followers = new List<Followers>();      // This line is a bit interesting, we create a List of a type, we chose Followers, a class can be used a type and is a neccesity.
    private Dictionary<string, object> weapons = new Dictionary<string, object>();      // This line creates a dictionary, where the key is always a string, but the value can be an int, float, bool, or anything. It might even be a custom Weapon or Spell class.

    var weapon = weapons["Bane of Mortals"];       // We use var instead of object as we only want weapon to accept a certain type, however that type is only decided when ran. Basically the type of weapon is ambigious until the code is ran.
}

//Follower.cs Just because
public class Follower
{
    private string name;
    private int health;
}
```



