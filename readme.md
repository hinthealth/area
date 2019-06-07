Hi. This gem is a fork of the area gem https://github.com/jgv/area and allows you to perform the following conversions:

* An area code to a region (state)
* A state to an area code
* A place to a zip code
* A zip code to a place (control granularity with city and state options)
* A zipcode to a lat/lon
* A zipcode to just a lat
* A zipcode to just a lon
* A lat/lon pair to a region
* A lat/lon pair to its zip code

Original area gem includes the following conversions:
* A zipcode to its GMT offset
* A state to its GMT offset
* A lat/lon pair to its GMT offset

The difference between the original area gem and this forked gem is the zipcodes.csv file. This gem uses the geonames US file from http://download.geonames.org/export/zip/US.zip, which provides a more up-to-date list of US-based zip codes. To meet the needs of the area gem format, we have adapted the original geonames file by removing columns 0, 3, 5, 6, 7, 8 and 11. All the information itself has remained the same.

Meaning of said columns:
* 0 country code
* 3 admin name1: 1. order subdivision (state)
* 5 admin name2: 2. order subdivision (county/province)
* 6 admin code2: 2. order subdivision (county/province)
* 7 admin name3: 3. order subdivision (community)
* 8 admin code3: 3. order subdivision (community)
* 11 accuracy

## Usage

#### Convert an area code to a state/region
``` ruby
646.to_region #=> NY
```

#### Convert a state to an area code
```` ruby
"AK".to_area #=> ["907"]
"CT".to_area #=> ["203", "860"]
```

#### Convert a place to a zip code
```` ruby
"long island city, ny".to_zip #=> ["11101", "11109", "11120"]
"hastings on hudson".to_zip #=> ["10706"]
```

#### Convert a zip code to a place
```` ruby
"11211".to_region #=> "Brooklyn, NY"
"11211".to_region(:city => true) #=> "Brooklyn"
"11211".to_region(:state => true) #=> "NY"
```

#### Convert a zip code to a lat/lon
```` ruby
"11211".to_latlon #=> "40.71209, -73.95427"
```

#### Convert a zip code to a lat
```` ruby
"11211".to_lat #=> "40.71209"
```

#### Convert a zip code to a lon
```` ruby
"11211".to_lon #=> "-73.95427"
```

#### Convert a lat/lon pair to a zipcode
```` ruby
[40.71209, -73.95427].to_zip #=> "11211"
```

#### Convert a lat/lon pair to a region
```` ruby
[40.71209, -73.95427].to_region #=> "Brooklyn, NY"
```

## Copyright

Copyright (c) 2012 Jonathan Vingiano. See [LICENSE](https://github.com/jgv/area/blob/master/MIT-LICENSE) for details.
