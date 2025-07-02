# Node-Based-Item-Repair-Design-System
A graph-based system for designing repairable object gameplay.

This system was developed for my Steam game Pieces of the Past, a cozy game about cleaning and repairing antique items in a shop.

![vpet_GIF_reworked](https://github.com/user-attachments/assets/29424e8f-131e-4091-9b49-d02dc2eb2041)

The repair process involves removing and reassembling object parts, but the order isn't linear. Instead, it's a complex dependency graph — pieces must be placed in a specific structure based on what’s already assembled or missing.

I needed a system that could handle this non-linear logic while remaining easy to use. Most importantly, designers should be able to implement it without writing any code.

At first, I created two types of components:

- Piece Component

- Slot Component (invisible parent objects that hold pieces)

When a piece is dragged onto a slot, it snaps to it — if accepted. Each slot checks:

- Is the piece in its accepted list?

- Are all above slots empty?

- Are all below slots filled?

Each Slot component must be manually added to its GameObject, and dependencies must be assigned manually.

![image](https://github.com/user-attachments/assets/743e25e2-8e0b-4a07-b055-ccc9342ecdff)

The Piece component also requires a fallback "space" GameObject, which defines where the piece returns to if it's not placed into a slot.
If a piece starts in a slot at the beginning of a level, that must also be predefined.

![image](https://github.com/user-attachments/assets/03fee4ce-c6c1-40ce-a442-e78c350dc68a)

While functional, this approach was tedious and error-prone, especially for complex objects with many dependencies.

## Final Version (Graph-Based Design)

To simplify setup, I built a node-based editor using the open-source library xNode.

With this system, designers can visually create and connect Slot and Piece nodes.
The graph editor handles the generation of all slot objects, dependency logic, and piece behaviors automatically.

Here’s an example of a graph used in the game:

![image](https://github.com/user-attachments/assets/f71125cb-e381-4bd9-8ab2-260d3351d87d)

The graph uses only two node types: **Slot** and **Piece**.
By connecting nodes in the correct order, designers can easily define complex logic — without ever touching code.

![image](https://github.com/user-attachments/assets/5e5d7d2a-7050-4edc-8f17-519cefab0128)

Note: The code for this project is not publicly available, as it is still a work in progress.
