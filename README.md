# TTTLocationFormatter
## Format coordinates, distance, bearing, and velocity in Metric or Imperial Units

When working with `CoreLocation`, you can use your favorite unit for distance... so long as your favorite unit is the meter. If you want to take distance calculations and display them to the user, you may want to use kilometers instead, or maybe even miles, if you're of the [Imperial](http://en.wikipedia.org/wiki/Imperial_units) persuasion.

`TTTLocationFormatter` gives you a lot of flexibility in the display of coordinates, distances, direction, speed, and velocity. Choose Metric or Imperial, cardinal directions, abbreviations, or degrees, and configure everything else (number of significant digits, etc.), with the associated `NSNumberFormatter`.

## Example Usage

    TTTLocationFormatter *locationFormatter = [[[TTTLocationFormatter alloc] init] autorelease];
    CLLocation *austin = [[[CLLocation alloc] initWithLatitude:30.2669444 longitude:-97.7427778] autorelease];
    CLLocation *pittsburgh = [[[CLLocation alloc] initWithLatitude:40.4405556 longitude:-79.9961111] autorelease];
    
### Distance in Metric Units with Cardinal Directions

    NSLog(@"%@", [locationFormatter stringFromDistanceAndBearingFromLocation:pittsburgh toLocation:austin]);
    // "2,000 km Southwest"
    
### Distance in Imperial Units with Cardinal Direction Abbreviations

    [locationFormatter.numberFormatter setMaximumSignificantDigits:4];
    [locationFormatter setBearingStyle:TTTBearingAbbreviationWordStyle];
    [locationFormatter setUnitSystem:TTTImperialSystem];
    NSLog(@"%@", [locationFormatter stringFromDistanceAndBearingFromLocation:pittsburgh toLocation:austin]);
    // "1,218 miles SW"
    
### Speed in Imperial Units with Bearing in Degrees

    [locationFormatter setBearingStyle:TTTBearingNumericStyle];
    NSLog(@"%@ at %@", [locationFormatter stringFromSpeed:25],[locationFormatter stringFromBearingFromLocation:pittsburgh toLocation:austin]);
    // "25 mph at 310°"

### Coordinates

    [locationFormatter setUsesSignificantDigits:NO];
    NSLog(@"%@", [locationFormatter stringFromLocation:austin]);
    // (30.2669444, -97.7427778)

## License

TTTLocationFormatter is licensed under the MIT License:

  Copyright (c) 2011 Mattt Thompson (http://mattt.me/)

  Permission is hereby granted, free of charge, to any person obtaining a copy
  of this software and associated documentation files (the "Software"), to deal
  in the Software without restriction, including without limitation the rights
  to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
  copies of the Software, and to permit persons to whom the Software is
  furnished to do so, subject to the following conditions:

  The above copyright notice and this permission notice shall be included in
  all copies or substantial portions of the Software.

  THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
  IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
  FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
  AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
  LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
  OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
  THE SOFTWARE.
