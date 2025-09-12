# A quick overview of C#

Three main things,
- C# is C-Sharp, don't call it C-Hashtag, or Hashtag C, you will be murdered. 
- C# files are saved as `.cs`.
- Most finished lines of code end with a semicolon `;`. This means you can split a single line of code into multiple lines for formatting.
- Blocks, like classes, if statements, while loops, function definitions, and more end with curly brackets `{ }`.
- And `//` represents a comment and will not be executed.

```{code-block} csharp
:linenos:
//script.cs
class script
{
    bool true_or_false = true;
    Debug.Log("Hello World);

    if(boolean)
    {
        Debug.Log("True");
    }
}
```

The `Debug.Log` is basically Unity's version of a print statement, and comes in three variations, <span class='teal'>Debug.Log</span>, <span class='yellow'>Debug.LogWarning</span>, and <span class='red'>Debug.LogError</span>. These will send messages to one of three tabs in the Console window in Unity.