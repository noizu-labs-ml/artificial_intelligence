# artificial_intelligence
Library for experimentation with novel/alternative AI configuration and re-usability. 


# TODO, 
1. Formalize below rambling into library components and diagrams before beginning implementation. 
2. Elixir - Neural model. 

# Word Stream	
Random unedited musing, on the off chance I am every proven right on any of these, or to just sound like the time cube dude in the short term. 

I suspect current generation deep learning models leave out a few very critical aspects of actual brain structures that limit of their ability to solve certain types of problems. 

1. Axion signalling thresholds are not static. The presence of neurochemicals and time since last firing impact the threshold that determines if a neuron will fire or not. 

1.a Setting different neurons to respond to the same neurochemical signal in different ways, I postulate, would let one prime the same network to produce different outputs based on current state. Chemical indicators of anxiety or fear for example, or inattention, could feedback into the system to prime it for false positives. E.g. when signals are present stating the entity is inattentive, you can (coupled with the item below) modify threshold rates to increase the likely hood that you interpret raw data as something dangerous. You see a water hose laying on top of some leaves with some black spots on them. You travel down the neural network with this data and hit the part that determines if it sees a snake or not. The input there doesn't read out snake but it's a close miss and you have input saying you are being inattentive so you push a fear signal up the network that lowers the threshold for "seeing" a snake with two black beady eyes. (increases the likely hood upper layers signal specific shapes by tweaking their trigger thresholds and inputs). Suddenly gasp you see a snake and pump out endorphins. But, because the current trigger threshold is a function of last firing and passage of time time, eventually the increased weighting that incorrectly pushed you to hallucinate a snake are reduced until you realize it's just a garden hose, and endorphins return to normal. 

1.b. Similarly I suspect incorporating the decaying threshold behavior for triggering axons is going to be absolutely critical to being able to produce a compact neural network that can incorporate the passage of time and causality in it's conclusions. This is because the decay function of the previous input forces an arrow of time on the calculation, and encodes previous state into the current calculation. A simple example of what this would look like in practice is motion blur. e.g. in a very a simple model because the threshold to fire after a threshold is met is lowered you see a ghost image leading from original position to current position. Which can then be incorporated in deeper layers to calculation motion, speed, etc. 

I would also postulate that allowing different paths in the neural network to operate with different decay rates allows for the network to split processing into immediate executive control and more subconscious/background processing. 

For example you meet an interesting stranger, they seem polite, familiar (as in not immediately strange or alarming), are well dressed and take an active interest in you. So your brain sends off short term signals for all clear and you engage. Meanwhile incoming signals that aren't strong enough to immediately override begin to pop up. The signals aren't strong enough to override the initial all clear signal you associate with the person but they continue to accumulate as more data comes in until eventually all of these slow burn signals hit a threshold (or gradually) trigger something that forces your conscious to reevaluate the situation and change your threat assessment. e.g. background processing running off of the same input that drives your initial categorization. that eventually adjusts your conscious categorization as new data or past experiences are pulled up and fed into your situational model. 

2. Current neural networks run top down through multiple layers. Organic brains contain neurons with incredibly long axion that can push feedback to neurons higher up in the chain. (or connect disparate systems.) E.g. you can trigger a node and someone will think of johny depp. 

Providing feedback plus decay over time from 1.a and 1.b above allows for a much more compact system. It also lets you dynamically tune your inputs to identify if a specific input has been observed. 

For example of what this might look like in practice. Consider our propensity to look at a building with two windows, an overhange, front door, and decide the windows look an awful lot like two eyes. The overhang like a nose and the door like a mouth, and once we see it it's hard to revert back to just seeing a simple house. 

A possible way to encode this in a network (although unlikely not how our brain would do it). is something like the following.

i. Your brain identifies two windows, an overhang and a door. 

ii. You travel through the neural network to the point where you notice two thingies, with a thing below them and then another thingy below it which fires a "this might be a face neuron" 

iii. At this point you can either overlay new information on the image and some how share it across all systems which means pushing around a lot of data or you could push a signal back up the stream to prime it to overlay gestalt lines if possible that that make the image appear more like a face. 

iv. because there were enough visual elements available that could be constructed into a face like thing an refined images flows in and the neurons are primed to identify those features. 

v. now we go from this might be a face to a this looks like a face neuron which suddenly triggers neurons related to hey it's a face. (humor, tendency to anthropomorphize, etc.). and these in turn sent out other signals possibly even ones back up the visual processing layers to for example send "it's safe signals" that reduce you're likely hood of suddenly interpreting a garden hose as a snake etc. 

The trick here is that pushing the feedback up the system locks the network into seeing or not seeing a face, rather than being able to see multiple overlapping possible constructs. Which is similar to how observe images such as this. It's very difficult to visualize when looking at certain optical illusions such as the young woman/old woman both images at the same time. Which insinuates instead of processing both in parallel and pushing the information upstream, a feedback mechanism actually primes you toward one or the other and that data than travels further down the neural network. 

3. Working rudimentary memory, and reusable modular networks. 

So keeping in mind of the concepts from 1. & 2. and a large amount of computing power plus some caveats it should be possible to train modular deep networks, that can be dropped into existing solutions and capable of altering behavior/focus based on upstream signals, with minimal additional training, and without the need to alter the training on the core module. The training process however becomes much more involved. 

The approach I would propose here is to, 

Stage 1
1. Prepare a deep network in the usual manner. 
2. Define output sections. (These nodes must contain the make of the car in the image I am viewing) (those nodes must encode the color of the car, etc.). 
a. Break the output layer into regions that must contain specific data in it’s entirety.
b. Train neural networks against those regions to answer or show specific data. Use these split off networks to reinforce learning. 
c. Once the network is sufficiently trained such that each of the split off networks correctly interprets the data to a sufficient degree re run the network and record the output of all of the split off networks and the intermediate layer they split from 
d. Repeat, breaking up large sub layers into smaller sections that can organize machine data into specific segments that can be routed to other components. 

An example, 

Let us say we wanted a deep learning program that can look at a picture, describe what it is viewing, ask questions about it and recreate it as a painting. 

So our first step is to train a program to do exactly this. Or find a large enough data set for validation for the trickier steps to come. Aka our validation method. 

Once we have our validation method we begin deciding where we want to cleave the network to control where specific information should be output. For example we might setup our network so that the first 32 nodes on the 10th layer are sperate from the other intermediate output nodes. And that these nodes must include the subject of the picture, It’s color, it’s size etc. we don’t care how the data is encoded only that these 32 nodes contain all of this information somehow. 

We then add on additional (and separate) networks that can read these values and are trained to output the attribute in question. We can train individual networks for each question or design one network that can answer them all. 

One network only knows how to extract the subject. One only knows how to extract the color, etc. We train this new intermediate network against our input data set and our traditional deep learning network until our sub network correctly outputs what they see as efficiently as the previous network. 

Now we add a shim layer that can distort the output so that color is misreported, etc. without impacting other values, 

Next we compress the 32 nodes (or 32 nodes modified by the shim) to these specific inputs and refeed our full 32 nodes plus these new inputs plus rest of the specific layer and proceed to segment off in a lower level a new layer that validates that given specific inputs the network can correctly describe the scene or draw the scene _and_ include the addended inputs as part of our validation logic to force the network to override it’s internal state with any overridden state. 

So now at each of these layers we feed in data from above and transform it into output we can add an alteration shim that lets a third party override behavior/change preferences/weighting for the final outcome. By training a new network to take those 32 nodes plus the remainder at that level (or another layer) plus input nodes from down stream and produce a modified 32 node output that has been verified to change behavior in layers below the one those interstitial outputs are grabbed from. 

We could for example explicitly define horizontal and vertical lines are output in a format that can be converted to bit images at a certain level. And then fed back into data processing. As one of the inputs layer to a section of trained nodes. 

The more we push to make sure certain data is available within certain subsets of layers the more flexibility we have to alter how the program executes without retraining the full path. And the more we gain the ability inject altered behavior by inserting shim layers that include inputs from other subsystems that would wish to alter this specific subsystem in some way. 

Further, if we wished to implement a very crude sort of memory like behavior we can take all of the digested values (like the subject of the picture and it’s color) and set a neural network that trains itself against those inputs to produce an output based on the current output which is then back fed into other nodes or the shim layers. So for example lets say a traumatic or noteworthy event is recorded that resulted in some major change in internal state of the simulated entity. Like being chased or finding a nice virtual meal, etc. Although the plumbing is a bit difficult we take all of the current inputs and back propagate a memory neural net so that given those current inputs we get high level summary node outputs similar to the current summary outputs, or some representation there of, and that input is then fed into shim layers to alter/enhance the final outcome. (with some trickiness around the decay of axion firing to allow a memory to fire and then alter functioning while recent). 

So with an god awful amount of time and computation power we can construct a library of trained networks that output information at different layers that can be interpreted/summarized with other networks, we can color the final outcome by training custom shim layers that take known inputs and other factors to alter what the actual perceived output is, and we can jury rig a poor mans sort of memory/learning behavior. Allowing us, assuming it’s feasible. To build up layers on top of layers over time that can understand the output of other layers and provide hints / direction to control how lower layers interpret their inputs. Which could eventually get you something close to a more general intelligence or at least a plug and play intelligence. (add the ability to spot red crested swallows to your binoculars. For only $5.99
