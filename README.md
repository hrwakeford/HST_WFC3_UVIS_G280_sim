## HST WFC3 UVIS G280 grism timeseries precision calculator 

This program was created by H.R.Wakeford
2020 Feb 6

It has been checked against the HAT-P-41b data obtained through GO-15288 
(PIs: D.K.Sing & N.K.Lewis) when compared to the ETC. 
These measurements reached photon noise limits which is what the ETC estimates. 
See Simulator_comparison_to_Wakeford2020.ipynb for a direct comparison.

Credit: H.R. Wakeford, when using ETC inputs please also credit the ETC in your proposals

Citation: [Wakeford et al. (2020), AJ, 159](https://ui.adsabs.harvard.edu/abs/2020AJ....159..204W/abstract)

___
Contents
- find_nearest(array, value):
- transit_depth_precision(wavelength,spectrum,wav_range,exptransit):
- UVIS_simulation(data_folder,file_name,exposure_time,orbits_in_transit,no_of_transits, mode):

___
	INPUT:
	`data_folder = '..Data/'`
		The place where the ETC output file located
		The ETC file needs to contain the following information in the correct structure. 
		This file can be self generated if also in this structure.
		(wavelength (A), readnoise, dark_counts, sky_counts, target_counts, total_counts)
		Columns 0 and 4 are used in this calculation, please maintain these column 
		positions for self input files
		Wavelength is input from this file in Angstroms 

	`file_name = ['H41_ETC']`
		This can be an array of filenames 
		make sure it is always in square brackets

	`exposure_time = [190]` 
		This is an array of exposuretimes corresponding to the 
		filenames listed in file_name
		make sure it is always in square brackets

	`orbits_in_transit = [2]` 
		This is an array of the number of HST orbits inside a single
		transit (not the total observation) corresponding to the
		filenames listed in file_name
		make sure it is always in square brackets

	`no_of_transits = [2]` 
		This is an array of the number of transits of each targets 
		in your program corresponding to the filenames listed in
		file_name make sure it is always in square brackets
	
	`wl = [2000,8000]`
		default value spans the maximum range of the grism. This will 
		calculate the broadband signal that will be the first line of
		the produced file. 
	
	`startw = 2000`
		This is the starting range for your spectral bins.
		Default is at minimum = 2000 angstroms. 
		Where this might be changed is for small stars with little 
		flux in the short wavelengths. Or if simulating the -1 order

	`endw = 8000`
		This is the end of the spectral binning range
		Default set to the maximum, 8000 angstroms

	`binlen = 100`
		This is in angstroms and specifies the size of the 
		spectral bins in wavlength space. 
		Minimum reccomended = 60 angstorms (Wakeford et al 2020 = 100)

	`out_name = 'string'`
		This is what you want the output specified as in addition 
		to the input name.

	OUTPUT:
	data file for each input planet file:
	output name = {data_folder}{file_name}.UVIS_{out_name}_sim.txt'
		contains the broadband {wl} and spectroscopic precisions ({binlen} bins) 
		wavelength (nm), bin size (nm), precision per transit (ppm), precision per target (ppm)
___