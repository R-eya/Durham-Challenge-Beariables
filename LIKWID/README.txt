Notes About DINE v DINE2
CAPABILITY
-DINE
  o Started by running likwid-topology locally and bench -a 
  o Lots of commands for peakflops - with extensions to optomise hardware availableto find theoreticam max 
  o So ran likwid-topology to find the type of CPU: AMD EPYC 7302 16-Core Processor, ARCHETECTURE: AMD K17 (Zen2) architecture
  o Looked up the highest supported AVX version
  o "Besides AVX, AMD is including the newer AVX2 standard, too, but not AVX-512." - https://www.lenovo.com/gb/en/glossary/what-is-verbose-die/#:~:text=A%20die%2C%20in%20the%20context,computers%20and%20other%20electronic%20devices.
  o So ran test peakflops_avx
  o BUT later found out that Zen2 supports FMA (used Multiply-Add) and the Zen2 archetecture has 2 fma units per core
  o So we understand the test we ran outputted half of the actual theoretical maximum
  o Theoretical 48732.78 MFlops/s WITHOUT FMA
  o Theoretical 97465.56 MFlops/s WITH FMA
  o This was also run with double precision instead of single precision (we know now double is the default for supercomputers for numerical accuracy so while it is not the 
  absoloute maximum maximum, we decided to go with double precision and because it scales up with the real test we ran i.e. we ran the same test for the real, our efficient values should be correct)
  o REAL MEASURED CAPACITY MFlops/s: 1685.55
  o Efficiency 

- DIN2
  o Mistakes: Intel(R) Xeon(R) Gold 6430 supports avx512 which doubles the register size from the default 256, so actual theoretical max is atleast x2
  o But again the archetecture has 2 AVX-512 FMA Units so if we ran test peakflops_avx512_fma instead then this would give x4  of our theoretical
  o OUR VALUE MFlops/s: 48732.78
  o ACTUAL VALUE WITH PROPER TEST : 194,931.12



COMPARISON
- THEORETICAL CAPBABILITIES: DINE2 is capable of aprox 2x the amount of floating point operations per sec than DINE. Read that DINE2 is more experiemental than DINE and the major difference is that DINE2  supports avx-512 while DINE does not which is primarily where this 2x difference comes from. 


  
