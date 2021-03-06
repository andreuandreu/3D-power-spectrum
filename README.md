# 3D-power-spectrum
List of extracted Fourier modes of Hydrodinamycal simulations transmission fraction field.

Explanation of the tables in this directory:
Each file contains the results of a simulation output for the Lyman alpha
transmission power spectrum, at a given redshift output, usually
z=2.2, 2.4, 2.6, 2.8 and 3.0, except for the Eulerian simulation,
which has redshift outputs at 2.9, 2.6, and 2.3.
Each file contains 552 entries, for all the k,mu bins at which the power
spectrum P_F is obtained from the simulation output. The first 296 of these
entries are for k<k_t, where the modes are combined only when they have
exactly the same values of k,mu. The last 256 entries are for bins at
k>k_t, with 16 bins in log(k) and 16 bins in mu.
There are 6 columns for all the entries, which are the following quantities:
1. Bin number (from 0 to 551)
2. k: exp(log(k)), where log(k) is the average value of log(k) of all the modes
     contributing to this bin. For k<k_t, this is just the value of k that is
     equal for all the modes.
3. mu: average value of mu of all the modes contributing to this bin.
     For k<k_t this is the value of mu that is equal for all the modes.
4. P_L: linear matter power spectrum at k, computed at the redshift of the
     output, divided by L^3, where L is the box size.
     The box sizes of the simulations can be 50, 60, 80 or 120Mpc/h.
     It is also and normalized by the mean F of that redshift, given by:
     \bar{F}(z) = exp(-0.0023(1+z)^3.65), as long as is not said otherwise.
5. P_F: transmission power spectrum at k,mu, obtained from the simulation
     output, divided by L^3.
6. w=n_F: number of independent modes contributing to this bin, from all
     three projections of the simulation. This number grows as k^3.
7. error=sigma_P: error computed from the number of independent modes,
   using epsilon=0.05 in equation 3.2. 

-------------------------------------------------------------------

Files for bias results from low-k points: ending in .res
These files contain the bias factors and errors as obtained only from the
values of P_F/P_L at the lowest k-modes, instead of the overall fit.
The wavenumbers used are generally all the modes with k < 2.7 k_1, where
k_1= (2pi)/L is the lowest wavenumber.
A linear regression is obtained to all the values of the expression:
 sqrt(P_F/P_L) = b_{Fdelta}(1+ beta mu^2)
The linear regression is obtained for these set of values with k < 2.7 k_1,
which turn out to have a mean mu^2 = 1/3= 0.33333. The calculations are
done by the code biaslk.f.
Each file of each simulation gives 5 rows for the 5 redshifts,
 z=2.2, 2.4, 2.6, 2.8, 3.0, and each row gives 10 numbers:
1. Slope, b_{Fdelta}*beta = f(Omega)*b_{Feta}
2. Error on the slope
3. Intercept at the mean mu^2, b_{Fdelta}(1+1/3*beta)
4. Error on the intercept at the mean mu^2.
5. b_{taudelta}
6. Error on b_{taudelta}
7. b_{taueta}
8. Error on b_{taueta}
9. beta
10. Error on beta
Note that the errors on the slope and the intercept at the mean mu^2 are
 uncorrelated, the other errors are computed combining these two quadratically.

The file L120F.res is computed by averaging a greater number of modes in the
L120 simulation, for k < 5.4 k_1.

