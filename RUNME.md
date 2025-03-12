# Implementation  
**1. Start osmWebWizard.py in SUMO**  

 • Import OpenStreetMap (OSM) data to create road network.  
 • commands  
 ```bash
  $ cd sumo/tools/  
  $ python osmWebWizard.py
```
 • Select the place, area, vehicles, traffic etc and generated the scenario. This will direct you to sumo-gui.  
 • The road network is created, and the simulation configuration file (e.g.,osm.sumocfg) is generated.    

  
**2. Process osm.sumocfg and Generate trace.xml**  
 • Run the traffic simulation using SUMO to generate mobility data.  
 • commands  
```bash
 $ cd sumo/tools/datefile/  
 $ sumo -c osm.sumocfg --fcd-output trace.xml
```
 • trace.xml file is generated, containing vehicle movement data like positions and speeds.  

  
**3. Convert SUMO Data to NS3-Compatible Format using traceExporter.py**  
 • Convert the trace.xml to the mobility.tcl file used by NS3.  
 • commands
```bash
 $python traceExporter.py -i date/trace.xml --ns2mobility-output=date/mobility.tcl
```
 • The Tcl mobility file (mobility.tcl) is generated, which defines vehicle movement and is compatible with NS3.  

  
**4. Simulate Network in NS3**  
 • Run the NS3 simulation using the mobility model and evaluate network performance
 • Search for the ./waf --run line in ns2-mobility-trace file in the MOBILITY module of NS3. 
 • commands
```bash
 $ cd ns-allinone-3.27/ns-3.27
 $ ./waf --run "scratch/ns2-mobility-trace --traceFile=/home/mahiya/mobility.tcl --nodeNum=129 –duration=100.0 --logFile=ns2-mob.log"
```
 • The NS3 simulation runs, and the VANET scenario is simulated based on the mobility.tcl file.
 • Include th below lines in the ns2-mobility-trace file  
   o #include "ns3/netanim-module.h"  
   o AnimationInterface anim("vehicularmobility.xml");
 • Run the following command again
```bash
 $ ./waf --run "scratch/ns2-mobility-trace --traceFile=/home/mahiya/mobility.tcl --nodeNum=129 –duration=100.0 --logFile=ns2-mob.log"
```

  
**5. Visualize Results using NetAnim**
 • Visualize the simulation output in NetAnim.  
 • command  
```bash
 $ cd ns-allinone-3.27/netanim-3.107/
 $ ./NetAnim
```
 • Select the  vehicularmobility.xml file in NetAnim and run it, this provids an animation of vehicle movement and network interactions.  

  
**6. Routing Protocol Comparison in NS3**
 • Navigate to the vanet-routing-compare file of the WAVE module in NS3.  
 • Mention the path to the mobility.tcl file. 
 • Compare different VANET routing protocols (AODV, OLSR, DSDV, DSR) under various scenarios.  
 • command
```bash
 $ ./waf --run "scratch/vanet-routing-compare --protocol=<x> --scenario=<y>"
```
 • BSM_PDR (Basic Safety Message Packet Delivery Ratio), MAC/PHY overhead and AverageRoutingGoodputKbp are logged to vanet-routing.output2.csv that facilitates the protocol's performance evaluation with dynamic      traffic scenarios. 

   
**7. Analyze and Plot Results**
 • Analyze the performance metrics and visualize the protocol comparison results.
 • command
 ```bash
 cat vanet-routing.output2.csv
```
• The data is output to the console for further analysis and plotting of metrics like packet delivery ratio, throughput, and packet overhead.

