.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 04 - PIII 2022
====================
(Fecha: 22 de agosto)


IDE para Python
^^^^^^^^^^^^^^^

- Descargar `Spyder <https://www.spyder-ide.org/>`_
- Versión actual: 5.3.2
- Instalar para todos los usuarios.

Módulos y paquetes
==================

**Módulo**: Es un archivo Python cuyas utilidades (funciones, clases, etc.) se pueden usar desde otro archivo.

- Supongamos el archivo ``matematicas.py``

.. code-block:: python 

	def sumar( a, b ) :
	    return a + b

	def restar( a, b ) :
	    return a - b

- Podremos utilizar estas funciones de la siguiente manera:

.. code-block:: python

	import matematicas  # Esta línea importa todos los recursos del archivo matematicas.py

	print( matematicas.sumar( 7, 5 ) )
	print( matematicas.restar( 17, 15 ) )

- Si sólo deseamos importar la función ``sumar`` hacemos:

.. code-block:: python

	from matematicas import sumar

	print( sumar( 7, 5 ) )

- Otras alternativas:

.. code-block:: python
	
	from matematicas import sumar, restar

	from matematicas import *


**Paquetes**: Es una carpeta que contiene varios módulos. 

.. code-block:: bash 

	operaciones/
	    |-- __init__.py    # Este archivo indica que la carpeta operaciones es un paquete y no una simple carpeta 
	    |-- matematicas.py
	    |-- matrices.py


- Alternativas para importar

.. code-block:: python
	
	import operaciones.matematicas

	from operaciones import matematicas

	from operaciones.matematicas import sumar


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


Entregable 03
=============

- Punto de partida: Entorno virtual creado y usando Spyder o Sublime Text para escribir el código fuente
- Considere la siguiente exponencial: ``y = np.exp( np.sin( n ) )``
- Es una secuencia, es decir, una señal discreta, en función de ``n``.
- Publique los primeros 5 valores positivos que toma ``y`` a partir del cero inclusive.
- Entrar al siguiente `link para ver el registro de los entregables <https://docs.google.com/spreadsheets/d/1VoiVIgvt3YoovQd4rFNI_tZY8dY8n2t-qkV3o7WgaOY/edit?usp=sharing>`_ 








