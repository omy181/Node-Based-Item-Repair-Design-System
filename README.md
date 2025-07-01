# Node-Based-Item-Repair-Design-System
A graph-based system for designing repairable object gameplay.

This system was developed for my Steam game Pieces of the Past, a cozy game about cleaning and repairing antique items in a shop.

![vpet_GIF_reworked](https://github.com/user-attachments/assets/29424e8f-131e-4091-9b49-d02dc2eb2041)

The repairing consists of taking out and putting back pieces together and these pieces's putting order is not linear it is more like a big graph with complex dependencies. So i had to come up with a solution for making these designs functional.

The repair process involves removing and reassembling object parts. However, the assembly order isn’t linear — it forms a complex dependency graph. I needed a system to make designing and managing this logic intuitive and functional.

Initially, I created two types of components:

- One for pieces

- One for slots (invisible parent objects that hold pieces)

When a piece is dragged onto a slot, it snaps to that slot — if the slot accepts it. The slot checks:

- Is the piece in the accepted pieces list?

- Are all above slots empty?

- Are all below slots filled?

Each Slot component must be manually added to slot GameObjects, with dependencies manually assigned.

![image](https://github.com/user-attachments/assets/743e25e2-8e0b-4a07-b055-ccc9342ecdff)

This is the Piece component. A space GameObject is assigned to define its fallback position (when not placed in a slot). If a piece starts in a slot, that must be predefined.

![image](https://github.com/user-attachments/assets/03fee4ce-c6c1-40ce-a442-e78c350dc68a)

While this first version worked, manually creating slot objects and linking dependencies was tedious.
To streamline the process, I built a node-based editor using the open-source library xNode.

With it, designers can create Slot and Piece nodes, then simply connect them to define logic visually.

Here’s an example graph used in-game:

![image](https://github.com/user-attachments/assets/f71125cb-e381-4bd9-8ab2-260d3351d87d)

The graph is composed of only two node types: Slot and Piece.

![image](https://github.com/user-attachments/assets/5e5d7d2a-7050-4edc-8f17-519cefab0128)
