---
Capstone Project Rubric: 


RESEARCH
Description of final project choice, why chosen, and what a successful project would do:

My final project is a smart stool that combines making a stool with basic electronics. I chose this project because it allowed me to work with both physical components and electronics, which interested me more than doing only one or the other. I wanted to create something functional and interactive rather than just decorative, but at the same time I did not want to make something so hard because of my lack of experience in engineering. 

A successful version of this project: 

It will function as a normal stool but also include a pressure sensor that detects when someone sits down. When pressure is applied, LED lights embedded in the stool will turn on, creating a visual response to the user. The electronics will be hidden underneath the stool so the design looks clean and intentional, with only the light visible. If completed successfully, the stool will be sturdy, visually appealing, and reliably respond to pressure.

Attribution of project serving as inspiration (author/maker and source):
Attribution of project serving as inspiration (author/maker and source):

This project is inspired by me searching on youtube for electronic ideas and sources that could be interesting to make into a final project that is also doable. Descriptions of the youtube videos are below and these include some of my inspirations for the electronic portions. For the wood portions some of the videos are also below, because I knew I wanted to include some woodworking so I looked for videos on that.

Sources:

<div class="video-sources">
	<h3>How to Use a Force Sensor with an Arduino (Lesson #23)</h3>
	<div class="video-embed">
		<iframe width="560" height="315" src="https://www.youtube.com/embed/r7oWtcE6QQc" title="How to Use a Force Sensor with an Arduino (Lesson #23)" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
		<p><a href="https://www.youtube.com/watch?v=r7oWtcE6QQc">Watch on YouTube</a></p>
	</div>

	<h3>Force Pressure Sensor with Arduino LED Indicator</h3>
	<div class="video-embed">
		<iframe width="560" height="315" src="https://www.youtube.com/embed/ZlXglJ1keIc" title="Force Pressure Sensor with Arduino LED Indicator" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
		<p><a href="https://www.youtube.com/watch?v=ZlXglJ1keIc">Watch on YouTube</a></p>
	</div>

	<h3>Making A $3 bar stool from a 2x4 | woodworking | diy gift ideas</h3>
	<div class="video-embed">
		<iframe width="560" height="315" src="https://www.youtube.com/embed/GsAb9DXlk-4" title="Making A $3 bar stool from a 2x4 | woodworking | diy gift ideas" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
		<p><a href="https://www.youtube.com/watch?v=GsAb9DXlk-4">Watch on YouTube</a></p>
	</div>
</div>

Description of how project is different than these sources that I got my inspiration from:

Unlike the electronics focused videos only or the woodworking focused video that focuses only on electronics or only on furniture design, my project combines building furniture with embedded electronics. Instead of attaching LEDs externally or making a small prototype, I am building a full-size stool with electronics fully hidden inside. I also designed my own stool dimensions and structure rather than copying an existing furniture plan. This makes my project more personalized and fabrication-focused than the videos that only include one small portion of engineering that I watched to get inspiration for my own project.



Design Specification Considerations
When designing my stool, I considered:

Size and scale so it can support a person safely(200+ lbs because that is what I weigh)
base diameter is 22.5 inches with wood that has a radius of .75+ inches and 18-20 inch legs 

Material choice, starting with cardboard prototypes before moving to wood

Placement of electronics so they are hidden and protected(under the bottom of the stool)

Ease of assembly and maintenance in case electronics need adjustment

Visual simplicity, ensuring the LEDs enhance the design rather than distract from it

These considerations have guided my physical design and they will guide my electronics layout when I complete it second semester.

INSTRUCTIONS
Final materials list including costs
Cardboard (for prototyping)- at Latin

Wood (final stool structure)- At Latin

Arduino microcontroller- at Latin

Pressure sensor- will order with mr dubick in January- according to research should be 30/40 dollars

LEDs- at Latin(10/15 dollars)

Resistors- at latin

PCB board- at Latin

Wires- at Latin

Power source (battery or USB)- will obtain 

Wood glue, screws, sandpaper, finish- at Latin

Most electronics were provided through the lab or classroom supply, keeping costs low.

Project Management (plan and deadlines)
To be completed later as instructed.

Tools used:
 (hand tools and Fab Lab equipment)
Laser cutter (for cardboard prototype pieces)

Sandpaper and sanding tools

Hand saw or band saw

Drill

Soldering iron

Arduino IDE (software tool)

Laser cutter settings were adjusted for cardboard settings( vector cut because I was only cutting- no engraving) to ensure clean cuts without burning.

files included- the part of the file that represents my cardboard prototype is the circular base and the four long legs on the right side of the screen. 

<div class="project-assets">
	<h3>TC cardboard SVG</h3>
	<p>Preview of the Tinkercad cardboard layout:</p>
	<img src="{{ '/assets/files/TC_cardboard.svg' | relative_url }}" alt="TC cardboard layout" style="max-width:100%;height:auto;" />

	<h3>Prototype images</h3>
	<div class="image-gallery" style="display:flex;flex-wrap:wrap;gap:10px;">
		<img src="{{ '/assets/images/unnamed.jpg' | relative_url }}" alt="unnamed" style="max-width:30%;height:auto;" />
		<img src="{{ '/assets/images/unnamed%20(1).jpg' | relative_url }}" alt="unnamed (1)" style="max-width:30%;height:auto;" />
		<img src="{{ '/assets/images/unnamed%20(2).jpg' | relative_url }}" alt="unnamed (2)" style="max-width:30%;height:auto;" />
		<img src="{{ '/assets/images/unnamed%20(3).jpg' | relative_url }}" alt="unnamed (3)" style="max-width:30%;height:auto;" />
		<img src="{{ '/assets/images/unnamed%20(4).jpg' | relative_url }}" alt="unnamed (4)" style="max-width:30%;height:auto;" />
		<img src="{{ '/assets/images/unnamed%20(5).jpg' | relative_url }}" alt="unnamed (5)" style="max-width:30%;height:auto;" />
	</div>
</div>


image explanation: obviously the cardboard is not a full representation of the stool, but everything is the same except for the thickness of the base and legs. The length of the legs and diameter of the stool is what I was testing- and each component that I was testing is the appropriate height. To clarify: I have wood selected from the shed with those exact heights, diameter, and length of the legs. That will be completed in the first couple weeks of second semester, along with assembling the electronic components of which have mostly been gathered. That is the plan.

Journaling portion:{% for post in site.posts %}
  {% if post.path == "_posts/2025-12-18-2025-post-journaling.md" %}
    <section class="embedded-journal">
      <h2>{{ post.title }}</h2>
      {{ post.content }}
    </section>
  {% endif %}
{% endfor %}


