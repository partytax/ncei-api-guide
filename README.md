# NCEI Data Service API for Completely Unhinged Maniacs™

This guide is an attempt to demystify the National Oceanic and Atmospheric Administration's (NOAA's) National Centers for Environmental Information (NCEI) Data Service API.

First, request a token at this URL: https://www.ncdc.noaa.gov/cdo-web/token
Don't be alarmed by the NCDC URL. The National Climactic Data Center (NCDC) is the former name of the NCEI.


**GET** `https://www.ncei.noaa.gov/access/services/data/v1?{paramKey1}={val1}&{paramKey2}={val2}`

|Parameter Key|Possible Values|Our Description|NCEI Description|
|---|---|---|---|
|dataset|||The dataset parameter selects the dataset to query for data. Please note that all the datasets are NOT available through the NCEI Access Data Service API, however new datasets are added quarterly.|
|stations|||The stations parameter adds a comma separated list of station identifiers for selection and subsetting.|
|startDate|||This is the date to select from the dataset for a given start date. This parameter is an ISO 8601 date (YYYY-MM-DD) -or- ISO 8601 combined date and time format (YYYY-MM-DDTHH:mm:ss). If using an ISO 8601 combined date and time format the T that separates the time is NOT optional. The ISO 8601 combined date and time also supports optional time zone representations.  Use Z or z for UTC and +HH:mm or -HH:mm for the offset from UTC. The plus symbol (+) must be URL encoded at “%2B” or it will not validate. The start and end dates are not required. The startDate must come before the endDate parameter. Some datasets are averages over time and may ignore parts of a date.|
|endDate|||This is the date to select datasets whose period of record (PoR) starts on or after the given endDate. This parameter is an ISO 8601 date (YYYY-MM-DD) -or- ISO 8601 combined date and time format (YYYY-MM-DDTHH:mm:ss). If using an ISO 8601 combined date and time format, the T that separates the time is NOT optional. The ISO 8601 combined date and time also supports optional time zone representations.  Use Z or z for UTC and +HH:mm or -HH:mm for the offset from UTC. The plus symbol (+) must be URL encoded as “%2B” or it will not validate.  If the start date is required for the dataset then you must include the startDate parameter.|
|dataTypes|||Data Types allows the selection of one or many dataTypes. Datasets have different names for the data types (e.g., variables, observations). The dataTypes parameter is used with a comma-separated list. This parameter is case-sensitive and will respond with an HTTPS Status Code: 400 Bad Request and JSON with more information.|
|boundingBox|||The bounding box is used to select data from a geographic location contained within the coordinates, given as four comma separated numbers. North and South range from -90 to 90 and East and West range from -180 to 180. If these are not set the geographic extent defaults to the entire globe (90,-180,-90,180).|
|format|||The format parameter allows the user to select how the data should be formatted. Note that some data formats ignore certain data types. For example, PDF data may only display data types for a report, and not for the requested dataTypes.|
|options|||The API supports an options parameter that turns features on and off. Options are separated by commas and the respective values are separated by a colon (:); boolean values are represented by true or false,or zero (0) and one (1). Options can either pass as a comma-separated list: …&options=includeAttributes:true,includeStationName:1 or individually as URL parameters: ...&includeAttributes=0&includeStationName=true|
|includeAttributes|||Includes the attribute for a selected datatype. These are typically comma separated (e.g., “T,,0,0700”), and added to the results if the includeAttributes parameter is set to true. This value can be the word true or a numeric representation of the boolean value, 1. The default value is false or 0 and will not display datatype(s) attributes.|
|includeStationName|||Includes the station’s name, if available, for the selected dataset and data type. This value can be the word true or a numeric representation of the boolean value, 1. The default value is false or 0 and will not display datatype(s) attributes.|
|includeStationLocation|||Includes the station’s location, if available, for the selected dataset and data type. This value can be the word true or a numeric representation of the boolean value, 1. The default value is false or 0 and will not display datatype(s) attributes.|
|units|||The units parameter converts the output data for datasets and datatypes that support conversion to either “metric” or “standard” units.|
