.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 16 - PIII 2022
====================
(Fecha: 17 de octubre)



Creación de GUI
===============

- QtDesigner para diseñar una interfaz con modalidad Drag and Drop.
- Creación de entorno virtual
- Instalación de bibliotecas
- Características de la biblioteca Qt
- Manejo de eventos
- Gráficos y reproducción

**Información**

- Ir a https://www.qt.io/download para descargar el QtCreator. No hace falta más que el QtCreator que tiene el QtDesigner que nos genera el .ui
- Ver aquí cómo se utiliza el .ui para generar la interfaz. https://www.pythonguis.com/tutorials/pyside-first-steps-qt-designer/


.. code-block:: bash 

	cd C:\Cosas\EntornosVirtuales
	mkdir PIII_con_GUI
	cd PIII_con_GUI

	virtualenv entorno_gui_piii
	.\entorno_gui_piii\Scripts\activate

	pip install numpy==1.19.5
	pip install shiboken6==6.0.0
	pip install PySide6==6.0.0 
	pip install matplotlib==3.3.4 
	pip install scipy==1.7.1
	pip install sounddevice==0.4.2

	python C:\Cosas\PIII\Codigos\GUI\ventana.py



- `Aquí un instructivo para creación de GUI <https://github.com/cosimani/Curso-PIII-2021/blob/main/images/Instructivo_GUI.pdf>`_ 


.. figure:: images/gui_parte1.png


Entregable Clase 18
===================

- Diseñar la interfaz anterior y ejecutar la aplicación.
- Agregar las funciones de generación de tonos y graficar la suma de varios tonos y reproducirlos.
- En el siguiente `link el registro de los entregables <https://docs.google.com/spreadsheets/d/1VoiVIgvt3YoovQd4rFNI_tZY8dY8n2t-qkV3o7WgaOY/edit?usp=sharing>`_ 





