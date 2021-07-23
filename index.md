# Sun Tracker Solar Powered Phone Charger
 This solar powered phone charger uses the Sun to power a battery and charge a phone. However, it can also track the movements of the Sun and will tilt towards the Sun like a sunflower. 

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Eric H | Lynbrook High School | Electrical Engineering | Incoming Sophomore

![Headstone Image](https://bluestampengineering.com/wp-content/uploads/2016/05/improve.jpg)
  
# Final Milestone
My final milestone is the increased reliability and accuracy of my robot. I ameliorated the sagging and fixed the reliability of the finger. As discussed in my second milestone, the arm sags because of weight. I put in a block of wood at the base to hold up the upper arm; this has reverberating positive effects throughout the arm. I also realized that the forearm was getting disconnected from the elbow servo’s horn because of the weight stress on the joint. Now, I make sure to constantly tighten the screws at that joint. 

[![Final Milestone](https://res.cloudinary.com/marcomontalbano/image/upload/v1612573869/video_to_markdown/images/youtube--F7M7imOVGug-c05b58ac6eb4c4700831b2b3070cd403.jpg )](https://www.youtube.com/watch?v=F7M7imOVGug&feature=emb_logo "Final Milestone"){:target="_blank" rel="noopener"}

# Second Milestone
My second milestone is completing the solar panel connected charger. I clipped off the connector of the solar panel wire and connected it to another head that could connect to my powerboost. The powerboost would take power from my solar panel and my lithium ion battery to output 5 volts of energy to properly charge a phone. 
[![Third Milestone](https://res.cloudinary.com/marcomontalbano/image/upload/v1612574014/video_to_markdown/images/youtube--y3VAmNlER5Y-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=y3VAmNlER5Y&feature=emb_logo "Second Milestone"){:target="_blank" rel="noopener"}

# First Milestone
My first milestone is hooking up the servo to the arduino. This is a large part of my project as it uses the gears to reposition the swivel of the solar panels to catch the most sunlight possible. I hooked it up to the arduino and made sure that it worked, writing a sample code to test out the motors. 
  

[![First Milestone](https://res.cloudinary.com/marcomontalbano/image/upload/v1624630671/video_to_markdown/images/youtube--lRqF1uRTP9g-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=lRqF1uRTP9g ""))](){:target="_blank" rel="noopener"}
# Circuit Diagram
<img width="559" alt="Screen Shot 2021-07-23 at 7 00 51 AM" src="https://user-images.githubusercontent.com/86114139/126793076-ff06d035-94c0-4405-9c20-e6948db062e6.png">

# Code
<pre>

<font color="#5e6d03">#include</font> <font color="#434f54">&lt;</font><b><font color="#d35400">Servo</font></b><font color="#434f54">.</font><font color="#000000">h</font><font color="#434f54">&gt;</font>

<b><font color="#d35400">Servo</font></b> <font color="#000000">servo</font><font color="#000000">;</font> &nbsp;&nbsp;<font color="#434f54">&#47;&#47; Create a servo object to control the servo</font>
<font color="#00979c">int</font> <font color="#000000">eLDRPin</font> <font color="#434f54">=</font> <font color="#000000">A0</font><font color="#000000">;</font> <font color="#434f54">&#47;&#47; Assign pins to the LDR&#39;s</font>
<font color="#00979c">int</font> <font color="#000000">wLDRPin</font> <font color="#434f54">=</font> <font color="#000000">A1</font><font color="#000000">;</font>
<font color="#00979c">int</font> <font color="#000000">eastLDR</font> <font color="#434f54">=</font> <font color="#000000">0</font><font color="#000000">;</font> <font color="#434f54">&#47;&#47;Create variables to store to LDR readings</font>
<font color="#00979c">int</font> <font color="#000000">westLDR</font> <font color="#434f54">=</font> <font color="#000000">0</font><font color="#000000">;</font>
<font color="#00979c">int</font> <font color="#000000">difference</font> <font color="#434f54">=</font> <font color="#000000">0</font><font color="#000000">;</font> <font color="#434f54">&#47;&#47;Create a variable to compare the two LDR&#39;s</font>
<font color="#00979c">int</font> <font color="#000000">error</font> <font color="#434f54">=</font> <font color="#000000">10</font><font color="#000000">;</font> &nbsp;<font color="#434f54">&#47;&#47; Variable for is there is a noticable difference between the tow LDR&#39;s</font>
<font color="#00979c">int</font> <font color="#000000">servoSet</font> <font color="#434f54">=</font> <font color="#000000">80</font><font color="#000000">;</font> <font color="#434f54">&#47;&#47;Variable for position of servo - will be different for each device</font>


<font color="#00979c">void</font> <font color="#5e6d03">setup</font><font color="#000000">(</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;<font color="#000000">servo</font><font color="#434f54">.</font><font color="#d35400">attach</font><font color="#000000">(</font><font color="#000000">9</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;<font color="#434f54">&#47;&#47;attaches the servo object to PWM pin 9</font>
 &nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">begin</font><font color="#000000">(</font><font color="#000000">9600</font><font color="#000000">)</font><font color="#000000">;</font> 
<font color="#000000">}</font>

<font color="#00979c">void</font> <font color="#5e6d03">loop</font><font color="#000000">(</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;<font color="#000000">eastLDR</font> <font color="#434f54">=</font> <font color="#d35400">analogRead</font><font color="#000000">(</font><font color="#000000">wLDRPin</font><font color="#000000">)</font><font color="#000000">;</font> <font color="#434f54">&#47;&#47;Read the LDR values</font>
 &nbsp;<font color="#000000">westLDR</font> <font color="#434f54">=</font> <font color="#d35400">analogRead</font><font color="#000000">(</font><font color="#000000">eLDRPin</font><font color="#000000">)</font><font color="#000000">;</font>


 &nbsp;<font color="#000000">difference</font> <font color="#434f54">=</font> <font color="#000000">eastLDR</font> <font color="#434f54">-</font> <font color="#000000">westLDR</font> <font color="#000000">;</font> <font color="#434f54">&#47;&#47;Check the difference </font>
 &nbsp;<font color="#5e6d03">if</font> <font color="#000000">(</font><font color="#000000">difference</font> <font color="#434f54">&gt;</font> <font color="#000000">10</font><font color="#000000">)</font> <font color="#000000">{</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Send the panel towards the LDR with a higher reading</font>
 &nbsp;&nbsp;&nbsp;<font color="#5e6d03">if</font> <font color="#000000">(</font><font color="#000000">servoSet</font> <font color="#434f54">&lt;=</font> <font color="#000000">140</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#000000">servoSet</font> <font color="#434f54">++</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#000000">servo</font><font color="#434f54">.</font><font color="#d35400">write</font><font color="#000000">(</font><font color="#000000">servoSet</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">}</font>
 &nbsp;<font color="#000000">}</font> <font color="#5e6d03">else</font> <font color="#5e6d03">if</font> <font color="#000000">(</font><font color="#000000">difference</font> <font color="#434f54">&lt;</font> <font color="#434f54">-</font><font color="#000000">10</font><font color="#000000">)</font> 
 &nbsp;<font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;<font color="#5e6d03">if</font> <font color="#000000">(</font><font color="#000000">servoSet</font> <font color="#434f54">&gt;=</font> <font color="#000000">15</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#000000">servoSet</font> <font color="#434f54">--</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#000000">servo</font><font color="#434f54">.</font><font color="#d35400">write</font><font color="#000000">(</font><font color="#000000">servoSet</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">}</font>
 &nbsp;<font color="#000000">}</font>
 &nbsp;<font color="#5e6d03">else</font>
 &nbsp;<font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">servo</font><font color="#434f54">.</font><font color="#d35400">write</font><font color="#000000">(</font><font color="#000000">80</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#000000">}</font>
 &nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">print</font><font color="#000000">(</font><font color="#000000">eastLDR</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Serial monitor can be useful for debugging&#47;setting up</font>
 &nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">print</font><font color="#000000">(</font><font color="#005c5f">&#34; &nbsp;&nbsp;- &nbsp;&nbsp;&#34;</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Use it to see if your LDR&#39;s are noticeably different when</font>
 &nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">print</font><font color="#000000">(</font><font color="#000000">westLDR</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;They have equal light shining on them, if so, correct with the error value</font>
 &nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">print</font><font color="#000000">(</font><font color="#005c5f">&#34; &nbsp;&nbsp;- &nbsp;&nbsp;&#34;</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">print</font><font color="#000000">(</font><font color="#000000">difference</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;
 &nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">print</font><font color="#000000">(</font><font color="#005c5f">&#34; &nbsp;&nbsp;- &nbsp;&nbsp;&#34;</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">print</font><font color="#000000">(</font><font color="#000000">servoSet</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Fine tune the servo settings, to maximise swing available</font>
 &nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">print</font><font color="#000000">(</font><font color="#005c5f">&#34; &nbsp;&nbsp;- &nbsp;&nbsp;&#34;</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">println</font><font color="#000000">(</font><font color="#005c5f">&#34;.&#34;</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">delay</font><font color="#000000">(</font><font color="#000000">100</font><font color="#000000">)</font><font color="#000000">;</font>
<font color="#000000">}</font>

</pre>
