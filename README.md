# SGS-Library
A specialized class for representing and manipulating scores and times in the sport of speedgolf

   The SGS class represents a speedgolf score, which combines golf strokes and time taken to hole out.
   A speedgolf score consists of the number of minutes/strokes (called strokeMinutes) and the number
   of seconds. It is written as [mm]m:ss, where m is the number of stroke-minutes and s is the number
   of seconds.

   This class works equally well for speedgolf times (time durations) and time pars 
   (also time durations): It will correctly handle time arithmetic when summing time durations or 
   subtracting one time from another.

   There are two unique features of speedgolf scores/times that distinguish them:
   1. An SGS can be negative. A negative SGS is interpreted as under par, 
      and only makes sense in the context of a speedgolf score. When an SGS object is 
      initialized using Date timestamps, negative time durations are NOT allowed. When
      an SGS object is intialized, if either the minutes or the seconds is negative,
      the SGS is set to be negative.

   2.  An SGS contains only minutes and seconds -- never hours. A player who completes a
      speedgolf round in one hour and 4 minutes, for example, is said to have played the
      round in 64 minutes, and if she needed 70 strokes for that round, her SGS would
      be 64 + 70 = 134. Hours just aren't a part of the speedgolf world.

   There are three sets of parameters you can use to instantiate a new SGS object:
   1. Two integers -- one for strokeMinutes and one for seconds. If etiher is negative, the SGS is assumed to be negative.
   2. Two Date objects -- one representing the start time and the other representing the end time of the duration. The SGS object is instantiating as the duration between the two timestamps. Note that the second time must temporally follow the first; it is not possible to instantiate a negative duration.
   3. One string in [-][m][m]m:ss format representing an SGS or duration as a string. The SGS string can have up to three minutes digits tor represent durations up to 999 minutes, or nearly 17 hours. Negative SGS values are accepted in this format; just use the minus sign at the front of the string. 
   
   This class provides a set of convenient methods for performing speedgolf and time duration arithmetic:
   * isUnderPar -- returns true ift he SGS object represents a speedgolf score that is under par, false otherwise
   * getStrokeMinutes -- returns the strokeMinutes (SGS) or minutes (time duration) portion of the object.
   * setSeconds -- returns the seconds portion of the object.
   * isGreaterThan, isEqualTo, isLessThan -- Methods that alllow two SGS objects to be compared.
   * toString -- returns a pretty-printable string representation of an SGS, e.g., "2:34", "-4:12"or "Even"
   * addTo, addToMany -- sums two SGSs or an array of SGSs
   * subtractFrom: subtracts one positve SGS from another (negative SGGs are not accepted by this method)

   ***IMPORTANT NOTE***
   The validity/invalidity of an SGS object is set in the constructor. 
   The validity of an SGS object can be tested through the isValid() method. If an invalid SGS
   object is used in SGS methods, or if you try to invoke SGS methods on an invalid SGS object, the returned result is always 'undefined'. Hence, you should always test an SGS for being valid before doing anything else with it.  
