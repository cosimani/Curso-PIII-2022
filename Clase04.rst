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


.. code-block:: python

	import numpy as np
	import matplotlib.pyplot as plt

	# Variables independientes
	x1 = np.linspace( 1, 12, 12 )
	x2 = np.linspace( 1, 12, 12 ) + 2
	x3 = np.linspace( 1, 12, 12 )
	x4 = x2 + x3

	# Para varios gráficos es útil usar la función subplots y luego axs
	# Documentación de subplots en: https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.subplots.html
	fig, axs = plt.subplots( nrows = 2, ncols = 2 )  
	fig.set_figwidth( 10 )
	fig.set_figheight( 6 )

	axs[ 0, 0 ].plot( x1, x2 )
	axs[ 0, 0 ].set_title( 'Gráfico 1' )
	axs[ 0, 0 ].set_xlabel( 'x' )
	axs[ 0, 0 ].set_ylabel( 'y' )

	axs[ 0, 1 ].plot( x1, x3 )
	axs[ 0, 1 ].set_title( 'Gráfico 2' )
	axs[ 0, 1 ].set_xlabel( 'x' )
	axs[ 0, 1 ].set_ylabel( 'y' )


	axs[ 1, 0 ].plot( x1, x4 )
	axs[ 1, 0 ].set_title( 'Gráfico 3' )
	axs[ 1, 0 ].set_xlabel( 'x' )
	axs[ 1, 0 ].set_ylabel( 'y' )

	axs[ 1, 1 ].scatter( x1, x4 )  # scatter plot = Diagrama de dispersión
	axs[ 1, 1 ].set_title( 'Gráfico 4' )
	axs[ 1, 1 ].set_xlabel( 'x' )
	axs[ 1, 1 ].set_ylabel( 'y' )

	plt.show()


.. code-block:: python

	import numpy as np
	import matplotlib.pyplot as plt

	x1 = np.linspace( 1, 12, 12 )
	x2 = np.linspace( 1, 12, 12 ) + 2

	fig, axs = plt.subplots( nrows = 2, ncols = 2 )  

	axs[ 0, 0 ].plot( x1, x2 )
	axs[ 0, 1 ].plot( x1, x2, 'g--d' )  
	axs[ 1, 0 ].scatter( x1, x2 )  
	axs[ 1, 1 ].stem( x1, x2 )
	plt.show()

Entregable Clase 04
===================

- Punto de partida: Usar Spyder para escribir el código desde cero
- Replicar exactamente la siguiente secuencia:

.. figure:: images/clase04_plot.png

- Explicar a medida que se vaya haciendo el ejercicio.
- Entrar al siguiente `link para ver el registro de los entregables <https://docs.google.com/spreadsheets/d/1Qpp9mmUwuIUEbvrd_oqsQGuPOO9i1YPlHa_wBWTS6co/edit?usp=sharing>`_ 
- En caso de compartir video, se realiza en Youtube (No listado) compartiendo con el docente por mensaje privado de Teams (antes de finalizar el día).
- Si se requiere de más tiempo para compartir el video, escribir al docente por WhatsApp para proponer nuevo horario.
- `Mesas de trabajo en Discord <https://discord.gg/TFKzMXrNCV>`_ 


**Alternativa para la creación de entornos virtuales**

- Módulo *venv*
- `Documentación de venv <https://docs.python.org/3/library/venv.html>`_ 
- Adaptar los siguientes comandos a lo visto en la `Clase 01 <https://github.com/cosimani/Curso-PIII-2021/blob/main/Clase01.rst>`_ 
- Este módulo ya viene instalado con Python (quizás debemos asegurarnos de esto durante la instalación)

.. code-block:: bash 

	cd C:\Cosas\2021\PIII2021\EntornosVirtuales  # Accedemos a la carpeta en donde creamos los entornos virtuales
	python -m venv entorno04                     # Creamos el entorno virtual
	.\entorno04\scripts\activate.bat             # Activamos el entorno virtual

	deactivate                                   # Desactivamos el entorno virtual

	# Para borrar el entorno virtual hay que borrar la carpeta donde se creó -> C:\Cosas\2021\PIII2021\EntornosVirtuales\entorno04
