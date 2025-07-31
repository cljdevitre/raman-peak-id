# RamanID
 RamanID (created by C. Devitre - https://github.com/cljdevitre/raman-peak-id) is designed to ID Raman spectra by comparison with spectral databases (right now - RRUFF). It’s built on top of RamanSpy (https://ramanspy.readthedocs.io/en/latest/). 
 It is built to use with Jupyter notebooks at present. I am not responsible for any conclusions drawn from peak matching. Users should use caution and common sense when trying to ID spectra. RamanID may wrong, I am not responsible and cannot be held liable for the accuracy of the results. Please mention my Github when using RamanID!

 The current version uses Pearson’s product-moment correlation coefficient (calculated using scipy https://scipy.org), but will be expanded. The coeff ( r ) is the square root of the covariance divided by product of the standard deviations for the spectra. x is normalized intensity at a specific wavenumber for spectrum 1, mx is the mean of x spectrum, y and my the same for y spectrum. This is why it has 3 conditions: 

 1) normalize the data so that the spectra are comparable (you are looking at shape, not absolute intensity); 2) ensure that the wavenumber axes are aligned (therefore interpolate one to ensure that its axis matches the other one); 3) the axes have the same range (crop both to the same relevant region). If r=1 the variables are perfectly linearly correlated and have a positive slope (when one increases with respect to its mean, so does the other). If r=-1, they are perfectly correlated but in opposite directions (one increases while the other decreases). If r=0, no correlation. So the closer you are to 1 (or 100% similarity), the better the match between the spectra. 
 
 The default normalization right now is MinMax but is easy to tweak with RamanSpy’s built-ins. 
 
 You can load RRUFF spectra directly from the internet if you wish, but it can be slow and can fail if there are bad spectra. Otherwise, I’ve included a slightly cleaned up version of RRUFF that will load with no issues.
 
 Note that RRUFF spectra do not extend to high wavenumbers, so it is not worth trying to compare high wave number regions (regardless, most of the vibrations of interest will actually be in the low wavenumber regions for minerals).
 