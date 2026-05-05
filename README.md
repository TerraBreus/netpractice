*This project has been created as part of the 42 curriculum by zivanov.*

# NetPractice
As an attempt at gamification, NetPractice is a set of ten puzzles teaching you the very (very) basics of how computers communicate with each other in the context of a (sub)network. This project introduces you to concepts such as; gateways, masking, IP's, routers, switches and routing tables.

## Description
(_for the eval sheet nerds_)
-  **Present the topic:** NetPractice is a simple 42 project teaching you a few ICT concepts to work with (sub)networking. Aka; how computers communicate with each other (Hint: ICT stands for Information and **Communication** Technology).
-  **Goal of the project:** Complete the ten given puzzles and upload the ten required corresponding configs. During the evaluation of the project, three "advanced" puzzles must be solved on the spot under the time limit of fifteen minutes.
-  **Brief overview of the project:** NetPractice is a set of ten puzzles teaching you the very (very) basics of how computers communicate with each other in the context of a (sub)network.

## ToC
-  [Instructions.](#instructions)
-  [Resources.](#resources)
-  [Explanations.](#explanations)

# Instructions.
From 42's intranet, the server files required for NetPractice can be downloaded from the corresponding project page. For me, this file is called `net_practice.1.9.tgz`.

First we must extract the `.tgz` file to see what is inside.
```
tar xfv net_practice.1.9.tgz
```
If all goes correct, you now have a `net_practice` folder. Let's enter it and run the server.
```
cd net_practice
bash run.sh
```
Your browser of choice should now open a new page with the url set to something as `http://localhost:49152/`. Login using your intraname (f.e `zivanov`) under the `Training` tab and press the `start!` button. 

You shall be given the first puzzle. Once completed you are allowed to the next stage. Make sure to download your config file for Moulinette to check once you upload your repo to the vogsphere. You can do this by pressing the `Get My Config` button next to the `Check Again` button. Do this for every level!

**Tip:** Pressing the Check Again button updates a log file in the bottom right corner. This is very useful for solving the puzzle when things go wrong even though you expect them to be right.

**NB:** 10 exported configuration files (one per level) must be placed at the repository root. If you don't know how to download the configuration files; reread the instructions. 

# Resources.
### **Crash Course on Computer Science:**
Technically this stuff doesn't help you solve the NetPractice puzzles, but I believe it is what they wanted to teach you underneath. It is a thousand times more useful when trying to understand InterComputorNetworkCommunication.
   - [Episode 30: Computer Networks](https://www.youtube.com/watch?v=3QhU9jd03a0)
   - [Episode 31: The Internet](https://www.youtube.com/watch?v=AEaKrq3SpW8)
   - [Episode 32: World Wide Web](https://www.youtube.com/watch?v=guvsH5OFizE)
### The Log.
NetPractice gives you a log. This log is useful. Use it.

Often times it tells you where a package fails to continue travelling further, showing you where the problem lies.

### **Artificial Intelligence:**
ICT Networking is pretty much analogue to how postal delivery services work. Asking AI for a metaphore on how computer networking works quickly gives you an understanding on how networks are setup. Here is a simple example using the `Gemini 3 Flash` model.
```
Explain to me how (sub) networks work in the context of ICT.
Form it into a metaphor of a delivery system.
Make sure to explain topics such as routers, switches, routing tables, destination and next hops.
```
---

#### AI SLOP INCOMING!!!!
Thinking of a computer network as a massive **Global Delivery Service** is a perfect way to visualize how data moves. To understand subnets, imagine a massive city divided into specific neighborhoods.

## 1. The Neighborhood (The Subnet)
In a massive city (the Internet), a **Subnet** is a gated community or a specific neighborhood. 
*   **The Logic:** Without neighborhoods, a delivery driver would have to search every single house in the city to find "123 Maple St." 
*   **The Subnet:** By grouping houses into a sub-network, we limit the "noise." Only the mail intended for your specific neighborhood enters the gate.


## 2. The Internal Courier (The Switch)
Inside your gated neighborhood, you have a **Switch**. 
*   **The Role:** The switch is like a local courier who knows every house in the neighborhood by its specific physical address (MAC address). 
*   **The Process:** If House A wants to send a package to House B in the same neighborhood, the Switch handles it instantly. It doesn't need a map of the whole world; it just knows who lives behind which door in its small zone.



## 3. The Neighborhood Post Office (The Router)
The **Router** sits at the entrance of the neighborhood. It is the only device that connects your local streets to the massive highway system outside.
*   **The Role:** It acts as the gateway. If you try to send a letter to a different city, the Switch realizes, "This isn't for anyone here," and hands it to the Router.



## 4. The Logbook (The Routing Table)
Every Router carries a **Routing Table**. Think of this as a "Master Logistics Logbook." 
*   It doesn't list every single house in the world (that would be a billion-page book). 
*   Instead, it lists **Destinations** (other neighborhoods) and the **Next Hop** (the next post office on the highway).

| Destination (Neighborhood) | Next Hop (Which Highway Exit?) |
| :--- | :--- |
| London District | Highway 101, North |
| Tokyo District | International Shipping Port |
| Local Neighborhood | Deliver Directly |





## 5. The Journey (Destination and Next Hop)
When a package (a data packet) leaves your house for a destination across the world:

1.  **Destination:** This is the final address written on the package (the IP address).
2.  **Next Hop:** Your local Router looks at the Destination, checks its Logbook, and realizes it doesn't have a direct road to the final house. However, it knows the "Next Hop"—another larger sorting facility three towns over. 
3.  **The Relay:** The package is passed from "Hop" to "Hop" (Router to Router). Each Post Office along the way only needs to know which direction to kick the package next to get it closer to the final neighborhood.



## Summary Table

| ICT Term | Delivery Metaphor |
| :--- | :--- |
| **IP Address** | The mailing address on the envelope. |
| **Subnet** | A specific neighborhood or zip code area. |
| **Switch** | The local courier who moves mail between neighbors. |
| **Router** | The Post Office at the edge of town connecting to highways. |
| **Routing Table** | The GPS/Logbook telling the Post Office which highway leads where. |
| **Next Hop** | The next sorting facility the package must reach to get closer. |

---

# Explanations.
Again, not necessary per the subject's requirement but some say active recalling is the best way of learning.

- IP adress
    Oversimplified, an IP adress is a location within a network. Think of it as a housenumber in a street. The number alone does not say much, but within a network it suddenly becomes useful.
    
    To complicate things a little an IP adress usually contains a network ID and a host ID. But for that we need to know what masks are.

- (sub)Network
    A network is a collection of digital devices communicating with each other. Within a Network, we can have smaller networks called sub-networks. Think of it as roads connecting houses. A street is a (sub)network just as a city is a network. 

- Masks
    A mask allows us for the whole package. In reality it is a 32bit number used to differentiate the network ID from the host ID. If this sounds difficult, don't worry. It is. 

    IP ADRESS

    `192.168.2.4`

    MASK

    `255.255.0.0`

    Basically says that the first two numbers cannot be changed; they are part of the network. The two zero's in the mask tell us that the two final numbers in the IP adress can have all 255 values. That means that this network has 255^2 different possible host ID's. Still difficult? Don't worry. It is.

- Packet
    A packet is a bit of digital information that is send through a network in order to communicate. It contains a payload and a header. If we see this as an oldschool mail, the payload is the content and the header is the adress written on the mail for all to see.

- Switch
    A switch allows multiple computers to be hooked up to the same network. It is analogue to a crossroad. Instead of needing individual connections between every digital device, you can pass them to a switch. That switch will then keep track of every devices that is connected to it and send the packet to the right device (by checking the MAC adress (nvm) and the host ID).

- Router
    This is a little more tricky. Routers allow for different networks to communicate with each other. If you think of it in terms of roads, where switches are the crossroads between streets, routers are the highways between cities. Routers work with routing tables. These are a list of places where the packets (of digital information) can go in order to reach their destination.
- Destination
    Every packet send from a digital device is meant for another specific digital device. The IP adress of the receiving digital device is called to be the destination of the packet.
- Next Hop
    Routing tables have Next hops. This simply means where the packet needs to go next in order to reach their final destination.
- 0.0.0.0/0
    Every routing table could use a default gateway. If it does not know the next hop for a specific destination, it sends it to the next hop of the default gateway.
