## Integration of a Mathematical Calulations with a Chat Completion System using LLM Function-Calling

### AIM:
To design and implement a Python function for calculating the volume of a cylinder, integrate it with a chat completion system utilizing the function-calling feature of a large language model (LLM).

### PROBLEM STATEMENT:
Design and integrate a Python function that calculates the volume of a cylinder, and enable the function to be called through a chat completion system, simulating an LLM interface.

### DESIGN STEPS:

#### STEP 1:Design the Python Function for Volume Calculation
Design the Python Function for Volume Calculation
Where:

(V) is the volume of the cylinder.
(r) is the radius of the base of the cylinder.
(h) is the height of the cylinder.
(\pi) is approximately 3.14159.

#### STEP 2:Create a Chat Completion System
The chat system will:

Take user input as queries.
Detect when the user wants to calculate the volume of a cylinder.
Call the volume calculation function when the user provides the required parameters (radius and height).

#### STEP 3:Integrate the Function with the LLM's Function-Calling Feature
In a system utilizing an LLM with function-calling capabilities:

The function must be defined to be invoked through the LLM interface.
The LLM must be able to extract values for radius and height from the user’s query and pass them to the function
### PROGRAM:
```python
import math
import re

def cylinder_volume(radius, height):
    return math.pi * radius**2 * height

def llm_query_to_function(query):
    if "volume of a cylinder" in query.lower():
        try:
            radius_match = re.search(r"radius\s*([\d.]+)", query, re.IGNORECASE)
            height_match = re.search(r"height\s*([\d.]+)", query, re.IGNORECASE)
            
            if radius_match and height_match:
                radius = float(radius_match.group(1))
                height = float(height_match.group(1))
                volume = cylinder_volume(radius, height)
                return f"The volume of the cylinder with radius {radius} units and height {height} units is {volume:.2f} cubic units."
            else:
                return "Sorry, I couldn't find both radius and height in the query. Please make sure to specify both."
        except ValueError:
            return "Sorry, I couldn't understand the values you provided. Please specify the radius and height clearly."
    else:
        return "I'm sorry, I can only help with calculating cylinder volumes."

if __name__ == "__main__":
    user_query = input("Please enter your query: ")
    response = llm_query_to_function(user_query)
    print(response)
``` 
### OUTPUT:
![image](https://github.com/user-attachments/assets/a56226e0-f106-4a61-b577-3006869bf5bf)


### RESULT:
This approach demonstrates the integration of a simple mathematical calculation (volume of a cylinder) into a chat-based system. The system can detect queries related to the volume of a cylinder and automatically invoke the function to calculate it. By leveraging an LLM’s function-calling capability, dynamic and natural interactions can be made, including processing more complex queries and extracting numerical values from user input.
