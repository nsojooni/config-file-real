# config-file-real

[model]
name = gaussian_noise
low-frequency-cutoff = 30.0
high-frequency-cutoff = 1024.0
epsilon = 0.03
mass1_ref = 23.2
mass2_ref = 2.59
tc_ref = 1249852257.0

[data]
instruments = H1 L1 V1
trigger-time = 1249852257.0
analysis-start-time = -4
analysis-end-time = 4
psd-estimation = median-mean
psd-segment-length = 8
psd-segment-stride = 4
psd-inverse-length = 8
pad-data = 8
channel-name = H1:GWOSC-4KHZ_R1_STRAIN L1:GWOSC-4KHZ_R1_STRAIN V1:GWOSC-4KHZ_R1$
frame-files = H1:H-H1_GWOSC_4KHZ_R1-1249852241-32.gwf L1:L-L1_GWOSC_4KHZ_R1-124$
strain-high-pass = 10
sample-rate = 2048

[sampler]
name = emcee_pt
ntemps = 4
nwalkers = 100
niterations = 300

[sampler-burn_in]
burn-in-test = min_iterations
min-iterations = 100

[variable_params]
; waveform parameters that will vary in MCMC
tc =
distance =
inclination =
mchirp =
q =
;eccentricity =

[static_params]
; waveform parameters that will not change in MCMC
approximant = TaylorF2
f_lower = 30
#; we'll choose not to sample over these, but you could
polarization = 0.0
ra = 0.218
dec = -0.436

#; You could also set additional parameters if your waveform model supports / requires it.
; spin1z = 0

;[prior-eccentricity]
;name = uniform
;min-eccentricity = 0
;max-eccentricity = 0.1

[prior-q]
; q prior
name = uniform
min-q = 8
max-q = 10

[prior-mchirp]
; chirp mass prior
name = uniform
min-mchirp = 6.3
max-mchirp = 6.5

[prior-tc]
; coalescence time prior
name = uniform
min-tc = 1249852256.9
max-tc = 1249852257.1

[prior-distance]
#; following gives a uniform in volume
name = uniform_radius
min-distance = 10
max-distance = 500

[prior-inclination]
name = sin_angle

[waveform_transforms-mass1+mass2]
; transform from mchirp, q to mass1, mass2 for waveform generation
name = mchirp_q_to_mass1_mass2
