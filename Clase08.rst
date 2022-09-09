.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 08 - PIII 2022
====================
(Fecha: 9 de septiembre)


Biblioteca SciPy
================
 
- Espacios vectoriales, integración, interpolación, FFT, procesamiento de señales y de imagen, ...
- `Documentación de SciPy <https://docs.scipy.org/doc/scipy/reference/>`_ 


`Operaciones entre señales (ipynb) <https://colab.research.google.com/drive/1rApDU5c70ApnZjSs0H-kJqpVp230Seoj?usp=sharing>`_ 
=====================================

.. code-block:: python
	
	import matplotlib.pyplot as plt
	plt.style.use( 'seaborn-darkgrid' )

	import numpy as np
	from scipy import signal

	# Para reproducir audio en la notebook.
	from IPython.display import Audio, display

	# señal triangular
	sample_rate = 44100
	duracion = 1
	n = np.linspace( 0, duracion, sample_rate * duracion )
	plt.xlim( [ 0, 0.005 ] )
	triangle = signal.sawtooth( 2 * np.pi * 800 * n, 0.5)
	plt.plot( n, triangle )

	n = np.linspace( 0, 1, 500, endpoint = False )
	square = signal.square( 2 * np.pi * 5 * n )
	plt.plot( n, square )
	plt.ylim( -2, 2 )

	n = np.linspace( 0, 5, 44100 * 5 )
	w = signal.chirp( n, f0 = 1, f1 = 1500, t1 = 5, method = 'quadratic' )
	plt.plot( n, w )
	plt.xlim( [ 0, 2 ] )
	plt.xlabel( 't (sec)' )
	plt.show()

	Audio( w, rate = 44100 )

	# Armar una señal compleja con una función seno.
	def cosenoidal( frecuencia, duracion, sample_rate, A = 1 ) :
	    n = np.linspace( 0, duracion, sample_rate * duracion )
	    return A * np.cos( 2 * np.pi * frecuencia * n )

	def generador_de_tono( frecuencia, duracion, sample_rate, A = 1 ) :
	    n = np.linspace( 0, duracion, sample_rate * duracion )
	    return A * np.sin( 2 * np.pi * frecuencia * n )

	cos_1 = cosenoidal( 300, 5, 44100 )
	cos_2 = cosenoidal( 400, 5, 44100 )
	sin_1 = generador_de_tono( 500, 5, 44100 )
	sin_2 = generador_de_tono( 200, 5, 44100 )
	suma_de_senales = cos_1 + cos_2 + sin_1 + sin_2

	plt.figure()
	t = np.linspace( 0, 5, 44100 * 5 )
	plt.plot( t, suma_de_senales )
	plt.xlim( [ 0, 0.05 ] )
	plt.grid()
	plt.show()

	Audio( suma_de_senales, rate = 44100 )

	mean = 0
	std = 1 
	sample_rate = 44100
	duracion = 5
	num_samples = seconds * sample_rate
	noise = np.random.normal( mean, std, size = num_samples)
	x = np.linspace( 0, duracion, num_samples )
	plt.plot( x, noise )
	plt.show()

	Audio( 0.5 * noise, rate = framerate )

	sin_noise = sin_1 + noise
	Audio( sin_noise, rate = sample_rate )



Entregable 06
=============

- Sumar una onda cuadrada y una onda triangular de igual amplitud y distintas frecuencias humanamente audibles
- Según su percepción auditiva, ¿cuál es la que predomina?
- Diseñar una función que facilite la cuantificación de una secuencia
- Deberá permitir el ingreso como parámetro la cantidad de bits del codificador
- También que permita ingresar el rango de amplitud a codificar
- Entrar al siguiente `link para ver el registro de los entregables <https://docs.google.com/spreadsheets/d/1VoiVIgvt3YoovQd4rFNI_tZY8dY8n2t-qkV3o7WgaOY/edit?usp=sharing>`_ 




