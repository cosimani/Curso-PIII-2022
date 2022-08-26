.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 05 - PIII 2022
====================
(Fecha: 26 de agosto)



Biblioteca numpy
================

- Vectores, matrices, gran colección de funciones matemáticas.
- `Documentación de numpy <https://numpy.org/doc/stable/index.html>`_ 


**Algunos ejemplos de su uso**

.. code-block:: python

	import numpy as np

	lista = [ 25., 8., 20., 75. ] 
	print( type( lista ), lista )

	v = np.array( lista )  # Transformo la lista en vector
	print( '\nv =', v )  # El vector no lleva comas separando los elementos
	print( 'tipo de v:', type( v ) )  # el tipo es numpy.ndarray
	print( 'longitud de v:', len( v ) )

	# máximo y mínimo valor de v
	print( 'máximo de v:', v.max(), 'o', np.max( v ) )  # función de numpy.ndarray: np.max()
	print( 'mínimo de v:', v.min(), 'o', np.min( v ) )


.. code-block:: python

	import numpy as np

	u = np.array( [ 5, 9, 10, -1 ] )  # Transforma la lista en vector
	v = np.array( [ -2, 0, 5, 4 ] )

	print( "vector u =", u )
	print( "vector v =", v )

	z = u + v 
	print( "z = u + v  ->  z =", z )

	w = 2 * z
	print( "2 * z =", w )

	t = w - 3
	print( "Restamos 3 a cada elemento del vector anterior", t )

.. code-block:: python

	import numpy as np

	v = np.zeros( 4, dtype = np.float32 )
	u = np.ones( 4, dtype = np.int64 )
	w = np.full( 4, 128, dtype = np.int8 )
	print( "v =", v,"   u =", u, "   w =", w )

.. code-block:: python

	import numpy as np

	s = np.arange( 5, 26, 3 )
	print( s, type( s ), type( s[ 0 ] ) )

	t = s.astype( np.float32 )  # cambiamos el tipo de datos al vector s a float32
	print( t, type( t ), type( t[ 0 ] ) )

	r = t[ 0 : 3 ]
	print( '\nLos 3 primeros elementos de t son:', r )
	print( 'Muestra 1 =', t[ 3 : ] )
	print( 'Muestra 2 =', t[ : ] )
	print( 'Muestra 3 =', t[ : 5 ] )

	p = t[ [ 1, 3, 5 ] ]
	print( 'Vector con los lugares pares de t:', p )

	lineal = np.linspace( 0, 1, 5 )
	print( lineal )



Biblioteca matplotlib
=====================

- Generador de gráficos.
- `Documentación de matplotlib <https://matplotlib.org/>`_ 


**Algunos ejemplos de su uso**

.. code-block:: python

	import matplotlib.pyplot as plt
	import numpy as np

	n = 21
	x = np.linspace( 0, 2, n )  # del 0 al 2 (inclusive), en n=21 números equiespaciados
	x2 = x * x
	x3 = x ** 3
	plt.plot( x, x, 'b.', x, x2, 'rd', x, x3, 'g^' )

	plt.xlim( -1, 2.5 )  # límites para el eje x
	plt.gca().legend( ( 'Lineal', 'Cuadrática', 'Cúbica' ) )

	plt.show()


.. code-block:: python

	import matplotlib.pyplot as plt
	import numpy as np

	n = np.arange( 0, 5, 1 )
	y = np.exp( np.sin( n ) )

	plt.stem( n, y )
	plt.show()



Entregable 03
=============

- Punto de partida: Entorno virtual creado y usando Spyder o Sublime Text para escribir el código fuente
- Considere la siguiente función: ``y = np.cos( n ) )``
- Es una secuencia, es decir, una señal discreta, en función de ``n``.
- Publique los primeros 50 valores que toma ``y`` modificando a cero los que son menores a cero.
- Ayudarse con este código:

.. code-block:: python

	y = [ 2, 3, 4, 5, 6, 7 ]
	r = [ 0, 0, 1, 1, 0, 1 ]

	res = np.array( [ 0 if r[ i ] == 0 else a for i, a in enumerate( y ) ] )
	#=> [ 0, 0, 4, 5, 0, 7 ]

- Realizar otro gráfico con una secuencia senoidal que tenga 12 muestras por ciclo.

- Entrar al siguiente `link para ver el registro de los entregables <https://docs.google.com/spreadsheets/d/1VoiVIgvt3YoovQd4rFNI_tZY8dY8n2t-qkV3o7WgaOY/edit?usp=sharing>`_ 



