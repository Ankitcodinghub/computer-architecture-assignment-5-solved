# computer-architecture-assignment-5-solved
**TO GET THIS SOLUTION VISIT:** [Computer Architecture Assignment 5 Solved](https://www.ankitcodinghub.com/product/computer-architecture-laboratory-solved/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;117744&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;3&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (3 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;Computer Architecture Assignment 5 Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (3 votes)    </div>
    </div>
Upgrade the simulator to a discrete event simulator.

Inputs and Outputs

The inputs and outputs stay the same. The inputs are the configuration file, the path where the statistics file is to be created, and the object file. The output is the statistics file. Report throughput in terms of instructions per cycle in the statistics file.

New Source Files

Place the new source files: Element.java, Event.java, EventQueue.java, ExecutionCompleteEvent.java, MemoryReadEvent.java, MemoryResponseEvent.java, MemoryWriteEvent.java in the generic package.

Updation of Simulator.java

• Add the following data member to the class: static EventQueue eventQueue;.

• Add the following line to the constructor: eventQueue = new EventQueue();.

• Update the loop in simulate() to look like this:

while ( not end of simulation )

{ performRW performMA performEX eventQueue . processEvents (); performOF performIF

increment clock by 1

}

• Add this function to the class:

public static EventQueue getEventQueue ()

{ return eventQueue ;

}

Discrete Event Simulator Model

Decide which units you wish to work using events, and which directly through function calls from the main loop. For all units that you believe will recieve events, make them implement the Element interface. This will then require you to implement a handleEvent() function for that unit.

Example

Below is a brief illustration of the Instruction Fetch stage. It is by no means complete. It is only to give you the basic idea.

public void performIF ()

{ i f ( IF EnableLatch . isIF enable ())

{ i f ( IF EnableLatch . isIF busy ())

{ return ;

}

Simulator . getEventQueue (). addEvent( new MemoryReadEvent(

Clock . getCurrentTime () + Configuration . mainMemoryLatency , this , containingProcessor . getMainMemory() ,

containingProcessor . getRegisterFile (). getProgramCounter ( )) );

IF EnableLatch . setIF busy ( true );

}

}

@Override public void handleEvent (Event e) { i f (IF OF Latch . isOF busy ())

{

e . setEventTime(Clock . getCurrentTime () + 1);

Simulator . getEventQueue (). addEvent(e );

} else

{

MemoryResponseEvent event = (MemoryResponseEvent) e ;

IF OF Latch . setInstruction ( event . getValue ());

IF OF Latch . setOF enable ( true );

IF EnableLatch . setIF busy ( false );

}

}

Below is the code snippet from the MainMemory.java class.

@Override public void handleEvent (Event e) { i f (e . getEventType () == EventType .MemoryRead)

{

MemoryReadEvent event = (MemoryReadEvent) e ;

Simulator . getEventQueue (). addEvent( new MemoryResponseEvent( Clock . getCurrentTime () , this , event . getRequestingElement () , getWord( event . getAddressToReadFrom ( ) ) ) ) ; }

}

Functionalities to be Implemented

• Modeling the latency of the main memory

– This should reflect in both instruction fetches and load/ store operations

• Modeling the latencies of different functional units: ALU, multiplier, divider, etc.

To Be Submitted

• A zip of the source files. They have to pass the test cases given for the previous assignment.

• A report that contains a table with

– the number of cycles taken by each benchmark program, – the throughput in terms of instructions per cycle.

Comment on your observations. Correlate with the nature of the benchmarks.
