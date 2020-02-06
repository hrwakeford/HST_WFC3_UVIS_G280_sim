This program was created by H.R.Wakeford
2020 Feb 6

It has been checked against the HAT-P-41b data obtained through GO-15288 
(PIs: D.K.Sing & N.K.Lewis) when compared to the ETC. 
These measurements reached photon noise limits which is what the ETC estimates.
Credit: H.R. Wakeford, when using ETC inputs please also credit the ETC in your proposals
Citation: Wakeford et al. (2020), AJ in review

This simulator will produce precisions for a transmission spectrum in 20nm bins from 
200-800nm and the broadband transit depth precision, and emission spectrum in 120nm 
bins from 200-800nm and the broadband eclipse depth precision.

Contents
- find_nearest(array, value):
- transit_depth_precision(wavelength,spectrum,wav_range,exptransit):
- UVIS_simulation(data_folder,file_name,exposure_time,orbits_in_transit,no_of_transits, mode):



	INPUT:
	data_folder = '..Data/' 
	The place where the ETC output file located
	The ETC file needs to contain the following information in the correct structure. 
	This file can be self generated if also in this structure.
	(wavelength (A), readnoise, dark_counts, sky_counts, target_counts, total_counts)
	Columns 0 and 4 are used in this calculation, please maintain these column 
	positions for self input files
	Wavelength is input from this file in Angstroms 

	file_name = ['PLANET'] 
	This can be an array of filenames 
	make sure it is always in square brackets

	exposure_time = [12] 
	This is an array of exposuretimes corresponding to the 
	filenames listed in file_name
	make sure it is always in square brackets

	orbits_in_transit = [4] 
	This is an array of the number of HST orbits in a single
	transit corresponding to the filenames listed in file_name
	make sure it is always in square brackets

	no_of_transits = [2] 
	This is an array of the number of transits of each targets 
	in your program corresponding to the filenames listed in file_name
	make sure it is always in square brackets

	OUTPUT:
	data file for each input planet file:
	output name = 'data_folder + file_name + .UVISsimulation.txt'
	contains the broadband (200-800nm) and spectroscopic precisions (20nm bins) 
	wavelength (nm), bin size (nm), precision per transit (ppm), precision per target (ppm)
