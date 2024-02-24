The LANDFIRE product file name includes the following information:
(using LANDFIRE 2016 Remap Hawaii BPS as an example)

Program     Extent     Year     Layer     Version
L           H          16       BPS       200 

Program = LANDFIRE [L]

Extent =  CONUS    [C] 
          HAWAII   [H] 
          ALASKA   [A] 
          INSULAR AREA [I]
		* Note that each individual island has its own initials 
	[F] is used when a file applies to all extents

Year = last two digits of most recent disturbance year featured in the version Ex.) 20[16]
	* Typically the year the version is named after 
	* Prior to LF 2022, products capable to the current year included the capable year in the naming convention
	instead of the year of the most recent disturbance

Product = the name of the LANDFIRE product Ex.) [BPS]

Version = LANDFIRE version Ex.) 200 (2.0.0) = LF 2016 Remap		      
      
Attribute Tables (CSV and DBF) apply to all extents (unless noted) therefore [F] is applied to the naming convention 
Ex.) [LF16_BPS_200] is the name of the attribute table for LF 2016 Remap BPS (all extents)
