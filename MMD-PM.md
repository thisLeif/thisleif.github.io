## Project Management Flow Charts using Mermaid


### Mermaid Markdown, Visualization via JavaScript
> Source: [Mermaid.JS.Org](https://mermaid.js.org/syntax/flowchart.html)  

```mermaid
---
title: Mermaid Flow Chart Basics
---
flowchart TD
    subgraph un[Node name only]
        direction LR
        firstNode 
        --> 
        |"nodeA --> nodeB"
        | secondNode
    end

    subgraph doux[Text In Connector]
        direction LR
        nodeA 
        -->  
        |"nodeA 
        --> 
        |Text
        | nodeB"
        | nodeB
    end

    subgraph troix[Connect after declared]
        direction LR
        fifthNode[nodeA]
        sixthNode[nodeB]
        fifthNode
        -->
        |"""
            nodeA
            nodeB
            nodeA --> nodeB
        """
        |sixthNode
    end

    subgraph quatre[Name and description]
        direction LR
        thirdN[*Italics* **Bold** 
        <u>Underline</u>]
        -->
        |"""nodeA[
        *Italics: 1 asterisk* 
        **Bold: 2 asterisks** 
        <u>Underline: HTML tags</u>] 
        --> 
        nodeB[First Line
        Second Line]"""
        |fourthN["""
        First Line
        Second Line"""]
    end

    subgraph cinque[Vary Lines, Styles, Shapes]
        direction LR
        shapeOne(("((circle))"))
        shapeTwo(["([oval])"])
        shapeOne
        -.->
        |"""
            nodeA((circle))
            nodeB([oval])
            nodeA -.-> nodeB
        """|shapeTwo

        shape3{"{diamond}"}
        shape4[("[(cylinder)]")]
        shape3
        ~~~
        |"
            nodeA{diamond}
            nodeB[(cylinder)]
            nodeA ~~~ nodeB
        "
        |shape4

        classDef bluFill fill:#00f;
        classDef bluTxt color:#00f;
        shp5[whtOnBlu]
        o--o
        |"""
        style shp5 color:#fff
        style shp6 fill:#fff
        classDef bluFill fill:#00f;
        classDef bluTxt color:#00f;
        shp5[whtOnBlu]
        o--o
        shp6[bluOnWht]:::bluTxt
        class shp5 bluFill;
        classDef str stroke:#f00;
        class shp5,shp6 str
        """
        |shp6[bluOnWht]:::bluTxt
        class shp5 bluFill;
        classDef str stroke:#f00;
        class shp5,shp6 str
        style shp5 color:#fff
        style shp6 fill:#fff
    end

    un-->doux-->troix-->quatre-->cinque
```

### Project Management Flow Charts, Visualizing Workflows  
