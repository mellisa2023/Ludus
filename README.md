# Ludus
Ludus: A Hybrid Storytelling Language for Authors, Creators, Game Writers, and Playwriters by Crystal Evans, A Jamaican author and web3 enthusiast. 
# Ludus

**A Hybrid Storytelling Language for Authors, Creators, Game Writers, and AI Tools**

Ludus is a narrative-focused, hybrid scripting language designed for:

- **Authors and storytellers** who want to build branching, emotionally rich stories  
- **Content creators** designing frameworks for interactive books, podcasts, or blogs  
- **Game developers** building dialogue systems and branching plots  
- **Screenwriters and playwrights** who want to prototype story structures  
- **AI enthusiasts** integrating large language models (LLMs) like GPT or Gemini to expand narrations  
- **Python and JavaScript developers** who want to parse and manipulate stories programmatically

---

##  What Ludus Does

 Uses a natural-language–inspired syntax  
 Supports structured yet human-readable story writing  
 Exports to JSON for data-driven tools or visualization  
Plays well with LLMs to turn narrate sections into rich prose  
Empowers creative workflows while giving technical teams a structured framework

---

##  Features

- **Character declarations** with traits and states  
- **Scene definitions** with narrative blocks  
- **Branching choices** using clear, readable options  
- **Emotion tracking** (`shows` / `loses`) with cause-and-effect  
- **Smooth transitions** between scenes with embedded narration  
- **JSON export** for feeding into games, visual novels, or other interactive systems  
- **LLM-friendly** design to expand Ludus scripts into fully fleshed-out text

---

## Project Structure

```plaintext
LudusLanguage/
  ├── ludus.py               # Python interpreter
  ├── Refined_Ludus_EBNF.pdf # Formal Ludus grammar
  ├── examples/              # Sample Ludus scripts
  └── README.md              # This file

Ludus is in early development. If you’d like to contribute, please open an issue or a pull request — collaboration is welcome!



# Ludus Complex Conditions

By default, Ludus supports simple conditions, like:

```plaintext
option "Option text" if CharacterName.trust > 5:
    ...
However, more advanced logic can be handled with complex conditions using:

and

or

grouping with parentheses

Example Complex Conditions
plaintext
Copy
Edit
option "Follow the hidden trail" if (Amara.trust > 5 and "map" in Amara.inventory) or Amara.traits includes "brave":
    narrate: "Amara studied the map and felt bold enough to take the shortcut."
    transition to "Secret Path" with:
        narrate: "She pushed aside thick ferns and stepped into a hidden clearing."
Rules
Combine multiple checks with and and or

Use parentheses to group conditions for clarity

Support string inclusion:

"item" in CharacterName.inventory

CharacterName.traits includes "brave"

EBNF Extension
ebnf
Copy
Edit
condition   = simple_condition , { logic_operator , simple_condition } ;
simple_condition = identifier , "." , identifier , comparator , value
                | '"' , string , '"' , "in" , identifier , "." , identifier
                | identifier , "." , identifier , "includes" , string ;
logic_operator  = "and" | "or" ;
Interpreter Support Sketch
In Python, you might parse the condition as a string, then safely evaluate it. One simple approach could be to build a dictionary of story state and then:

python
Copy
Edit
if eval(condition_string, {}, story_state):
    # allow option
Full Ludus Example
plaintext
Copy
Edit
Choice:
    option "Trust the wolf" if Amara.trust > 5 and Amara.feelings == "curious":
        narrate: "Amara chose to believe the wolf's strange but calm eyes."
        transition to "Wolf's Lair" with:
            narrate: "They disappeared together into the dark forest."

    option "Run away" if Amara.trust <= 5 or "map" in Amara.inventory:
        narrate: "Amara refused to risk betrayal again."
        transition to "Safe Path" with:
            narrate: "She ran along a route she knew by heart."
