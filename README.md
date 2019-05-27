# coverage-with-splat
```
SPLAT!(1)                       KD2BD Software                       SPLAT!(1)

NAME
       splat An RF Signal Propagation, Loss, And Terrain analysis tool

SYNOPSIS
       splat  [-t  transmitter_site.qth] [-r receiver_site.qth] [-c rx antenna
       height for LOS coverage analysis (feet/meters) (float)] [-L rx  antenna
       height  for  ITM  coverage  analysis  (feet/meters)  (float)]  [-p ter‐
       rain_profile.ext] [-e  elevation_profile.ext]  [-h  height_profile.ext]
       [-H   normalized_height_profile.ext]  [-l  ITM_profile.ext]  [-o  topo‐
       graphic_map_filename.ppm] [-b  cartographic_boundary_filename.dat]  [-s
       site/city_database.dat] [-d sdf_directory_path] [-m earth radius multi‐
       plier (float)]  [-f  frequency  (MHz)  for  Fresnel  zone  calculations
       (float)]  [-R  maximum coverage radius (miles/kilometers) (float)] [-dB
       threshold beyond which contours will  not  be  displayed]  [-gc  ground
       clutter  height (feet/meters) (float)] [-fz Fresnel zone clearance per‐
       centage (default = 60)] [-ano  alphanumeric  output  file  name]  [-ani
       alphanumeric input file name] [-udt user_defined_terrain_file.dat] [-n]
       [-N]  [-nf]  [-sc]  [-dbm]  [-ngs]  [-geo]  [-kml]  [-gpsav]  [-metric]
       [-olditm]

DESCRIPTION
       SPLAT!  is  a  powerful terrestrial RF propagation and terrain analysis
       tool for the spectrum between 20 MHz and 20 GHz.  SPLAT! is free  soft‐
       ware,  and  is  designed for operation on Unix and Linux-based worksta‐
       tions.  Redistribution and/or modification is permitted under the terms
       of  the GNU General Public License, Version 2, as published by the Free
       Software Foundation.  Adoption of SPLAT!  source code in proprietary or
       closed-source  applications  is  a  violation  of  this  license and is
       strictly forbidden.

       SPLAT! is distributed in the hope that it will be useful,  but  WITHOUT
       ANY  WARRANTY,  without even the implied warranty of MERCHANTABILITY or
       FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General  Public  License
       for more details.


INTRODUCTION
       Applications of SPLAT! include the visualization, design, and link bud‐
       get analysis of wireless Wide Area Networks (WANs), commercial and ama‐
       teur  radio  communication  systems above 20 MHz, microwave links, fre‐
       quency coordination and interference studies,  and  the  prediction  of
       analog and digital terrestrial radio and television contour regions.

       SPLAT! provides RF site engineering data such as great circle distances
       and bearings between sites, antenna elevation angles (uptilt),  depres‐
       sion  angles  (downtilt),  antenna height above mean sea level, antenna
       height above average terrain, bearings, distances,  and  elevations  to
       known  obstructions,  Irregular  Terrain  Model  path  attenuation, and
       received signal strength.  In  addition,  the  minimum  antenna  height
       requirements  needed  to clear terrain, the first Fresnel zone, and any
       user-definable percentage of the first Fresnel zone are also provided.

       SPLAT! produces reports, graphs, and high resolution  topographic  maps
       that  depict  line-of-sight  paths,  and  regional path loss and signal
       strength contours through which expected coverage areas of transmitters
       and  repeater  systems  can be obtained.  When performing line-of-sight
       and Irregular Terrain  Model  analyses  in  situations  where  multiple
       transmitter  or repeater sites are employed, SPLAT! determines individ‐
       ual and mutual areas of coverage within the network specified.

INPUT FILES
       SPLAT! is a  command-line  driven  application  and  reads  input  data
       through  a number of data files.  Some files are mandatory for success‐
       ful execution of the program, while  others  are  optional.   Mandatory
       files  include digital elevation topography models in the form of SPLAT
       Data Files (SDF files), site location files (QTH files), and  Irregular
       Terrain Model parameter files (LRP files).  Optional files include city
       location  files,  cartographic  boundary  files,  user-defined  terrain
       files,  path  loss  input  files,  antenna radiation pattern files, and
       color definition files.

 SPLAT DATA FILES
       SPLAT! imports topographic data in the form of SPLAT Data Files (SDFs).
       These  files may be generated from a number of information sources.  In
       the United States, SPLAT Data Files can be generated through U.S.  Geo‐
       logical  Survey  Digital Elevation Models (DEMs) using the postdownload
       and usgs2sdf utilities included with SPLAT!.   USGS  Digital  Elevation
       Models   compatible  with  these  utilities  may  be  downloaded  from:
       http://edcftp.cr.usgs.gov/pub/data/DEM/250/.

       Significantly better resolution and accuracy can  be  obtained  through
       the  use  of  SRTM  Version 2 digital elevation models, especially when
       supplemented by USGS-derived SDF data.  These one-degree by  one-degree
       models  are  the  product  of the Space Shuttle STS-99 Radar Topography
       Mission, and are available for most populated  regions  of  the  Earth.
       SPLAT  Data  Files may be generated from 3 arc-second SRTM-3 data using
       the included srtm2sdf utility.  SRTM-3 Version 2 data may  be  obtained
       through  anonymous  FTP  from: ftp://e0srp01u.ecs.nasa.gov:21/srtm/ver‐
       sion2/SRTM3/

       Note that SRTM filenames refer to the latitude  and  longitude  of  the
       southwest  corner of the topographic dataset contained within the file.
       Therefore, the region of interest must lie north and east of the  lati‐
       tude and longitude provided in the SRTM filename.

       The srtm2sdf utility may also be used to convert 3-arc second SRTM data
       in Band Interleaved by Line (.BIL) format for use  with  SPLAT!.   This
       data   is  available  via  the  web  at:  http://seamless.usgs.gov/web‐
       site/seamless/

       Band Interleaved by Line data must be downloaded  in  a  very  specific
       manner  to  be  compatible  with  srtm2sdf  and SPLAT!.  Please consult
       srtm2sdf's documentation for instructions  on  downloading  .BIL  topo‐
       graphic data through the USGS's Seamless Web Site.

        Even  greater  resolution  and accuracy can be obtained by using 1 arc-
       second SRTM-1 Version 2 topography data.  This data  is  available  for
       the United States and its territories and possessions, and may be down‐
       loaded from: ftp://e0srp01u.ecs.nasa.gov:21/srtm/version2/SRTM1/

       High resolution SDF files for use with SPLAT! HD may be generated  from
       data in this format using the srtm2sdf-hd utility.

       Despite  the higher accuracy that SRTM data has to offer, some voids in
       the data sets  exist.   When  voids  are  detected,  the  srtm2sdf  and
       srtm2sdf-hd  utilities  replace  them  with corresponding data found in
       usgs2sdf generated SDF files.  If USGS-derived SDF data is  not  avail‐
       able,  voids  are  handled  through adjacent pixel averaging, or direct
       replacement.

       SPLAT Data Files contain integer value topographic elevations in meters
       referenced  to  mean  sea level for 1-degree by 1-degree regions of the
       Earth.  SDF files can be read  by  SPLAT!  in  either  standard  format
       (.sdf) as generated directly by the usgs2sdf, srtm2sdf, and srtm2sdf-hd
       utilities, or in bzip2  compressed  format  (.sdf.bz2).   Since  uncom‐
       pressed  files  can  be  read slightly faster than files that have been
       compressed, SPLAT! searches for needed SDF data in uncompressed  format
       first.   If  uncompressed  data cannot be located, SPLAT! then searches
       for data in bzip2 compressed format.  If no compressed SDF files can be
       found  for  the  region  requested,  SPLAT!  assumes the region is over
       water, and will assign an elevation of sea-level to these areas.

       This feature of SPLAT! makes it possible to perform path  analysis  not
       only over land, but also between coastal areas not represented by Digi‐
       tal Elevation Model data.  However, this  behavior  of  SPLAT!   under‐
       scores  the  importance  of  having  all the SDF files required for the
       region being analyzed if meaningful results are to be expected.
       
SITE LOCATION (QTH) FILES
       SPLAT! imports site location information of  transmitter  and  receiver
       sites analyzed by the program from ASCII files having a .qth extension.
       QTH files contain the site's name, the  site's  latitude  (positive  if
       North  of  the  equator,  negative  if South), the site's longitude (in
       degrees West, 0 to 360 degrees, or degrees East 0 to -360 degrees), and
       the site's antenna height above ground level (AGL), each separated by a
       single line-feed character.  The antenna height is assumed to be speci‐
       fied  in  feet  unless  followed  by the letter m or the word meters in
       either upper or lower case.  Latitude and longitude information may  be
       expressed  in either decimal format (74.6864) or degree, minute, second
       (DMS) format (74 41 11.0).

       For example, a site location file describing television  station  WNJT-
       DT, Trenton, NJ (wnjt-dt.qth) might read as follows:

               WNJT-DT
               40.2828
               74.6864
               990.00

       Each  transmitter  and  receiver site analyzed by SPLAT! must be repre‐
       sented by its own site location (QTH) file.

IRREGULAR TERRAIN MODEL PARAMETER (LRP) FILES
       Irregular Terrain Model Parameter data files are  required  for  SPLAT!
       to  determine  RF  path  loss, field strength, or received signal power
       level in either point-to-point or area prediction mode.  Irregular Ter‐
       rain  Model parameter data is read from files having the same base name
       as the transmitter site QTH file, but with a  .lrp  extension.   SPLAT!
       LRP files share the following format (wnjt-dt.lrp):

               15.000  ; Earth Dielectric Constant (Relative permittivity)
               0.005   ; Earth Conductivity (Siemens per meter)
               301.000 ; Atmospheric Bending Constant (N-units)
               647.000 ; Frequency in MHz (20 MHz to 20 GHz)
               5       ; Radio Climate (5 = Continental Temperate)
               0       ; Polarization (0 = Horizontal, 1 = Vertical)
               0.50    ; Fraction of situations (50% of locations)
               0.90    ; Fraction of time (90% of the time)
               46000.0 ; Effective Radiated Power (ERP) in Watts (optional)

       If  an  LRP file corresponding to the tx_site QTH file cannot be found,
       SPLAT! scans the current working directory for  the  file  "splat.lrp".
       If  this file cannot be found, then default parameters will be assigned
       by SPLAT! and a corresponding "splat.lrp" file containing these default
       parameters  will be written to the current working directory.  The gen‐
       erated "splat.lrp" file can then be edited by the user as needed.
       
       Typical Earth dielectric constants and conductivity values are as  fol‐
       lows:
                                  Dielectric Constant  Conductivity
               Salt water       :        80                5.000
               Good ground      :        25                0.020
               Fresh water      :        80                0.010
               Marshy land      :        12                0.007
               Farmland, forest :        15                0.005
               Average ground   :        15                0.005
               Mountain, sand   :        13                0.002
               City             :         5                0.001
               Poor ground      :         4                0.001

       Radio climate codes used by SPLAT! are as follows:

               1: Equatorial (Congo)
               2: Continental Subtropical (Sudan)
               3: Maritime Subtropical (West coast of Africa)
               4: Desert (Sahara)
               5: Continental Temperate
               6:  Maritime  Temperate,  over land (UK and west coasts of US &
       EU)
               7: Maritime Temperate, over sea

       The Continental Temperate climate is common to large land masses in the
       temperate  zone, such as the United States.  For paths shorter than 100
       km, there is little difference between Continental and Maritime Temper‐
       ate climates.

       The  seventh  and  eighth parameters in the .lrp file correspond to the
       statistical analysis provided by  the  ITM  model.   In  this  example,
       SPLAT!  will  return  the  maximum  path loss occurring 50% of the time
       (fraction of time, or Time Variability) in 90% of situations  (fraction
       of  situations,  or  Location  Variability).   This is often denoted as
       F(50,90) in Longley-Rice studies.  In the United  States,  an  F(50,90)
       criteria  is typically used for digital television (8-level VSB modula‐
       tion), while F(50,50) is used for analog (VSB-AM+NTSC) broadcasts.

       For further information on ITM  propagation  model  parameters,  please
       refer  to: http://flattop.its.bldrdoc.gov/itm.html and http://www.soft‐
       wright.com/faq/engineering/prop_longley_rice.html

       The last parameter in the .lrp file corresponds  to  the  transmitter's
       Effective  Radiated Power (ERP), and is optional.  If it is included in
       the .lrp file, then SPLAT! will compute received signal strength levels
       and  field strength level contours when performing ITM studies.  If the
       parameter is omitted, path loss is computed instead.  The ERP  provided
       in  the .lrp file can be overridden by using SPLAT!'s -erp command-line
       switch.  If the .lrp file contains an ERP parameter and the  generation
       of  path  loss  rather than field strength contours is desired, the ERP
       can be assigned to zero using the -erp switch without  having  to  edit
       the .lrp file to accomplish the same result.

CITY LOCATION FILES
       The  names  and  locations  of  cities, tower sites, or other points of
       interest may be imported and plotted on topographic maps  generated  by
       SPLAT!.   SPLAT!  imports  the names of cities and locations from ASCII
       files containing the location of interest's name, latitude, and  longi‐
       tude.  Each field is separated by a comma.  Each record is separated by
       a single line feed character.  As was the case  with  the  .qth  files,
       latitude  and longitude information may be entered in either decimal or
       degree, minute, second (DMS) format.

       For example (cities.dat):

               Teaneck, 40.891973, 74.014506
               Tenafly, 40.919212, 73.955892
               Teterboro, 40.859511, 74.058908
               Tinton Falls, 40.279966, 74.093924
               Toms River, 39.977777, 74.183580
               Totowa, 40.906160, 74.223310
               Trenton, 40.219922, 74.754665

       A total of five separate city data files may be imported at a time, and
       there  is  no limit to the size of these files.  SPLAT! reads city data
       on a "first come/first served" basis, and plots  only  those  locations
       whose  annotations  do  not conflict with annotations of locations read
       earlier in the current city data file,  or  in  previous  files.   This
       behavior  minimizes  clutter  in SPLAT! generated topographic maps, but
       also mandates that important locations be placed toward  the  beginning
       of the first city data file, and locations less important be positioned
       further down the list or in subsequent data files.

       City data files may  be  generated  manually  using  any  text  editor,
       imported  from  other  sources, or derived from data available from the
       U.S. Census Bureau using the citydecoder utility included with  SPLAT!.
       Such   data   is   available  free  of  charge  via  the  Internet  at:
       http://www.census.gov/geo/www/cob/bdy_files.html, and must be in  ASCII
       format.

CARTOGRAPHIC BOUNDARY DATA FILES
       Cartographic  boundary data may also be imported to plot the boundaries
       of cities, counties, or states on topographic maps generated by SPLAT!.
       Such  data  must  be  of the form of ARC/INFO Ungenerate (ASCII Format)
       Metadata Cartographic Boundary Files, and are available from  the  U.S.
       Census     Bureau     via     the    Internet    at:    http://www.cen‐
       sus.gov/geo/www/cob/co2000.html#ascii        and        http://www.cen‐
       sus.gov/geo/www/cob/pl2000.html#ascii.  A total of five separate carto‐
       graphic boundary files may be imported at a time.  It is not  necessary
       to  import  state  boundaries  if  county  boundaries have already been
       imported.

PROGRAM OPERATION
       SPLAT! is invoked via the command-line using a series of  switches  and
       arguments.   Since  SPLAT!  is  a CPU and memory intensive application,
       this type of interface minimizes overhead  and  lends  itself  well  to
       scripted (batch) operations.  SPLAT!'s CPU and memory scheduling prior‐
       ity may be modified through the use of the Unix nice command.

       The number and type of switches passed to SPLAT! determine its mode  of
       operation and method of output data generation.  Nearly all of SPLAT!'s
       switches may be cascaded in any order on the command line when invoking
       the program.

       Simply  typing  splat  on  the  command  line  will return a summary of
       SPLAT!'s command line options:

                    --==[ SPLAT! v1.4.0 Available Options... ]==--


            -t txsite(s).qth (max of 4 with -c, max of 30 with -L)
            -r rxsite.qth
            -c plot coverage of TX(s) with an RX antenna at X feet/meters AGL
            -L plot path loss map of TX based on an RX at X feet/meters AGL
            -s filename(s) of city/site file(s) to import (5 max)
            -b filename(s) of cartographic boundary file(s) to import (5 max)
            -p filename of terrain profile graph to plot
            -e filename of terrain elevation graph to plot
            -h filename of terrain height graph to plot
            -H filename of normalized terrain height graph to plot
            -l filename of path loss graph to plot
            -o filename of topographic map to generate (.ppm)
            -u filename of user-defined terrain file to import
            -d sdf file directory path (overrides path in ~/.splat_path file)
            -m earth radius multiplier
            -n do not plot LOS paths in .ppm maps
            -N do not produce unnecessary site or obstruction reports
            -f frequency for Fresnel zone calculation (MHz)
            -R modify default range for -c or -L (miles/kilometers)
           -sc display smooth rather than quantized contour levels
           -db threshold beyond which contours will not be displayed
           -nf do not plot Fresnel zones in height plots
           -fz Fresnel zone clearance percentage (default = 60)
           -gc ground clutter height (feet/meters)
          -ngs display greyscale topography as white in .ppm files
          -erp override ERP in .lrp file (Watts)
          -ano name of alphanumeric output file
          -ani name of alphanumeric input file
          -udt filename of user defined terrain input file
          -kml generate Google Earth (.kml) compatible output
          -geo generate an Xastir .geo georeference file (with .ppm output)
          -dbm plot signal power level contours rather than field strength
        -gpsav preserve gnuplot temporary working files after SPLAT! execution
       -metric  employ  metric  rather  than  imperial  units for all user I/O
       -olditm invoke older ITM propagation model rather than the newer ITWOM

       The command-line options for splat and splat-hd are identical.

       SPLAT! operates in two distinct modes: point-to-point  mode,  and  area
       prediction  mode.   Either  a  line-of-sight (LOS) or Irregular Terrain
       (ITM) propagation model may be invoked by the user.  True Earth,  four-
       thirds  Earth,  or any other user-defined Earth radius may be specified
       when performing line-of-sight analysis.
       
POINT-TO-POINT ANALYSIS
       SPLAT! may be used to perform line-of-sight  terrain  analysis  between
       two specified site locations.  For example:

       splat -t tx_site.qth -r rx_site.qth

       invokes a line-of-sight terrain analysis between the transmitter speci‐
       fied in tx_site.qth and receiver specified in rx_site.qth using a  True
       Earth  radius  model,  and  writes a SPLAT! Path Analysis Report to the
       current working directory.  The report contains details of  the  trans‐
       mitter  and receiver sites, and identifies the location of any obstruc‐
       tions detected along the line-of-sight path.  If an obstruction can  be
       cleared  by  raising  the receive antenna to a greater altitude, SPLAT!
       will indicate the minimum antenna height required for  a  line-of-sight
       path to exist between the transmitter and receiver locations specified.
       Note that imperial units (miles, feet) are specified unless the -metric
       switch is added to SPLAT!'s command line options:

       splat -t tx_site.qth -r rx_site.qth -metric

       If  the antenna must be raised a significant amount, this determination
       may take a few moments.  Note that the results provided are the minimum
       necessary  for  a  line-of-sight path to exist, and in the case of this
       simple example, do not take Fresnel zone  clearance  requirements  into
       consideration.

       qth  extensions  are  assumed by SPLAT! for QTH files, and are optional
       when specifying -t and -r arguments on the command-line.  SPLAT!  auto‐
       matically  reads  all SPLAT Data Files necessary to conduct the terrain
       analysis  between  the  sites  specified.   SPLAT!   searches  for  the
       required  SDF  files  in  the  current working directory first.  If the
       needed files are not found, SPLAT! then searches in the path  specified
       by the -d command-line switch:

       splat -t tx_site -r rx_site -d /cdrom/sdf/

       An  external directory path may be specified by placing a ".splat_path"
       file under the user's home directory.  This file must contain the  full
       directory  path  of  last resort to all the SDF files.  The path in the
       $HOME/.splat_path file must be of the form of a single  line  of  ASCII
       text:

       /opt/splat/sdf/

       and can be generated using any text editor.

       A  graph  of  the  terrain profile between the receiver and transmitter
       locations as a function of distance from the receiver can be  generated
       by adding the -p switch:

       splat -t tx_site -r rx_site -p terrain_profile.png

       SPLAT!  invokes gnuplot when generating graphs.  The filename extension
       specified to SPLAT! determines the format of the graph produced.   .png
       will produce a 640x480 color PNG graphic file, while .ps or .postscript
       will produce postscript output.  Output in formats such as  GIF,  Adobe
       Illustrator, AutoCAD dxf, LaTeX, and many others are available.  Please
       consult gnuplot, and gnuplot's documentation for  details  on  all  the
       supported output formats.

       A graph of elevations subtended by the terrain between the receiver and
       transmitter as a function of distance from the receiver can  be  gener‐
       ated by using the -e switch:

       splat -t tx_site -r rx_site -e elevation_profile.png

       The  graph  produced  using  this  switch illustrates the elevation and
       depression angles resulting from the  terrain  between  the  receiver's
       location   and  the  transmitter  site  from  the  perspective  of  the
       receiver's location.  A second trace is plotted between the  left  side
       of the graph (receiver's location) and the location of the transmitting
       antenna on the right.   This  trace  illustrates  the  elevation  angle
       required  for  a  line-of-sight  path to exist between the receiver and
       transmitter locations.  If the trace intersects the  elevation  profile
       at  any  point on the graph, then this is an indication that a line-of-
       sight path does not exist under the conditions given, and the  obstruc‐
       tions  can be clearly identified on the graph at the point(s) of inter‐
       section.

       A graph illustrating terrain height referenced to a line-of-sight  path
       between  the  transmitter  and  receiver  may be generated using the -h
       switch:

       splat -t tx_site -r rx_site -h height_profile.png

       A terrain height  plot  normalized  to  the  transmitter  and  receiver
       antenna heights can be obtained using the -H switch:

       splat -t tx_site -r rx_site -H normalized_height_profile.png

       A contour of the Earth's curvature is also plotted in this mode.

       The  first Fresnel Zone, and 60% of the first Fresnel Zone can be added
       to height profile graphs by adding the -f switch, and specifying a fre‐
       quency (in MHz) at which the Fresnel Zone should be modeled:

       splat -t tx_site -r rx_site -f 439.250 -H normalized_height_profile.png

       Fresnel Zone clearances other 60% can be specified using the -fz switch
       as follows:

       splat -t tx_site -r rx_site -f 439.250 -fz 75 -H height_profile2.png

       A graph showing ITM path loss may be plotted using the -l switch:

       splat -t tx_site -r rx_site -l path_loss_profile.png

       As before, adding the -metric switch forces the graphs  to  be  plotted
       using  metric  units of measure.  The -gpsav switch instructs SPLAT! to
       preserve (rather than delete) the gnuplot working files generated  dur‐
       ing  SPLAT! execution, allowing the user to edit these files and re-run
       gnuplot if desired.

       When performing a  point-to-point  analysis,  a  SPLAT!  Path  Analysis
       Report  is  generated  in  the form of a text file with a .txt filename
       extension.  The report contains  bearings  and  distances  between  the
       transmitter  and  receiver, as well as the free-space and ITM path loss
       for the path being analyzed.  The mode of propagation for the  path  is
       given  as  Line-of-Sight,  Single  Horizon, Double Horizon, Diffraction
       Dominant, or Troposcatter Dominant.  Additionally, if the  receiver  is
       located  at the peak of a single obstruction or at the peak of a second
       obstruction, SPLAT! will report RX at  Peak  Terrain  Along  Path  when
       operating under the ITWOM propagation model.

       Distances  and  locations  to known obstructions along the path between
       transmitter and receiver  are  also  provided.   If  the  transmitter's
       effective  radiated power is specified in the transmitter's correspond‐
       ing .lrp file, then predicted signal strength and  antenna  voltage  at
       the receiving location is also provided in the Path Analysis Report.

       To  determine  the signal-to-noise (SNR) ratio at remote location where
       random Johnson (thermal) noise is the primary limiting factor in recep‐
       tion:

       SNR = T - NJ - L + G - NF
       
       where  T  is  the ERP of the transmitter in dBW in the direction of the
       receiver, NJ is Johnson Noise in dBW (-136 dBW for a 6  MHz  television
       channel),  L  is the path loss provided by SPLAT!  in dB (as a positive
       number), G is the receive antenna gain in dB over isotropic, and NF  is
       the receiver noise figure in dB.

       T may be computed as follows:

       T = TI + GT

       where  TI  is  actual  amount of RF power delivered to the transmitting
       antenna in dBW, GT is the transmitting antenna gain (over isotropic) in
       the  direction  of the receiver (or the horizon if the receiver is over
       the horizon).

       To compute how much more signal is available over the minimum to neces‐
       sary to achieve a specific signal-to-noise ratio:

       Signal_Margin = SNR - S

       where  S  is  the minimum required SNR ratio (15.5 dB for ATSC (8-level
       VSB) DTV, 42 dB for analog NTSC television).

       A topographic map may be generated by  SPLAT!  to  visualize  the  path
       between  the  transmitter  and receiver sites from yet another perspec‐
       tive.  Topographic maps generated by SPLAT! display elevations using  a
       logarithmic  grayscale,  with  higher  elevations  represented  through
       brighter shades of gray.  The dynamic range  of  the  image  is  scaled
       between the highest and lowest elevations present in the map.  The only
       exception to this is sea-level, which is represented  using  the  color
       blue.

       Topographic output is invoked using the -o switch:
       
       splat -t tx_site -r rx_site -o topo_map.ppm

       The  .ppm extension on the output filename is assumed by SPLAT!, and is
       optional.

       In this example, topo_map.ppm will  illustrate  the  locations  of  the
       transmitter  and receiver sites specified.  In addition, the great cir‐
       cle path between the two sites will be drawn over locations  for  which
       an  unobstructed  path exists to the transmitter at a receiving antenna
       height equal to that of the receiver site (specified in rx_site.qth).

       It may desirable to populate the topographic map with names  and  loca‐
       tions  of  cities,  tower  sites, or other important locations.  A city
       file may be passed to SPLAT! using the -s switch:

       splat -t tx_site -r rx_site -s cities.dat -o topo_map

       Up to five separate city files may be passed to SPLAT! at a  time  fol‐
       lowing the -s switch.

       County and state boundaries may be added to the map by specifying up to
       five U.S. Census  Bureau  cartographic  boundary  files  using  the  -b
       switch:

       splat -t tx_site -r rx_site -b co34_d00.dat -o topo_map

       In  situations  where multiple transmitter sites are in use, as many as
       four site locations may be passed to SPLAT! at a time for analysis:

       splat -t tx_site1 tx_site2 tx_site3 tx_site4 -r rx_site -p profile.png

       In this example, four separate terrain profiles and obstruction reports
       will be generated by SPLAT!.  A single topographic map can be specified
       using the -o switch, and line-of-sight paths between  each  transmitter
       and  the  receiver  site indicated will be produced on the map, each in
       its own color.  The path between the first transmitter specified to the
       receiver  will be in green, the path between the second transmitter and
       the receiver will be in cyan, the path between  the  third  transmitter
       and  the  receiver  will  be in violet, and the path between the fourth
       transmitter and the receiver will be in sienna.

       SPLAT! generated topographic maps are 24-bit TrueColor Portable  PixMap
       (PPM)  images.   They  may  be  viewed,  edited,  or converted to other
       graphic formats by popular image viewing applications such as  xv,  The
       GIMP,  ImageMagick,  and  XPaint.  PNG format is highly recommended for
       lossless compressed storage of  SPLAT!   generated  topographic  output
       files.  ImageMagick's command-line utility easily converts SPLAT!'s PPM
       files to PNG format:

       convert splat_map.ppm splat_map.png

       Another excellent PPM to PNG  command-line  utility  is  available  at:
       http://www.libpng.org/pub/png/book/sources.html.  As a last resort, PPM
       files may be compressed using the bzip2 utility, and read  directly  by
       The GIMP in this format.

       The -ngs option assigns all terrain to the color white, and can be used
       when it is desirable to generate a map that is devoid of terrain:

       splat -t tx_site -r rx_site -b co34_d00.dat -ngs -o white_map

       The resulting .ppm image file can be converted to .png  format  with  a
       transparent background using ImageMagick's convert utility:

       convert -transparent "#FFFFFF" white_map.ppm transparent_map.png


REGIONAL COVERAGE ANALYSIS
       SPLAT! can analyze a transmitter or repeater site, or network of sites,
       and predict the regional coverage for each  site  specified.   In  this
       mode,  SPLAT!  can  generate a topographic map displaying the geometric
       line-of-sight coverage area of the sites based on the location of  each
       site  and the height of receive antenna wishing to communicate with the
       site in question.  A regional analysis may be performed by SPLAT! using
       the -c switch as follows:

       splat -t tx_site -c 30.0 -s cities.dat -b co34_d00.dat -o tx_coverage

       In  this  example,  SPLAT! generates a topographic map called tx_cover‐
       age.ppm that illustrates the predicted line-of-sight regional  coverage
       of  tx_site  to  receiving  locations  having  antennas 30.0 feet above
       ground level (AGL).  If the -metric switch is used, the  argument  fol‐
       lowing  the  -c switch is interpreted as being in meters rather than in
       feet.  The contents of cities.dat are plotted on the map,  as  are  the
       cartographic boundaries contained in the file co34_d00.dat.

       When  plotting  line-of-sight  paths  and  areas  of regional coverage,
       SPLAT! by default does not account for the effects of atmospheric bend‐
       ing.   However, this behavior may be modified by using the Earth radius
       multiplier (-m) switch:

       splat -t wnjt-dt -c 30.0 -m 1.333  -s  cities.dat  -b  counties.dat  -o
       map.ppm

       An  earth radius multiplier of 1.333 instructs SPLAT! to use the "four-
       thirds earth" model for line-of-sight propagation analysis.  Any appro‐
       priate earth radius multiplier may be selected by the user.

       When performing a regional analysis, SPLAT! generates a site report for
       each station analyzed.  SPLAT! site  reports  contain  details  of  the
       site's  geographic  location,  its  height  above  mean  sea level, the
       antenna's height above mean sea level, the antenna's height above aver‐
       age  terrain,  and  the height of the average terrain calculated toward
       the bearings of 0, 45, 90, 135, 180, 225, 270, and 315 degrees azimuth.


DETERMINING MULTIPLE REGIONS OF LOS COVERAGE
       SPLAT! can also display line-of-sight coverage areas  for  as  many  as
       four separate transmitter sites on a common topographic map.  For exam‐
       ple:

       splat -t site1 site2 site3 site4 -c 10.0 -metric -o network.ppm

       plots the regional line-of-sight coverage of site1, site2,  site3,  and
       site4  based  on  a  receive  antenna  located 10.0 meters above ground
       level.  A topographic map is then written to the file network.ppm.  The
       line-of-sight  coverage area of the transmitters are plotted as follows
       in the colors indicated (along with their corresponding RGB  values  in
       decimal):

           site1: Green (0,255,0)
           site2: Cyan (0,255,255)
           site3: Medium Violet (147,112,219)
           site4: Sienna 1 (255,130,71)

           site1 + site2: Yellow (255,255,0)
           site1 + site3: Pink (255,192,203)
           site1 + site4: Green Yellow (173,255,47)
           site2 + site3: Orange (255,165,0)
           site2 + site4: Dark Sea Green 1 (193,255,193)
           site3 + site4: Dark Turquoise (0,206,209)

           site1 + site2 + site3: Dark Green (0,100,0)
           site1 + site2 + site4: Blanched Almond (255,235,205)
           site1 + site3 + site4: Medium Spring Green (0,250,154)
           site2 + site3 + site4: Tan (210,180,140)

           site1 + site2 + site3 + site4: Gold2 (238,201,0)
           
       If  separate  .qth files are generated, each representing a common site
       location but a different  antenna  height,  a  single  topographic  map
       illustrating  the regional coverage from as many as four separate loca‐
       tions on a single tower may be generated by SPLAT!.

PATH LOSS ANALYSIS
       If the -c switch is replaced by a -L switch, an ITM path loss map for a
       transmitter site may be generated:

       splat -t wnjt -L 30.0 -s cities.dat -b co34_d00.dat -o path_loss_map

       In  this mode, SPLAT! generates a multi-color map illustrating expected
       signal levels in areas surrounding the transmitter site.  A  legend  at
       the  bottom  of the map correlates each color with a specific path loss
       range in decibels.

       The -db switch allows a threshold to be set beyond which contours  will
       not  be plotted on the map.  For example, if a path loss beyond -140 dB
       is irrelevant to the survey being conducted, SPLAT!'s  path  loss  plot
       can be constrained to the region bounded by the 140 dB attenuation con‐
       tour as follows:

       splat -t wnjt-dt -L 30.0 -s  cities.dat  -b  co34_d00.dat  -db  140  -o
       plot.ppm

       The  path  loss contour threshold may be expressed as either a positive
       or negative quantity.

       The path loss analysis range may be modified to  a  user-specific  dis‐
       tance  using  the  -R  switch.  The argument must be given in miles (or
       kilometers if the -metric switch is used).  If a range wider  than  the
       generated  topographic  map  is specified, SPLAT! will perform ITM path
       loss calculations between all four corners of the area prediction map.

       The colors used to illustrate contour regions in SPLAT! generated  cov‐
       erage  maps  may  be  tailored  by  the  user  by creating or modifying
       SPLAT!'s color definition files.  SPLAT! color  definition  files  have
       the  same  base  name  as  the transmitter's .qth file, but carry .lcf,
       .scf, and .dcf extensions.  If the necessary file does not exist in the
       current  working  when  SPLAT!  is run, a file containing default color
       definition parameters that is suitable for manual editing by  the  user
       is written into the current directory.

       When  a regional ITM analysis is performed and the transmitter's ERP is
       not specified or is zero, a .lcf path loss color definition file corre‐
       sponding to the transmitter site (.qth) is read by SPLAT! from the cur‐
       rent working directory.  If a .lcf file corresponding to the  transmit‐
       ter  site is not found, then a default file suitable for manual editing
       by the user is automatically generated by SPLAT!.

       A path loss color definition file  possesses  the  following  structure
       (wnjt-dt.lcf):

        ;  SPLAT!  Auto-generated  Path-Loss  Color Definition ("wnjt-dt.lcf")
       File
        ;
        ; Format for the parameters held in this file is as follows:
        ;
        ;    dB: red, green, blue
        ;
        ; ...where "dB" is the path loss (in dB) and
        ; "red", "green", and "blue" are the corresponding RGB color
        ; definitions ranging from 0 to 255 for the region specified.
        ;
        ; The following parameters may be edited and/or expanded
        ; for future runs of SPLAT!  A total of 32 contour regions
        ; may be defined in this file.
        ;
        ;
         80: 255,   0,   0
         90: 255, 128,   0
        100: 255, 165,   0
        110: 255, 206,   0
        120: 255, 255,   0
        130: 184, 255,   0
        140:   0, 255,   0
        150:   0, 208,   0
        160:   0, 196, 196
        170:   0, 148, 255
        180:  80,  80, 255
        190:   0,  38, 255
        200: 142,  63, 255
        210: 196,  54, 255
        220: 255,   0, 255
        230: 255, 194, 204

       If the path loss is less than 80 dB, the color Red (RGB = 255, 0, 0) is
       assigned  to  the region.  If the path loss is greater than or equal to
       80 dB, but less than 90 db, then Dark Orange (255, 128, 0) is  assigned
       to  the  region.   Orange (255, 165, 0) is assigned to regions having a
       path loss greater than or equal to 90 dB, but less than 100 dB, and  so
       on.   Greyscale  terrain  is displayed beyond the 230 dB path loss con‐
       tour. Adding the -sc switch will smooth  the  transitions  between  the
       specified quantized contour levels.

FIELD STRENGTH ANALYSIS
       If the transmitter's effective radiated power (ERP) is specified in the
       transmitter's .lrp file, or expressed on  the  command-line  using  the
       -erp  switch,  field  strength contours referenced to decibels over one
       microvolt per meter (dBuV/m) rather than path loss are produced:

       splat -t wnjt-dt -L 30.0 -erp 46000 -db 30 -o plot.ppm

       The -db switch can be used in this mode as before to limit  the  extent
       to  which  field  strength  contours  are plotted.  When plotting field
       strength contours, however, the argument given is interpreted as  being
       expressed in dBuV/m.

       SPLAT!  field  strength  color  definition  files  share a very similar
       structure to .lcf files used for plotting path loss:

        ; SPLAT! Auto-generated Signal Color Definition ("wnjt-dt.scf") File
        ;
        ; Format for the parameters held in this file is as follows:
        ;
        ;    dBuV/m: red, green, blue
        ;
        ; ...where "dBuV/m" is the signal strength (in dBuV/m) and
        ; "red", "green", and "blue" are the corresponding RGB color
        ; definitions ranging from 0 to 255 for the region specified.
        ;
        ; The following parameters may be edited and/or expanded
        ; for future runs of SPLAT!  A total of 32 contour regions
        ; may be defined in this file.
        ;
        ;
        128: 255,   0,   0
        118: 255, 165,   0
        108: 255, 206,   0
         98: 255, 255,   0
         88: 184, 255,   0
         78:   0, 255,   0
         68:   0, 208,   0
         58:   0, 196, 196
         48:   0, 148, 255
         38:  80,  80, 255
         28:   0,  38, 255
         18: 142,  63, 255
          8: 140,   0, 128

       If the signal strength is greater than or equal to 128 dB over 1 micro‐
       volt per meter (dBuV/m), the color Red (255, 0, 0) is displayed for the
       region.  If the signal strength is greater than or equal to 118 dBuV/m,
       but  less  than 128 dBuV/m, then the color Orange (255, 165, 0) is dis‐
       played, and so on.  Greyscale terrain is  displayed  for  regions  with
       signal strengths less than 8 dBuV/m.

       Signal  strength contours for some common VHF and UHF broadcasting ser‐
       vices in the United States are as follows:

              Analog Television Broadcasting
              ------------------------------
              Channels 2-6:       City Grade: >= 74 dBuV/m
                                     Grade A: >= 68 dBuV/m
                                     Grade B: >= 47 dBuV/m
              --------------------------------------------
              Channels 7-13:      City Grade: >= 77 dBuV/m
                                     Grade A: >= 71 dBuV/m
                                     Grade B: >= 56 dBuV/m
              --------------------------------------------
              Channels 14-69:   Indoor Grade: >= 94 dBuV/m
                                  City Grade: >= 80 dBuV/m
                                     Grade A: >= 74 dBuV/m
                                     Grade B: >= 64 dBuV/m

              Digital Television Broadcasting
              -------------------------------
              Channels 2-6:       City Grade: >= 35 dBuV/m
                           Service Threshold: >= 28 dBuV/m
              --------------------------------------------
              Channels 7-13:      City Grade: >= 43 dBuV/m
                           Service Threshold: >= 36 dBuV/m
              --------------------------------------------
              Channels 14-69:     City Grade: >= 48 dBuV/m
                           Service Threshold: >= 41 dBuV/m

              NOAA Weather Radio (162.400 - 162.550 MHz)
              ------------------------------------------
                         Reliable: >= 18 dBuV/m
                     Not reliable: <  18 dBuV/m
              Unlikely to receive: <  0 dBuV/m

              FM Radio Broadcasting (88.1 - 107.9 MHz)
              ----------------------------------------
              Analog Service Contour:  60 dBuV/m
              Digital Service Contour: 65 dBuV/m
              
RECEIVED POWER LEVEL ANALYSIS
       If the transmitter's effective radiated power (ERP) is specified in the
       transmitter's  .lrp  file,  or  expressed on the command-line using the
       -erp switch, and the -dbm switch is invoked, received power level  con‐
       tours referenced to decibels over one milliwatt (dBm) are produced:

       splat -t wnjt-dt -L 30.0 -erp 46000 -dbm -db -100 -o plot.ppm

       The  -db switch can be used to limit the extent to which received power
       level contours are plotted.  When plotting power  level  contours,  the
       argument given is interpreted as being expressed in dBm.

       SPLAT! received power level color definition files share a very similar
       structure to the color definition files described earlier, except  that
       the  power  levels  in  dBm may be either positive or negative, and are
       limited to a range between +40 dBm and -200 dBm:

        ; SPLAT! Auto-generated DBM  Signal  Level  Color  Definition  ("wnjt-
       dt.dcf") File
        ;
        ; Format for the parameters held in this file is as follows:
        ;
        ;    dBm: red, green, blue
        ;
        ; ...where "dBm" is the received signal power level between +40 dBm
        ; and -200 dBm, and "red", "green", and "blue" are the corresponding
        ;  RGB  color  definitions ranging from 0 to 255 for the region speci‐
       fied.
        ;
        ; The following parameters may be edited and/or expanded
        ; for future runs of SPLAT!  A total of 32 contour regions
        ; may be defined in this file.
        ;
        ;

          +0: 255,   0,   0
         -10: 255, 128,   0
         -20: 255, 165,   0
         -30: 255, 206,   0
         -40: 255, 255,   0
         -50: 184, 255,   0
         -60:   0, 255,   0
         -70:   0, 208,   0
         -80:   0, 196, 196
         -90:   0, 148, 255
        -100:  80,  80, 255
        -110:   0,  38, 255
        -120: 142,  63, 255
        -130: 196,  54, 255
        -140: 255,   0, 255
        -150: 255, 194, 204

ANTENNA RADIATION PATTERN PARAMETERS
       Normalized field voltage patterns for a transmitting antenna's horizon‐
       tal  and  vertical planes are imported automatically into SPLAT! when a
       path loss, field strength, or received power level coverage analysis is
       performed.   Antenna  pattern  data is read from a pair of files having
       the same base name as the transmitter and LRP files, but with  .az  and
       .el  extensions  for azimuth and elevation pattern files, respectively.
       Specifications regarding pattern rotation (if any) and mechanical  beam
       tilt  and  tilt  direction  (if  any)  are also contained within SPLAT!
       antenna pattern files.

       For example, the first few lines of a SPLAT! azimuth pattern file might
       appear as follows (kvea.az):

               183.0
               0       0.8950590
               1       0.8966406
               2       0.8981447
               3       0.8995795
               4       0.9009535
               5       0.9022749
               6       0.9035517
               7       0.9047923
               8       0.9060051

       The  first  line of the .az file specifies the amount of azimuthal pat‐
       tern rotation (measured clockwise in degrees from  True  North)  to  be
       applied  by SPLAT! to the data contained in the .az file.  This is fol‐
       lowed by azimuth headings (0 to 360 degrees) and their associated  nor‐
       malized field patterns (0.000 to 1.000) separated by whitespace.

       The  structure of SPLAT! elevation pattern files is slightly different.
       The first line of the .el file specifies the amount of mechanical  beam
       tilt  applied  to  the  antenna.   Note that a downward tilt (below the
       horizon) is expressed as a positive angle, while an upward tilt  (above
       the  horizon)  is expressed as a negative angle.  This data is followed
       by the azimuthal direction of the tilt, separated by whitespace.

       The remainder of the file consists of elevation angles and their corre‐
       sponding  normalized  voltage radiation pattern (0.000 to 1.000) values
       separated by whitespace.  Elevation angles must  be  specified  over  a
       -10.0  to  +90.0  degree  range.  As was the convention with mechanical
       beamtilt, negative elevation angles are used  to  represent  elevations
       above  the  horizon,  while positive angles represents elevations below
       the horizon.

       For example, the first few lines a SPLAT! elevation pattern file  might
       appear as follows (kvea.el):

               1.1    130.0
              -10.0   0.172
              -9.5    0.109
              -9.0    0.115
              -8.5    0.155
              -8.0    0.157
              -7.5    0.104
              -7.0    0.029
              -6.5    0.109
              -6.0    0.185

       In  this  example,  the  antenna  is  mechanically  tilted downward 1.1
       degrees towards an azimuth of 130.0 degrees.

       For best results, the resolution of  azimuth  pattern  data  should  be
       specified  to  the  nearest  degree azimuth, and elevation pattern data
       resolution should be specified to the nearest  0.01  degrees.   If  the
       pattern  data specified does not reach this level of resolution, SPLAT!
       will interpolate the values provided  to  determine  the  data  at  the
       required resolution, although this may result in a loss in accuracy.

EXPORTING AND IMPORTING REGIONAL CONTOUR DATA
       Performing  a  regional coverage analysis based on an ITM path analysis
       can be a very time consuming process, especially  if  the  analysis  is
       performed  repeatedly  to  discover what effects changes to a transmit‐
       ter's antenna radiation pattern make to the predicted coverage area.

       This process can be expedited by exporting the contour data produced by
       SPLAT!  to  an  alphanumeric output (.ano) file.  The data contained in
       this file can then be modified to incorporate antenna pattern  effects,
       and imported back into SPLAT! to quickly produce a revised contour map.
       Depending on the way in which SPLAT! is  invoked,  alphanumeric  output
       files  can  describe  regional  path loss, signal strength, or received
       signal power levels.

       For example, an alphanumeric output file containing path loss  informa‐
       tion can be generated by SPLAT! for a receive site 30 feet above ground
       level over a 50 mile radius surrounding a transmitter site to a maximum
       path loss of 140 dB (assuming ERP is not specified in the transmitter's
       .lrp file) using the following syntax:

       splat -t kvea -L 30.0 -R 50.0 -db 140 -ano pathloss.dat

       If ERP is specified in the .lrp file or on the command line through the
       -erp  switch,  the  alphanumeric  output file will instead contain pre‐
       dicted field values in dBuV/m.  If the  -dBm  command  line  switch  is
       used,  then  the  alphanumeric  output file will contain receive signal
       power levels in dBm.

       SPLAT! alphanumeric output files can exceed many hundreds of  megabytes
       in  size.   They  contain information relating to the boundaries of the
       region they describe followed by latitudes (degrees North),  longitudes
       (degrees West), azimuths (referenced to True North), elevations (to the
       first obstruction), followed by either  path  loss  (in  dB),  received
       field  strength  (in  dBuV/m),  or received signal power level (in dBm)
       without regard to the transmitting antenna's radiation pattern.

       The first few lines of a SPLAT! alphanumeric output file could take  on
       the following appearance (pathloss.dat):

               119, 117    ; max_west, min_west
               35, 34      ; max_north, min_north
               34.2265424, 118.0631096, 48.199, -32.747, 67.70
               34.2270358, 118.0624421, 48.199, -19.161, 73.72
               34.2275292, 118.0617747, 48.199, -13.714, 77.24
               34.2280226, 118.0611072, 48.199, -10.508, 79.74
               34.2290094, 118.0597723, 48.199, -11.806, 83.26 *
               34.2295028, 118.0591048, 48.199, -11.806, 135.47 *
               34.2299962, 118.0584373, 48.199, -15.358, 137.06 *
               34.2304896, 118.0577698, 48.199, -15.358, 149.87 *
               34.2314763, 118.0564348, 48.199, -15.358, 154.16 *
               34.2319697, 118.0557673, 48.199, -11.806, 153.42 *
               34.2324631, 118.0550997, 48.199, -11.806, 137.63 *
               34.2329564, 118.0544322, 48.199, -11.806, 139.23 *
               34.2339432, 118.0530971, 48.199, -11.806, 139.75 *
               34.2344365, 118.0524295, 48.199, -11.806, 151.01 *
               34.2349299, 118.0517620, 48.199, -11.806, 147.71 *
               34.2354232, 118.0510944, 48.199, -15.358, 159.49 *
               34.2364099, 118.0497592, 48.199, -15.358, 151.67 *

       Comments  can  be  placed  in the file if they are preceeded by a semi‐
       colon.  The vim text editor has proven capable of editing files of this
       size.

       Note  as  was the case in the antenna pattern files, negative elevation
       angles refer to upward tilt (above the horizon), while positive  angles
       refer  to downward tilt (below the horizon).  These angles refer to the
       elevation to the receiving antenna at the  height  above  ground  level
       specified  using  the  -L  switch  if  the path between transmitter and
       receiver is unobstructed.  If the  path  between  the  transmitter  and
       receiver  is  obstructed,  an  asterisk (*) is placed on the end of the
       line, and the elevation angle returned by SPLAT! refers  the  elevation
       angle  to  the  first  obstruction  rather than the geographic location
       specified on the line.  This is done in response to the fact  that  the
       ITM  model  considers  the  energy  reaching  a  distant  point over an
       obstructed path to be the result of the energy scattered over  the  top
       of the first obstruction along the path.  Since energy cannot reach the
       obstructed location directly, the actual elevation angle to the  desti‐
       nation over such a path becomes irrelevant.

       When  modifying SPLAT! path loss files to reflect antenna pattern data,
       only the last numeric column should be amended to reflect the antenna's
       normalized  gain  at  the azimuth and elevation angles specified in the
       file.  Programs and scripts capable of performing this task are left as
       an exercise for the user.

       Modified  alphanumeric  output  files  can be imported back into SPLAT!
       for generating revised coverage maps provided that  the  ERP  and  -dBm
       options  are  used  as  they were when the alphanumeric output file was
       originally generated:

       splat -t kvea -ani pathloss.dat -s city.dat -b county.dat -o map.ppm

       Note that alphanumeric output files generated by splat cannot  be  used
       with  splat-hd,  or  vice-versa  due  to the resolution incompatibility
       between the two versions of the program.  Also, each of the three types
       of  alphanumeric  output  files are incompatible with one another, so a
       file containing path loss data cannot be imported into SPLAT!  to  pro‐
       duce signal strength or received power level contours, etc.

USER-DEFINED TERRAIN INPUT FILES
       A  user-defined  terrain  file is a user-generated text file containing
       latitudes, longitudes, and heights above ground level of specific  ter‐
       rain features believed to be of importance to the SPLAT! analysis being
       conducted, but noticeably absent from the  SDF  files  being  used.   A
       user-defined  terrain file is imported into a SPLAT! analysis using the
       -udt switch:

        splat -t tx_site -r rx_site -udt udt_file.txt -o map.ppm

       A user-defined terrain file has the following appearance and structure:

              40.32180556, 74.1325, 100.0 meters
              40.321805, 74.1315, 300.0
              40.3218055, 74.1305, 100.0 meters

       Terrain height is interpreted as being described in feet  above  ground
       level  unless  followed  by the word meters, and is added on top of the
       terrain specified in the SDF data  for  the  locations  specified.   Be
       aware  that  each user-defined terrain feature specified will be inter‐
       preted as being 3-arc seconds in both latitude and longitude  in  splat
       and  1  arc-second  in  latitude  and  longitude in splat-hd.  Features
       described in the user-defined  terrain  file  that  overlap  previously
       defined features in the file are ignored by SPLAT! to avoid ambiguity.

GROUND CLUTTER
       The height of ground clutter can be specified using the -gc switch:

             splat -t wnjt-dt -r kd2bd -gc 30.0 -H wnjt-dt_path.png

       The  -gc  switch  as  the  effect of raising the overall terrain by the
       specified amount in feet (or meters if the -metric switch is  invoked),
       except  over  areas  at sea-level and at the transmitting and receiving
       antenna locations.

SIMPLE TOPOGRAPHIC MAP GENERATION
       In certain situations it may be desirable to generate a topographic map
       of  a  region  without plotting coverage areas, line-of-sight paths, or
       generating obstruction reports.  There are several ways of doing  this.
       If  one  wishes to generate a topographic map illustrating the location
       of a transmitter and receiver site  along  with  a  brief  text  report
       describing the locations and distances between the sites, the -n switch
       should be invoked as follows:

       splat -t tx_site -r rx_site -n -o topo_map.ppm

       If no text report is desired, then the -N switch is used:

       splat -t tx_site -r rx_site -N -o topo_map.ppm

       If a topographic map centered about a single  site  out  to  a  minimum
       specified radius is desired instead, a command similar to the following
       can be used:

       splat -t tx_site -R 50.0 -s NJ_Cities -b NJ_Counties -o topo_map.ppm

       where -R specifies the minimum radius of the map in miles  (or  kilome‐
       ters  if  the  -metric switch is used).  Note that the tx_site name and
       location are not displayed in this example.  If display of this  infor‐
       mation  is  desired,  simply  create a SPLAT! city file (-s option) and
       append it to the list of command-line options illustrated above.

       If the -o switch and output filename are omitted in  these  operations,
       topographic  output  is written to a file named tx_site.ppm in the cur‐
       rent working directory by default.

GEOREFERENCE FILE GENERATION
       Topographic, coverage (-c), and path loss contour (-L)  maps  generated
       by  SPLAT!  may be imported into Xastir (X Amateur Station Tracking and
       Information Reporting) software by generating a georeference file using
       SPLAT!'s -geo switch:

       splat -t kd2bd -R 50.0 -s NJ_Cities -b NJ_Counties -geo -o map.ppm

       The  georeference file generated will have the same base name as the -o
       file specified, but have a  .geo extension, and permit proper interpre‐
       tation and display of SPLAT!'s .ppm graphics in Xastir software.
       
GOOGLE MAP KML FILE GENERATION
       Keyhole  Markup Language files compatible with Google Earth may be gen‐
       erated by SPLAT! when performing point-to-point  or  regional  coverage
       analyses by invoking the -kml switch:

       splat -t wnjt-dt -r kd2bd -kml

       The  KML file generated will have the same filename structure as a Path
       Analysis Report for the transmitter  and  receiver  site  names  given,
       except it will carry a  .kml extension.

       Once  loaded into Google Earth (File --> Open), the KML file will anno‐
       tate the map display with the names of  the  transmitter  and  receiver
       site  locations.   The viewpoint of the image will be from the position
       of the transmitter site looking towards the location of  the  receiver.
       The  point-to-point path between the sites will be displayed as a white
       line while the RF  line-of-sight  path  will  be  displayed  in  green.
       Google  Earth's  navigation  tools  allow  the user to "fly" around the
       path, identify landmarks, roads, and other featured content.

       When performing regional coverage analysis, the  .kml file generated by
       SPLAT!  will permit path loss or signal strength contours to be layered
       on top of Google Earth's display along with a corresponding  color  key
       in  the  upper left-hand corner.  The generated .kml file will have the
       same basename as that of the .ppm file normally generated.

DETERMINATION OF ANTENNA HEIGHT ABOVE AVERAGE TERRAIN
       SPLAT! determines antenna height above average terrain (HAAT) according
       to  the  procedure  defined  by  Federal Communications Commission Part
       73.313(d).  According to  this  definition,  terrain  elevations  along
       eight  radials  between  2  and 10 miles (3 and 16 kilometers) from the
       site being analyzed are sampled and averaged for  each  45  degrees  of
       azimuth  starting with True North.  If one or more radials lie entirely
       over water or over land outside the United States (areas for  which  no
       USGS topography data is available), then those radials are omitted from
       the calculation of average terrain.

       Note that SRTM-3 elevation data, unlike older USGS data, extends beyond
       the  borders  of the United States.  Therefore, HAAT results may not be
       in full compliance with FCC Part 73.313(d) in areas along  the  borders
       of the United States if the SDF files used by SPLAT! are SRTM-derived.

       When  performing point-to-point terrain analysis, SPLAT! determines the
       antenna height above average terrain only if  enough  topographic  data
       has  already  been  loaded by the program to perform the point-to-point
       analysis.  In most cases, this will be true, unless the site  in  ques‐
       tion  does  not  lie  within 10 miles of the boundary of the topography
       data in memory.

       When performing area prediction analysis,  enough  topography  data  is
       normally  loaded  by  SPLAT!  to  perform average terrain calculations.
       Under such conditions, SPLAT! will provide  the  antenna  height  above
       average terrain as well as the average terrain above mean sea level for
       azimuths of 0, 45, 90, 135, 180, 225, 270, and 315 degrees, and include
       such  information  in the generated site report.  If one or more of the
       eight radials surveyed fall over water, or over regions  for  which  no
       SDF  data  is available, SPLAT! reports No Terrain for the radial paths
       affected.

ADDITIONAL INFORMATION
       The latest news and information regarding SPLAT! software is  available
       through   the   official   SPLAT!   software   web   page  located  at:
       http://www.qsl.net/kd2bd/splat.html.

AUTHORS
       John A. Magliacane, KD2BD <kd2bd@amsat.org>
              Creator, Lead Developer

       Doug McDonald <mcdonald@scs.uiuc.edu>
              Original Longley-Rice ITM Model integration

       Ron Bentley <ronbentley@embarqmail.com>
              Fresnel Zone plotting and clearance determination

KD2BD Software                 01 February 2011                      SPLAT!(1)

```

Installation
------------
```
$ sudo apt-get update -y
$ sudo apt-get install -y splat
```

version
```
$ splat -version
```

Info
```
man splat
```
