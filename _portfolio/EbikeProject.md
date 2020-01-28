---
title: "Electric Bike Project"
excerpt: "Freshman Project <br/><img src='/images/Ebike/Ebike!.jpeg'>"
collection: portfolio
---


I started building the electric bike on a whim (and because I had [Red Envelope](https://en.wikipedia.org/wiki/Red_envelope) money left over from the holidays) during my freshman year. I started by doing lots of research and reading about people's experience online. I decided to build an bike as opposed to a skateboard because I didn't know how to ride a skateboard (at that time anyways; now I get around campus on an electric skateboard, *like a cool kid*).

As a freshman, I was only equipped with physics and electromagnetic knowledge from highschool physics, so I decided to not invest too much time designing the individual components in the system. I bought the BMS (Battery Management System), Motor Controller, and Battery Charger online. Also, I needed a normal bike to convert -- luckily the apartment complex I was living in at the time had an annual abandoned bike cleanout, and the maintenance man (who I spent the semester befriending) agreed to give me the least deterioted bicycle. 

The hard part was figuring out how to build the battery pack. Most people online used Li-poly/LiPo predesigned battery packs for RC applications, but I figured that would be too boring. Since most solar cars made their battery packs from individual 18650 cells, I decided I wanted to make mine the same way. (Around this time I recently joined [Solar Gators](https://www.ufsolargators.org/) and have spent many hours reading on the subject of solar cars - funny enough Solar Gators used Lead acid batteries our first year, but that was mainly due to lack of manufactering time and the hefty cost of Li-Ion batteries).

The 18650 cells I wanted were quite expensive. The [LG MJ1s](https://www.18650batterystore.com/product-p/lg-mj1-18650-batteries.htm) that the solar car team used in their first Li-Ion battery pack (click [here](andyyangengineer.com/404.html) for the post about that experience!) costs up to $5 a cell! The car uses something like 400 of these cells (20s20p). I read online that old laptop batteries used to use these same type of cells too, so I went on ebay to check for availability. Thankfully I was able to find a large stash of these cells! 

<figure>
    <img style="float: center;" src="/images/Ebike/CellsTopDown.jpeg"> 
    <figcaption> Fig.1 - Top down view of the amalgamation of cells I bought. </figcaption>
</figure>

<figure>
    <img style="float: center;" src="/images/Ebike/CellsSide.jpeg">
    <figcaption> Fig.2 - Side view of the amalgamation of cells I bought. </figcaption>
</figure>

The cells averaged down to $1 to $2 a pop, which was significantly cheaper than the ones I had my eyes set on. However the capacities and internal resistances were also significantly worse. Since I needed to know the capacities of every cell I also bought a 4 cell charger/discharger. This device, seen in fig 3, would be able to measure the capacities as well as the internal resistances of the cells. So I begun the long and arduous journey of measuring and taking note of the capacities of each li-ion cell. I had to charge up the entire cell, then discharge they to measure capacity. 


<figure>
    <img style="float: center;" src="/images/Ebike/BattCap.jpeg">
    <figcaption> Fig.3 - A picture from the week long capacity tests. </figcaption>
</figure>

Amongst the lot I purchased there were some that were completely unusable. When measured across the terminals, I either saw voltages below the minimum (2.5V or 2.7V depending on how conservative you are) or no voltage at all. In the numbers of cells I bought, about 20 couldn't be used - usually this is becuase the cells were discharged completely and could not be revived, or because they were near their end of life cycle and had tiny capacities, or they didn't have much capacity to begin with. 

As I suspected, when I was down with all the measurements The cell's capacities as a whole varied dramastically. The largest capacity I saw was something like 2500mAh, while the lowest was close to 500mAh.

<figure>
    <img style="float: center;" src="/images/Ebike/DiffCaps.jpeg">
    <figcaption> Fig.4 - These cells showed drastic differenced in their capacities. </figcaption>
</figure>

Since the capacity of the cell was limited by *the parallel group with the least capacity* The plan was to maximize the capacity of the pack as a whole by making sure the parallel groups were all evenly matched in capacity. When I did the capacity tests, I numbered the cells and recorded the capacities. Then with the help of my roommate we wrote a script to group the cells together in a way to make the capacities of each paralle group match. 

An important note was to decide the configuration of the battery pack. Since the motor / motor controller was rated for 48V, I used 13 cells in series, which puts the nominal pack voltage of 48.1V (since 13 * 3.7V = 48.1V). Then I just used as many cells as I could to make the parallel groups. The end configuration was 13s11p. 

Once I knew how to group the cells together, it was time to get to work assembling the pack. Initially I made a spot welder from the transformer of a old microwave. I removed the secondary windings from the transformer and used some hefty wiring of my own, since I expected there to be lots of current. In the applicaiton of spot welding high current is needed, so using my knowledge of transformer equations I knew to have 1 or 2 windings on the secondary side. I also salvaged the door switch from the microwave to use as my on and off switch since it was a momentary on switch and was conviently there. 

Unfortunately when I started testing I obliterated through the nickel strips I bought when I tried to spot weld them together. After several unsuccessful attempts I decided to bite the dust and ask the ECE department at UF if they had a spotwelder I could use. I also asked the mechanical department, to which they responded they had a sheet metal spot welder (I was amused by the thought of even attempting to use this on a battery) but not the battery spot welder I was looking for. (Later I realized the reason I oblierated through the weld was because without pulsing of the welder I had no control of the current, and to acheive the best welds I needed to control the spot welder to PWM the welding.) The ECE department didn't have a spot welder, but offered to buy one and let me use, if I specc'ed one out (thanks Mike!). 

<figure>
    <img style="float: center;" src="/images/Ebike/StartoftheSpotWelds.jpeg">
    <figcaption> Fig.5 - In NEB, starting my welds. </figcaption>
</figure>

<figure>
    <img style="float: center;" src="/images/Ebike/AssembledBatPack.jpeg">
    <figcaption> Fig.6 - My spot welded battery pack! </figcaption>
</figure>

After assembling the battery pack the next step was soldering the BMS leads onto the pack. 

<figure>
    <img style="float: center;" src="/images/Ebike/FinishedPack.jpeg">
    <figcaption> Fig.6 - Getting ready to solder the BMS onto the pack </figcaption>
</figure>

During the process of soldering I had accidently shorted a cell, by melting the insulating sleeve. Thankfully the result wasn't too explosive, and the cell extinguished it self before going into thermal runaway. By messing up a cell here, I actually had to momentarily to remove a parallel group (this explains why there are 12 in series in fig 6 as opposed to 13) to weld again using NEB's spot welder.

<figure>
    <img style="float: center;" src="/images/Ebike/ShortedCell.jpeg">
    <figcaption> Fig.7 - Extinguished Cell </figcaption>
</figure>

I also had to build a box to keep the battery pack in and a way to secure the box to my bike. I used a rear wheel mounting rack I got off of amazon, and secured the rack to the wood box I made. 

<figure>
    <img style="float: center;" src="/images/Ebike/BattBoxNoPaint.jpeg">
    <figcaption> Fig.8 - Letting the wood glue dry on my custom battery box </figcaption>
</figure>

And of course, I had to paint it black to make it look cool, and match my bike. I selected a plastic based spray paint to add insulation between the pack and the metal nails. I also added a layer of electrical tape over the metal for extra insulation. I also added a hinged top for serviceability. 

<figure>
    <img style="float: center;" src="/images/Ebike/PaintedBattBox.jpeg">
    <figcaption> Fig.9 - Look at that box! </figcaption>
</figure>

Finally, here is the completed project. 

<figure>
    <img style="float: center;" src="/images/Ebike/Ebike!.jpeg">
    <figcaption> Fig.6 - Finished Ebike! </figcaption>
</figure>

Unfortunately I didn't take anymore pictures of the bike, or of me and the bike, but the use of the bike was short lived. With the weight of the motor and the weight of the battery pack, moving the bike down and up a flight of stairs was more troubled than what it was worth - furthermore I was always worried about the bike when I was in class so I did not bring it to campus frequently. Then one cold morning when I took it out to ride, the motor controller suddenly blew out on me. That was around the end of freshman year, and shortly after I started my internship at FPL's sister company Next Era Energy in the distributed generation department. By the time I came back from the internship my role as Solar Gator's Electrical Lead started, and so my desire to fix up the bike lessened drastically. 

However building the bike was a enormous learning oppurtunity. I feel by building the bike and going through the motions I got a large leg up on my peers and served as a great interview discussion point. Furthermore, I was able to bring my experience of building the battery pack to Solar Gators, where I also helped build a battery pack. 