========================================================================
ESTRUCTURA DE DIRECTORIOS Y ARCHIVOS - ANDE PLUGIN v3.4 "Legado" (12 Marzo)
========================================================================
Ruta de instalación local: 
C:\Users\[usuario]\AppData\Roaming\QGIS\QGIS3\profiles\default\python\plugins\ande_plugin\

ande_plugin/                      # Directorio Raíz del Plugin
│
├── __init__.py                   # Punto de entrada exigido por QGIS. Inicializa el plugin.
├── metadata.txt                  # Metadatos del plugin (versión, autor, descripción, tags).
├── ande_plugin.py                # CONTROLADOR (MVC): Orquesta la UI y llama a los procesos lógicos.
├── ande_plugin_dialog.py         # VISTA (MVC): Clase Python que carga y maneja la ventana interactiva.
├── ande_plugin_dialog_base.ui    # VISTA (MVC): Archivo XML de diseño gráfico generado en Qt Designer.
├── icon.png                      # Icono oficial del plugin mostrado en la barra de herramientas.
│
├── core/                         # MODELO (MVC): Carpeta con el "Cerebro" y lógica de negocio.
│   ├── __init__.py               # Convierte la carpeta 'core' en un módulo de Python importable.
│   │
│   ├── (Módulos de Baja Tensión - BT Unificada)
│   ├── generador_lineas.py       # Algoritmo de trazado inicial para red BT.
│   ├── segmentador_lineas.py     # Corta las líneas BT generadas en cada poste.
│   ├── fusionador_lineas.py      # Une tramos segmentados (Union-Find) eliminando superposiciones.
│   ├── normalizadorbt.py         # Limpia atributos, impone estándar corporativo y renombra capa BT.
│   │
│   ├── (Módulos de Media Tensión - MT)
│   ├── generador_lineas_mt.py    # Algoritmo de trazado para red MT (soporta vanos largos 120m+).
│   ├── segmentador_lineas_mt.py  # Corta las líneas MT generadas en cada poste.
│   ├── fusionador_lineas_mt.py   # Une tramos segmentados en circuitos continuos MT.
│   ├── divisor_transformadores.py# Motor espacial que corta la línea MT al intersectar un PD/Equipo.
│   ├── normalizador.py           # Estándar MT, renombra capa y usa "Bulk Delete" para no saturar RAM.
│   │
│   ├── (Módulos Complementarios y Auditoría - Toolbox)
│   ├── qa_topologico.py          # [NUEVO] CENTINELA: Auditoría topológica Anti-FME y exportador CSV.
│   ├── procesador_acometidas.py  # Genera líneas cliente-poste inyectando ID continuo en capa oficial.
│   ├── procesador_luminarias.py  # Conecta puntos de luz (AP) a la red respetando ejes de calles.
│   ├── procesador_equipos.py     # Filtra elementos de maniobra (Seccionadores/Reconectadores).
│   ├── procesador_terminales.py  # Auditoría QA/QC de postes marcados como "Terminal" en texto vs mapa.
│   └── procesador_lineas_disponibles.py # Calcula "Cupos" restando líneas físicas de la capacidad del poste.
│
└── utils/                        # (Opcional) Carpeta para funciones de ayuda futuras.
    └── (vacío o herramientas menores de formato/log)

========================================================================
NOTA DE ARQUITECTURA:
Si se necesita modificar la Interfaz Gráfica, editar .ui en Qt Designer.
Si se necesita modificar el Trazado o Atributos, editar archivos dentro de /core/.
Si se necesita modificar las Acciones de los botones, editar ande_plugin.py.

========================================================================
