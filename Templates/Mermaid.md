## Flow chart
```mermaid
graph LR
%% comment
	a --- b
	b === c
	d --> |action| b
	e[blabla] ==> c
	f{fun} --> e	
```

```mermaid
graph TD
	a(content)
	b([content])
	c[(content)]
	d((content))
	e>content]
	a --- f{{content}}
	b -.- g[/content/]
	c -.-> h

	classDef white fill:#fff,color:#000
	class a,b,c,d,e white
```

```mermaid
graph LR
	a---|here is text|b
	c-->|more text|d
	
	style c fill:#aa0,color:#000
```

```mermaid
graph TD
	a --> d
	subgraph Graph one
		a --- link
	end
	subgraph Graph two
		c --- d
	end

	click link "obsidian://open?vault=ML&file=Feature%20Scaling"
```

### Orientation
- TD - top down (also TB for top to bottom)
- BT - bottom to top
- RL - right to left
- LR - left to right

### Misc 
thicker lines, use '=' over '-'
## State diagram
```mermaid
stateDiagram-v2
	ts: training set
	la: learning algorithm
	f: f (model)
	ts --> la
	la --> f
	x --> f: feature
	f--> y: prediction
```

## Bar Chart
```mermaid
pie title blabla
	"content" : 7
	"another" : 3
```

## Journey
```mermaid
journey
	title My working day
	section Go to work
		Do thing A: 5: Me
		Do thing B: 7: Cat
	section Go home
		Do thing A again: 2: Me
		Do thing B again: 1: Cat
	section new section
		Do blabla: 8: Me
```
