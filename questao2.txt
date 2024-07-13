0.1::flw.
0.7::str(dry); 0.2::str(wet); 0.1::str(snow_covered).
0.9::k.
0.9::b.

0.01::r :- str(dry), flw.
0.99::r :- str(dry), \+flw.
0.05::r :- str(wet), flw.
0.95::r :- str(wet), \+flw.
0.001::r :- str(snow_covered), flw.
0.999::r :- str(snow_covered), \+flw.

0.99::v :- r.
0.01::v :- \+r.

0.99::li :- v, b, k.
0.01::li :- v, b, \+k.
0.01::li :- v, \+b, k.
0.001::li :- v, \+b, \+k.
0.3::li :- \+v, b, k.
0.005::li :- \+v, b, \+k.
0.005::li :- \+v, \+b, k.
0::li :- \+v, \+b, \+k.

evidence(str(snow_covered)).

query(v).
