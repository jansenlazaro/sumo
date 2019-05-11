# Sumo
Simple sumo simulation for ns3

Netconvert - imports digital road networks from different sources and generates road networks that can be used by other tools from the package.
Duarouter - generating routes
Netgenerate - generate edges and such


To convert edg.xml, con.xml, nod.xml and tll.xml to net.xml:
	netconvert --node-files=MyNodes.nod.xml --edge-files=MyEdges.edg.xml \
  	--connection-files=MyConnections.con.xml --type-files=MyTypes.typ.xml \
  	--output-file=MySUMONet.net.xml

To convert net.xml to edg.xml, con.xml, nod.xml and tll.xml:
	netconvert -s test.net.xml --plain-output-prefix test

To make random trips:
	randomTrips.py -n test.net.xml -e 100 -r test.rou.xml --trip-attributes="type=\"typedist1\"" --additional-file type.add.xml --edge-permission passenger bus

	** 	-n load file
		-e end time
		-r generate route instead of trips
		--trip-attributes="type=\"typedist1\""	defines attributes
		--additional-file type.add.xml		types specified
		--edge-permission			allows spawning of custom cars in edges

In sumocfg, if you don't want the piled up cars to be automatically removed add this:
	<processing>
		<time-to-teleport value="-1"/>
	<processing>