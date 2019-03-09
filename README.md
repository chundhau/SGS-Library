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

   This class provides a set of convenient methods for performing speedgolf and 
   time duration arithmetic. While JavaScript allows only one constructor, there
   are actually two ways to set up an SGS:
   1. Use the constructor to initialize an SGS with a designated number of  
      strokeMinutes and seconds. Both strokeMinutes and seconds must be integers. While both
      strokeMinutes and seconds may be negative, the SGS is considered to be negative only
      if strokeMinutes is negative; the negative-ness of seconds is ingored.
   2. After constructing an SGS, use setDuration to create an SGS object that acts like a duration.
      setDuration accepts two dates and stores the duration in terms of (stroke)Minutes and seconds.
      If you pass in two Dates where the first Date comes after the second, the resulting SGS is 
      considered invalid. 

   ***IMPORTANT NOTE***
   The validity/invalidity of an SGS object is set in the constructor. 
   The validity of an SGS object can be tested through the isValid() method. If an invalid SGS
   object is used in SGS methods, the returned result is always 'undefined'. Hence, you should always 
   test an SGS for being valid before doing anything else with it.  
