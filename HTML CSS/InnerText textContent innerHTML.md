[medium article](https://medium.com/@stevriss22/differences-between-innertext-textcontent-innerhtml-23268b2ac7b2)

**.innerText**

> If the user needs to grab the rendered inner text content, it is best to use ‘.innerText’. In other words, if a user wants to return text with CSS attributes(such as bolding, italics, etc.) and the same spacing as the node ‘.innerText’ is the way to go. In most cases when we are grabbing the inner text content of a node they want to bring its attributes with it, so this is the best route.


**.textContent**

> This property returns the inner text content of **all** children of the node it is called on. It ignores styling and is only looking for the non-rendered text content of the nodes. If a parent node has 400 child nodes and the ‘.textContent’ property is called on the parent node, the inner text content of ALL 400 child nodes will be displayed.


**.innerHTML**
> This property is the easiest to differentiate from the other two. ‘.innerHTML’, like ‘.textContent’, returns the inner text content of **all** child nodes. The difference is that ‘.innerHTML’ returns the non-rendered text content **as well as** the HTML tags of the child nodes.

