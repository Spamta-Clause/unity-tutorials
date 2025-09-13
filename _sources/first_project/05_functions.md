# Key Unity Functions
Now we are going to go over the main functions in Unity, you'll have some of these in every single script pretty much. 

Firstly we have `Awake() { }`, this is ran when the object is first loaded, next we have `Start() { }`, ran after all Awakes are done, even the ones on other objects! Next, we have our Updates, `Update() { }` is ran every single frame, and `FixedUpdate() { }` is ran 60 times per second, provided your computer can handle it. Below is some code that is mostly functional.

```{code-block} csharp
:linenos:
:emphasize-lines: 35
//A.cs
public class A : MonoBehaviour //MonoBehaviour is basically our fundamental base class for every Unity script, as it sets up some key variables.
{
    public int value_one;
    public int value_two;
    
    void Awake()
    {
        value_one = 1;
    }

    void Start()
    {
        value_two = 2;
    }

    void Update()
    {
        value_one += 1;
    }

    void FixedUpdate()
    {
        value_two += 2;
    }
}

//B.cs
public class B : MonoBehaviour
{
    void Start()
    {
        var A = FindObjectOfType<A>().GetComponent<A>(); //Finds the first object that has the script A on it. Then finds A on that object.
        Debug.Log(A.value_one);
        Debug.Log(A.value_two);
    }
}
```

This code should work, `value_one` would be printed as 1, and `value_two` would be printed as 2. `value_one` will also be 238, or 7, or 94, after one second, or any other number. `value_two` will be 122. This code is horrible though, specifically because of the suspicously highlighted line. Why you ask? Well what if we had a lot more in A's Start function before we define the value of `value_two`? What will happen is B's Start function will log `value_two` before A's Start function defines the value of `value_two` and will log it as 0. This will never occur with `value_one` as B's Start function will only run once A, and everyone else's Awake functions are done. Basically, setup references to other scripts in Awake, or define values, but never try and get values and just use Start for that.
