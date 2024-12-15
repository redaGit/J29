# EDA Workshop 

| Version | 24.12.1 |
| ------- | ------- |

> Join the community on [discord](https://eda.dev/discord)

## Topics:

### Overview

### [Topologies](#topologies-1)
 - TopoNodes
 - TopoLinks
 - Topologies
 - Further Reading [docs.eda.dev](https://docs.eda.dev/user-guide/topologies/) and [documentation.nokia.com](https://documentation.nokia.com/eda/24-12/books/user/topologies.html)
> 🔑 Key Takeaway: The playground operates using the same mechanism that powers digital twin capabilities, enabling you to test and validate any changes before applying them to the physical network.

### [Fabric](#fabric-1)
 - Building Blocks
 - Manual Configuration
 - Template Deployment
 - Further Reading [docs.eda.dev](https://docs.eda.dev/apps/fabric/)
> 🔑 Key Takeaway: The declarative, intent-based approach provided by EDA allows an engineer to validate and implement an entire fabric in less time than it takes an engineer to log into a single switch.

### Queries
 - EQL 
 - Natural Language
 - edactl
 - e9s
 - Further Reading [docs.eda.dev](https://docs.eda.dev/user-guide/queries/) and [documentation.nokia.com](https://documentation.nokia.com/eda/24-12/books/user/queries.html)
> 🔑 Key Takeaway: The EQL allows the entire state of the managed devices to be queried and parsed in real-time providing data for visualization and streaming to external apps. This allows the engineer a view into the managed network as as if it were a single resource.

### Day 1+
 - Digital Twin
 - Custom Dashboards [documentation.nokia.com](https://documentation.nokia.com/eda/24-12/books/user/dashboard-designer.html)
 - Deviations & Remediation
 - Revision Control (Restore/Revert)

### Challenge Yourself
 - ZTP
 - Create Custom Dashboard

---

# Overview

> "In the similar spirit of _reducing the barriers_ that we did with SR Linux, we distribute the free EDA version by publishing EDA components in the public container registry. Leaving you no excuses not to try it :brain:" - Roman Dodin

The workshop will primarily focus on getting familiar with the key concepts in EDA. As such, we are not going to spend a lot of time diving deep into the inner workings of EDA. We hope that participating in this workshop will whet your appetite. Since EDA is free (as in :beer:) to try, you can easily spin up your own installation and get as wild as you want!

**When you are ready to spin up your own playground... [Try EDA!](https://docs.eda.dev/getting-started/try-eda/)**

We will be building our fabric and overlay on top of the base topology that is instantiated when you start the Try EDA! Playground, but you are encouraged to get as creative as your computer resources will allow 💻

# Topologies

The topology is the foundation of the layers of abstraction EDA uses to implement the declared intent of the engineer. It is made up of a number of nodes, interfaces and links. 

The default topology in the playground (and the one we are using) is depicted in this image:

![Playground Topology](images/topology_ss.jpg)

In EDA, the topology is a tree made up of nodes and links. Each *tier* of the tree can contain multiple resources and relationships between *tiers* is drawn based on the links 🌲

The playground topology when depicted in this abstracted way looks like this:

![Playground Topology Abstraction](images/toponodes_and_topolinks_ss.jpg)

You may have noticed that the abstraction image refers to the nodes as TopoNodes and the links as TopoLinks. In EDA, a leaf or spine switch would be a TopoNode and the circuit between the leaf and spine would be a TopoLink.

![EDA UI](images/topology_pane.jpg)

## :rocket: Activity 

Based on the image above:

1. Click this dropdown to choose the `eda` namespace
2. Click `Main`
3. Click `Topologies`
4. Click the `i` to open this information screen
5. Click `leaf1` to be able to see all of the information about the node, take a moment to look at all of the available information about this node.

Next, look through the options on the left side of the screen to find `Nodes` in the `Targets` subsection.

1. You will see a list of the three nodes in our topology [ spine, leaf1, leaf2 ]
2. Click on the three vertical dots on the far right-hand side of one of the nodes.
3. Click `Node Configuration` to see the full configuration of the node as it is currently deployed. You will be able to come back to look at this after other steps to be able to see how the configuration changes as you build out the fabric. Close this view when you are done.
4. Now click `Configuration View` from the three vertical dots. This is where the various options were set for this node.
5. Click `Edit` in the bottom right corner of the `Configuration View` and notice the yaml pane - you can make changes to the yaml or the gui in this screen and they will update eachother. Change `operatingSystem` to `sros` and notice that the other side also changes. Click cancel in the lower left corner or the X in the upper right when you are done here, and then click OK.

The `Links` and `Interfaces` sections are further down the left side in the `Topology` section. Spend some time to see what you can find in these.

## 🏆 Going Deeper

Topologies can be built manually, but it is far more common to generate the topology files using one of the methods described in the [docs.eda.dev](https://docs.eda.dev/user-guide/topologies/#topology-file)

To challenge yourself, draw your topology on a napkin and then use the tools to generate your topology in EDA to match your drawing.

[^ back to top](#topologies)
---

# Fabric


