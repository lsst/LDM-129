Large Synoptic Survey Telescope (LSST)

Data Management Infrastructure Design

Mike Freemon and Jeff Kantor

LDM-129

Latest Revision: October 11, 2013

This LSST document has been approved as a Content-Controlled Document by
the LSST DM Technical Control Team. If this document is changed or
superseded, the new document will retain the Handle designation shown
above. The control is on the most recent digital document with this
Handle in the LSST digital archive and not printed versions. Additional
information may be found in the LSST DM TCT minutes.

Change Record

+---------------+--------------+--------------------------------------------------------------------------------+--------------------------------+
| **Version**   | **Date**     | **Description**                                                                | **Owner name**                 |
+===============+==============+================================================================================+================================+
| 1.0           | 7/13/2011    | Initial version as an assembled document; previous material was distributed.   | Mike Freemon and Jeff Kantor   |
+---------------+--------------+--------------------------------------------------------------------------------+--------------------------------+
| 2.0           | 10/9/13      | Updated for Final Design Review                                                | Mike Freemon and Jeff Kantor   |
+---------------+--------------+--------------------------------------------------------------------------------+--------------------------------+
| 3.0           | 10/11/2013   | TCT approved                                                                   | R Allsman                      |
+---------------+--------------+--------------------------------------------------------------------------------+--------------------------------+
+---------------+--------------+--------------------------------------------------------------------------------+--------------------------------+
+---------------+--------------+--------------------------------------------------------------------------------+--------------------------------+
+---------------+--------------+--------------------------------------------------------------------------------+--------------------------------+
+---------------+--------------+--------------------------------------------------------------------------------+--------------------------------+
+---------------+--------------+--------------------------------------------------------------------------------+--------------------------------+
+---------------+--------------+--------------------------------------------------------------------------------+--------------------------------+
+---------------+--------------+--------------------------------------------------------------------------------+--------------------------------+
+---------------+--------------+--------------------------------------------------------------------------------+--------------------------------+
+---------------+--------------+--------------------------------------------------------------------------------+--------------------------------+
+---------------+--------------+--------------------------------------------------------------------------------+--------------------------------+
+---------------+--------------+--------------------------------------------------------------------------------+--------------------------------+

The LSST Data Management Infrastructure Design

Overview
========

The Data Management Infrastructure is composed of all computing,
storage, and communications hardware and systems software, and all
utility systems supporting it, that form the platform of execution and
operations for the DM System. All DM System Applications and Middleware
are developed, integrated, tested, deployed, and operated on the DM
Infrastructure.

This document describes the design of the DM Infrastructure at the
highest level of discussion. It is the “umbrella” document over many
other referenced documents that elaborate on the design in greater
detail.

|image0|

Figure 1. The 3-layered architecture of the Data Management System
enables scalability, reliability, and evolutionary capability.

The DM System is distributed across four sites in the United States and
Chile. Each site hosts one or more physical facilities, in which reside
DM Centers. Each Center performs a specific role in the operational
system.

|image1|

Figure 2: Data Management Sites, Facilities, and Centers.

The Base Center is in the Base Facility on the AURA compound in La
Serena, Chile. The primary role of the Base Center is:

-  Data Access

-  L3 Community Resources

The Archive Center is in the National Petascale Computing Facility at
NCSA in Champaign, IL. The primary role of the Archive Site is:

-  Alert Production processing

-  Data Release Production processing

-  Calibration Production processing

-  Data Access

-  Education and Public Outreach (EPO) Infrastructure

-  L3 Community Resources

Both sites have copies of all the raw and released data for data access
and disaster recovery purposes.

The Base and Archive Sites host the respective Base and Archive Centers,
plus a co-located Data Access Center (DAC).

The Headquarters Site final location is not yet determined, but for
planning and design purposes is assumed to be in Tucson, Arizona. While
the Base and Archive Sites provide large-scale data production and data
access at supercomputing center scale, the Headquarters is a management
and supervisory control center for the DM System, and as a result is
much more modest in terms of infrastructure.

The DMS data centers are modern, high-end computing facilities
consisting of significant compute, storage, and networking resources
that are needed to support the generation and access to the LSST data
products. The remainder of this document describes those computing
resources and technologies in more detail.

Infrastructure Components
=========================

The Infrastructure is organized into components, which are each composed
of hardware and software integrated and deployed as an assembly, to
provide computing, communications, and/or storage capabilities required
by the DM System. lists the major infrastructure components of the DM
system, and indicates if those items are needed for the Center, DAC, or
both. It is the shared infrastructure that reduces overall costs and
motivates the use of co-location for the Data Access Centers at the
Archive and Base Sites.

|image2|

Figure 3. The major components of the LSST DM Infrastructure.

|image3|

Figure 4: Infrastructure Components at the Archive and Base Sites.

Both the Base Center and the Archive Center have essentially the same
architecture (), differing only by capacity and quantity. There are
different external network interfaces depending on the site.

The capacities and quantities are derived from the scientific, system,
and operational requirements via a detailed sizing model. The complete
sizing model and the process used to arrive at the infrastructure is
available in the LSST Project Archive. A summary is provided in and .

|image4|

Table 1: Compute and Facilities Summary.

|image5|

Table 2. Storage Summary.

This design assumes that the DM System will be built using commodity
parts that are not bleeding edge, but rather have been readily available
on the market for one to two years. This choice is intended to lower the
risk of integration problems and the time to build a working,
production-level system. This also defines a certain cost class for the
computing platform that can be described in terms of technology
available today. We then assume that we will be able to purchase a
system in 2020 in this same cost class with the same number of dollars
(ignoring inflation); however, the performance of that system will be
greater than the corresponding system purchased today by some
performance evolution curve factor.

Finally, note that Base Site equipment is purchased in the U.S., and
delivered by the equipment vendors to the Archive Site in Champaign, IL.
NCSA installs, configures, and tests the Base Site equipment before
shipping to La Serena.

The anticipated network between the Archive Site at NCSA and the Base
Site in La Serena, Chile, should be sufficient to transfer LSST’s Data
Products over the network from NCSA to La Serena. The fallback plan is
for NCSA to load the physical storage destined for La Serena with the
data products and transfer the data via physical media as part of the
annual hardware acquisition cycle.

Facilities
==========

This section describes the operational characteristics of the facilities
in which the DM infrastructure resides.

National Petascale Computing Facility, Champaign, IL, US
--------------------------------------------------------

The National Petascale Computing Facility (NPCF) is a new data center
facility on the campus of the University of Illinois. It was built
specifically to house the Blue Waters system, but will also host the
LSST Data Management systems. The key characteristics of the facility
are:

-  |image6|\ 24MW of power (1/4 of campus electric usage)

-  5900 tons of CHW cooling

-  F‐3 tornado & Seismic resistant design

-  NPCF is expected to achieve LEED Gold certification, a benchmark for
   the design, construction, and operation of green buildings.

-  NPCF's forecasted power usage effectiveness (PUE) rating is an
   impressive 1.1 to 1.2, while a typical data center rating is 1.4. PUE
   is determined by dividing the amount of power entering a data center
   by the power used to run the computer infrastructure within it, so
   efficiency is greater as the quotient decreases toward 1.

-  Three on-site cooling towers will provide water chilled by Mother
   Nature about 70 percent of the year.

-  Power conversion losses will be reduced by running 480 volt AC power
   to compute systems.

-  The facility will operate continually at the high end of the American
   Society of Heating, Refrigerating and Air-Conditioning Engineers
   standards, meaning the data center will not be overcooled. Equipment
   must be able to operate with a 65F inlet water temperature and a 78F
   inlet air temperature.

-  Provides high-performance Ethernet connections as required with up to
   300 gigabit external network.

-  There is no UPS in the PCF. LSST will install rack-based UPS systems
   to keep systems running during brief power outages and to
   automatically manage controlled shutdowns when extended power outages
   occur. This ensures that file system buffers are flushed to disk to
   prevent any data loss.

The fire suppression system at the NPCF is a double action water system.
 The first triggering event loads the sprinklers with water and
pressurizes it in the system.  The water is not released unless the
second trigger occurs.

NOAO Facility, La Serena, Chile
-------------------------------

NOAO is expanding their facility in La Serena, Chili, in order to
accommodate the LSST project. Refer to the Base Site design in the
Telescope and Site Subsystem for more detail. The DM requirements for
the Base Facility are documented in LSE-77.

|image7|

Floorspace, Power, and Cooling
------------------------------

and shows the facilities usage by the LSST Data Management System over
the survey period. This does not include any extra space that might be
needed during the process of transitioning replacement equipment or
staging of Base Site equipment at the Archive Site.

|image8|

|image9|

Table 3: Floorspace, power, and cooling estimates for the Data
Management System. The left column is the Archive Site and the rightmost
column is the BaseSite.

|image10|

Figure 5: Power and floorspace needed by the Data Management System over
the survey period.

Note that the current baseline for power, cooling, and floor space
assumes air-cooled equipment. If the sizing model or technology trends
change and we find that flops-per-watt is the primary constraint in our
system design, we will evaluate water-cooled systems.

Computing
=========

The primary compute capability for LSST is a computer cluster providing
a large yet flexible computational resource. The cluster design was
chosen both for its favourable cost and its flexibility to allow for
design/requirement changes throughout the life of the project.

The computational build-out begins in 2018 continues on an annual basis
throughout Operations. The replacement policy eventually reduces the
node count in 2025 and beyond via more powerful nodes (see ). show the
corresponding purchases by year.

|image11|

Figure 6. The number of compute nodes on-the-floor over the survey
period.

The sizing of the cluster is based on proven, sustained application
performance and projections for hardware performance improvements.

The cluster will utilize the GPFS storage described in the next section
and the high-speed InfiniBand network will have bridge devices
connecting it to the external network providing limited visibility of
the compute nodes to the full outside network.

System reliability will be achieved in multiple ways. The software
design will be tolerant to the loss of a compute node and the management
system will detect and remove failing hardware from the compute pool
automatically. The management infrastructure will either include
high-reliability in the hardware or provide redundancy in the case of
failure. The core network will include highly reliable switches
utilizing redundancy at the component level (N+1 or N+N power supplies,
etc.).

The initial server hardware design is planned as a direct extension of
the cluster server hardware available today. That is a two-socket node,
minimal local secondary storage, and attached to the InfiniBand network.
The primary difference between todays hardware and future systems is
expected to be higher core counts and faster memory. All compute nodes
purchased at the same time will have the same configuration to minimize
the number of spares needed and maximize the ability to shift servers
around to perform different tasks. The InfiniBand network will utilize
the best available technology at the time of the initial deployment,
currently estimated to be EDR speeds and plan for a full core network
replacement at mid-life of the project.

Secondary storage for the cluster will utilize the GPFS file system
described in the next section.

|image12|\ The system will be managed as a distributed memory cluster
using industry best practices in system management and security. Tools
such as xCAT will be used to provide a highly scalable and efficient
management interface to deploy and monitor system resources as needed.
xCAT is in use today at NCSA for the administration of computational
clusters and has been proven to scale to the cluster size required for
LSST. xCAT provides some monitoring capability which will be augmented
with NCSA provided tools such cluStat and the Integrated Systems Console
(ISC) that have been used successfully on past and current systems at
NCSA, including Blue Waters. All system logs will be centrally collected
for use in security monitoring and system problem detection and review.
Tools including the ISC and Simple Event Correlator (SEC) will
continuously analyse the log flow to generate alerts for system issues.
These alerts will provide system administrators with immediate notice of
issues as well as be used to take automated actions to remove
problematic components from production. The management practices will
conform to industry best practices including requiring all administrator
access to funnel through a central access point and not allow user
privilege escalation. Finally the core management server will have
regular backups to ensure timely system recovery in the event of a major
disaster or system intrusion.

The Linux operating system and the rest of the compute node environment
will be uniform across the compute infrastructure to simplify management
and application deployment. This fits the traditional cluster model well
and thus will be the primary usage model. A cloud model will also be
available, but is unlikely to be a common usage model in the primary
compute environment. The software environment will be managed for
stability and reliability as well as performance. There will be no more
than one planned system maintenance outage per month, coordinated with
the rest of the project team and conforming to the LSST maintenance
schedule and procedures. In addition all changes to the computational
environment will be tracked via a change control process and approved
prior to implementation with appropriate reviews by project staff in
accordance with LSST policies.

Hardware is purchased in the year before it is needed in order to
leverage price/performance improvements. A special situation occurs for
the Commissioning phase of Construction. In 2018, we acquire and install
the computing infrastructure needed to support Commissioning, for which
we use the same sizing as that for the first year of Operations.

shows the requirements on the compute infrastructure driven by the LSST
processing. summarizes the technical infrastructure necessary to meet
those requirements.

|image13|

Figure 7: The growth of compute requirements over the survey period.

|image14|

Table 4: Compute sizing for the Data Management System.

|image15|

Figure 8: The number of nodes purchased by year over the survey period.

Storage
=======

Image storage will be controller-based storage in a RAID6 8+2
configuration for protection against individual disk failures. GPFS is
the parallel file system.

NCSA’s current hardware model for the GPFS environment is using building
blocks of commodity servers and disk. If more disk capacity or
performance is required, then hardware can be added to the configuration
to accommodate those needs. There are servers with internal SAS disks
for metadata, SAS disk controllers, and disk enclosures using todays 4TB
SATA drives. NCSA is utilizing the fast SAS internal drives for metadata
needs, and using GPFS metadata replication across servers for data
integrity and fault tolerance. The controller and disk enclosure is in
the first disk unit for the GPFS NSD server. The other two disk
enclosures add additional capacity but not performance (See ). The
servers are best deployed as “sister pairs”. They are both active NSDs,
but have metadata mirrors between the two, thus eliminating the single
point of failure. If one fails, there would be a slight performance
degradation, but the data is still readily available from the secondary
server. Currently the GPFS environment at NCSA is connected to the
clusters over Ethernet, but in the case of the LSST it’s just as easy to
integrate the GPFS into the compute cluster and use Infiniband or some
other low latency technology for data environments within a cluster.
NCSA is managing two clusters with GPFS filesystems that exact way
today.

Figure 9. GPFS Storage Infrastructure.

summarizes the LSST storage infrastructure for storing and retrieving
image and other file-based data.

|image16|

Table 5: Image file storage sizing for the Data Management System.

GPFS was chosen as the baseline for the parallel filesystem
implementation based upon the following considerations:

-  NCSA has and will continue to have deep expertise in GPFS and HPSS.

-  NCSA is conducting extensive scaling tests with GPFS and any
   potential problems that emerge at high loads will be solved by the
   time LSST going into Operations.

-  LSST gets special pricing due to the University of Illinois’ campus
   licensing agreement with IBM. These prices are quite favorable and
   even at the highest rates are lower than NCSA can currently get for
   equivalent Lustre service.

-  NCSA provides level 1 support for all UIUC campus licenses under the
   site licensing agreement.

-  Choice of parallel filesystem implementation is transparent to users
   of LSST.

Mass Storage
============

The mass storage system will be HPSS. The GPFS-HPSS Interface (GHI) is
used to create a hierarchical storage system.

|image17|\ The HPSS system is comprised of core servers and movers. The
core servers is where the metadata and process control takes place. The
core servers has its own HA environment and failover between the two
servers. It has a DB2 database that contains all the data with all the
associated files within the HPSS system. The 2\ :sup:`nd` component is
the movers. This is where the hardware sits for writing the data to disk
and tape. The performance of the data being written to disk and tape are
directly proportional to the number of movers and the amount of data
that can be written by them. NCSA’s deployment of HPSS for the NCSA Blue
Waters archive are the core servers being 64 core machines with large
data disk arrays and the mover systems as Dell 720 machines each with a
portion of a disk cache and 8 fiberchannel-attached tape drives. The 720
machines have two 40GigE cards for data transfer, a FC card for the
direct attached tape drives, and a IB card for the disk cache attached.

All client interaction (meaning both processing and people) is with the
single GPFS namespace. This is due to GHI which captures the request for
any data that is not resident in GPFS and is in HPSS and fetches the
data from HPSS on behalf of the user. All client interaction no longer
is required to know the data location. It will be found and brought
locally into client disk cache.

The mass storage system at the Archive Site will write data to dual or
RAIT tapes. The Base Site will write a single copy thus being a disaster
recovery site.

There will be a technology refresh at Year 5 of LSST Operations, when a
new tape drive environment will be purchased to replace the existing
library equipment, and the library system will be upgraded.

captures the requirements and sizing of the mass storage system.

|image18|

|image19|

Figure 10. Capacities and sizing of the Mass Storage System.

Databases
=========

The relational database catalogs are implemented with qserv, an approach
similar to the map-reduce approach in architecture, but applied to
processing sql queries. The database storage is provided via local disk
drives within the database servers themselves. See Document-11625 for
additional information regarding the database architecture.

There will be a large number of database worker nodes, each with its own
local storage. shows the number of worker nodes by year, as well as the
number of drives per node, the amount of storage per node, and the total
number of disk drives in the system. A breakdown of how that storage is
used is provided in .

There are two identical instances of the qserv database environment at
the two DMS Data Access Centers: The U.S. Data Access Center at NCSA,
and the Chilean Data Access Center in La Serena.

|image20|

Figure 11: The number of database nodes on-the-floor over the survey
period.

|image21|

Figure 12. L2 database disk storage, single site.

and summarize the infrastructure associated with supporting the QServ
databases.

|image22|

|image23|

Table 6. Database worker nodes in the Data Management System.

|image24|

|image25|

Table 7: Database sizing for the Data Management System.

Additional Support Servers
==========================

There are a number of additional support servers in the LSST DM
computing environment.

They include:

-  User Data Access - Login Nodes, Web Portals

-  Science User Interface and Image Access Servers

-  VOEvent Brokers

-  Pipeline Support - Condor, ActiveMQ Brokers

-  Cluster Management, Image Deployment

-  Data Management Control System (DMCS) Servers, including Intersite
   Data Transfer

-  Network Security Servers (NIDS)

-  Logging – Collecting and Analyzing System Logs

-  L3 Allocations Support

Cluster Interconnect and Local Networking
=========================================

The local network technologies will be a combination of 10GigE and
InfiniBand.

10GigE will be used for the external network interfaces (i.e. external
to the DM site), user access servers and services (e.g. web portals,
VOEvent servers), mass storage (due to technical limitations), and the
Long Haul Network (see the next section). 10GigE is ubiquitous for these
uses and is a familiar and known technology.

InfiniBand will be used as the cluster interconnect for intra-node
communication within the compute cluster, as well as to the database
servers. It will also be the storage fabric for the image data.
InfiniBand provides the low-latency communication we need at the Base
Site for the MPI-based alert generation processing to meet the 60-second
latency requirements, as well as for the storage I/O performance we need
at the Archive Site for Data Release Production. By using InfiniBand in
this way, we can avoid buying, implementing, and supporting the more
expensive Fibre Channel for the storage fabric.

|image26|

Figure 13: Interconnect Trends 2002-2013. Src: Scientific Computing
World. Issue 127.

Long Haul Network
=================

The communication link between Summit and Base will be 200 Gbps.

The network between the Base Site in La Serena, and the Archive Site in
Champaign, IL, will support 10 Gbps minimum, 40 Gbps during the night
hours, and 80 Gbps burst capability in the event we have a service
interruption and need to “catch up”.

The key features of the network plan are:

-  Mountain summit – Base is only new fiber, 200 Gbps capacity

-  Inter-site Long-Haul links on existing fiber

-  LSST is leveraging and driving US - Chile long-haul network expansion

-  Capacity growth supports construction and commissioning

-  1 Gb/s 2011, 3 Gb/s 2018, 10-40-80 Gb/s 2019

-  Equipment is available today at budgeted cost

|image27|

Figure 14: The LSST Long Haul Network

Additional information can be found in the Network Design Document,
LSE-78.

and depict the nightly and non-nightly data flows, respectively, over
the LSST international network.

|image28|

Figure 15: The Nightly Data Flows over the LSST International Network.

|image29|

Figure 16. The Non-Nightly Data Flows over the LSST International
Network.

Policies
========

A just-in-time approach for purchasing hardware is used to leverage the
fact that hardware prices get cheaper over time. This also allows for
the use of the latest features of the hardware if valuable to the
project.

We buy in the fiscal year before the need occurs so that the
infrastructure is installed, configured, tested, and ready to go when
needed. There is also a ramp up of the initial computing infrastructure
for the Commissioning phase of Construction.

Shown in this section are various polices that we implement for the DM
computing infrastructure. Additional supporting discussion is contained
within document LDM-143.

Replacement Policy
------------------

-  Compute Nodes 5 Years

-  Disk Drives 3 Years

-  Tape Media 5 Years

-  Tape Drives 3 Years

-  Tape Library System Once at Year 5

   1. .. rubric:: Storage Overheads
         :name: storage-overheads

-  RAID 20%

-  Filesystem 10%

   1. .. rubric:: Spares (hardware failures)
         :name: spares-hardware-failures

-  Compute Nodes 3% of nodes

-  Disk Drives 3% of drives

-  Tape Media 3% of tapes

   1. .. rubric:: Extra Capacity
         :name: extra-capacity

-  Disk 10% of TB

-  Tape 10% of TB

Disaster Recovery
=================

Mass storage is used at both sites to ensure the safe keeping of data
products. At the Archive Site, the mass storage system will write two
copies of all data to different media. One set of media stays in the
tape library for later recall as needed. The second copy is transported
off-site. This protects against both media failures (e.g. bad tapes) and
loss of the facility itself.

The Base Site will write a single copy of data to tape, which remains
near-line in the tape library system.

Either Site can be the source of data for recovery of the other Site.

CyberSecurity
=============

LSST has an open data policy. The primary data deliverables of LSST Data
Management are made available to the authorized users without any
proprietary period.

|image30|\ As a result, the central considerations are when applying
security policies are not about the theft of L1 and L2 data. The main
considerations are:

-  Data Protection

-  Data Integrity

-  Misuse of Facility

-  L3 Community Data

We leverage best practices to ensure a secure computing environment.
This includes monitoring such as the use of intrusion detection systems,
partitioning of resources such as segregating the L3 compute nodes from
the core DM processing nodes, and limiting the scope of authorizations
to only that which is needed.

Refer to LSE-99 for additional information. This is a LSST system-wide
document, not just DM, as cybersecurity reaches across to all of the
LSST subsystems.

.. |image0| image:: media/image3.png
.. |image1| image:: media/image4.png
.. |image2| image:: media/image5.png
.. |image3| image:: media/image6.png
.. |image4| image:: media/image7.png
.. |image5| image:: media/image8.png
.. |image6| image:: media/image9.png
.. |image7| image:: media/image10.png
.. |image8| image:: media/image11.png
.. |image9| image:: media/image12.png
.. |image10| image:: media/image13.png
.. |image11| image:: media/image14.png
.. |image12| image:: media/image15.png
.. |image13| image:: media/image16.png
.. |image14| image:: media/image17.png
.. |image15| image:: media/image18.png
.. |image16| image:: media/image19.png
.. |image17| image:: media/image20.png
.. |image18| image:: media/image11.png
.. |image19| image:: media/image21.png
.. |image20| image:: media/image22.png
.. |image21| image:: media/image23.png
.. |image22| image:: media/image11.png
.. |image23| image:: media/image24.png
.. |image24| image:: media/image11.png
.. |image25| image:: media/image25.png
.. |image26| image:: media/image26.jpeg
.. |image27| image:: media/image27.png
.. |image28| image:: media/image28.png
.. |image29| image:: media/image29.png
.. |image30| image:: media/image30.png
