# Level 0 data

This directory contains simulated JWST data for the challenge level 0. For this level the groundtruth is given to all modellers.

The data is a 5" wide view of a galaxy-galaxy strong lens that contains a single subhalo, as it would be observed in the NIRCam/F200W filter on JWST. All observational and instrumental properties have been chosen to be as realistic as possible. The exposure time has been set to 1000 seconds, which is more or less in the middle range of strong lensing JWST data sets that are currently publicly available.

The properties of the strong lens system are as follows:
- lens mass distribution = EPL + shear
- subhalo mass distribution = truncated spherical NFW
- lens light distribution = elliptical Sérsic
- source light distribution = elliptical Gaussian

This directory contains the following files:

- `mock-20241129_181219-NIRCAM_F200W-SEED_86429.fits`: multi-extension FITS file the following arrays:
    - 1 (`SCI`): the full imaging data.
    - 2 (`ERR`): the noise map, which is the total standard deviation of the noise per pixel.
    - 3 (`PSF`): the PSF at the data resolution.
    - 4 (`LENS_LIGHT`): the true lens light distribution, **to be subtracted from the imaging data** if not modelled.
    - 5 (`MODEL`): the clean simulated image (i.e. `SCI` without noise).
    - 6 (`MODEL_UNCOV`): the unconvolded simulated image.
    - 7 (`SUBPOT`): subhalo potential (projected onto the data grid).
    - 8 (`SUBKAPPA`): subhalo convergence (projected onto the data grid).
    - 9 (`PSF_SUPER`): supersampled PSF, 7 times the data resolution.

- `mock-20241129_181219-NIRCAM_F200W-SEED_86429.csv`: CSV file containing the parameters of the simulation:
    - `XXX-c_x`, `XXX-c_x`: position along the _x_ and _y_ axes.
    - `XXX-q`: axis ratio
    - `XXX-phi`: position angle (radians), computed counterclockwise from the positive _x_ axis.
    - `XXX-theta_Ein`: Einstein radius (arcsec).
    - `XXX-gamma`: logarithmic mass density slope (arcsec), 2 being an isothermal profile.
    - `lens_mass-gamma_ext`: shear strength.
    - `lens_mass-phi_ext`: shear position angle (radians), computed counterclockwise from the positive _x_ axis.
    - `lens_light-I_eff`: half-light intensity.
    - `lens_light-r_eff`: half-light radius (arcsec).
    - `lens_light-n_sersic`: Sérsic index.
    - `source_light-I_0`: central intensity.
    - `source_light-sigma`: Gaussian standard deviation (arcsec).
    - `subhalo_mass-log10(m200)`: logarithm of the M_200 mass of the subhalo (~ virial mass).
    - `subhalo_mass-log10(c200)`: logarithm of the c_200 concentration of the subhalo.
    - `subhalo_mass-tau`: ratio of the truncation radius to the scale radius of the subhalo.
    - `z_d`, `z_s`, `z_sub`: redshift of the deflector / lens, the source, the subhalo.
    - `H0`, `Om0`, `Ode0`, `Ok0`: cosmological parameters of Astropy's `LambdaCDM`.
    - `pix_scl`: pixel size (arcsec) of the data.
    - `x_pixel0`, `y_pixel0`: model coordinates of pixel [0, 0].

Note that the headers of the FITS file extensions also extra contain some complementary information.
