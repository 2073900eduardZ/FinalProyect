<<<<<<< HEAD
<<<<<<< HEAD

# Huellas evolutivas en felinos

# Edward Oña

Este proyecto compara las huellas evolutivas del tigre (Panthera tigris) y el león (Panthera leo) mediante el análisis filogenético de dos genes ortólogos obtenidos de NCBI:
el mitocondrial cytochrome b (MT-CYB) y el nuclear RAG1. Se exploran las diferencias y concordancias evolutivas reflejadas en ambos tipos de ADN, revelando cómo la herencia
materna y biparental contribuyen al entendimiento de la historia evolutiva de estos grandes felinos.
# Como se realizará:
•Obtención de secuencias genéticas de Panthera tigris y Panthera leo atravez del NCBI para comparar tanto el gen mitocondrial como nuclear
•Alineación de secuencias
•Construcción de árboles filogenéticos
•Comparación de resultados en ambos tipos

![ ](https://cdn.pixabay.com/photo/2018/01/09/10/56/animal-3071324_1280.jpg)

# Requisitos para ejecutar el programa
•Esearch
•datasets
•MAFFT
•IQ-TREE
•Astral (Java)
•Git
•Figtree

# Como usar los programas?
1. Buscar y descargar las secuencias de las especies elegidas (*Panthera tigris* y *Panthera leo*) junto con los nombres de los genes “cytochrome b” (mitocondrial) y “RAG1” (nuclear) en NCBI GenBank, usando `esearch` y `efetch`.
2. Descargar las secuencias en formato FASTA y guardarlas en archivos separados.
3. Pegar cada secuencia FASTA en la herramienta BLAST de NCBI para confirmar que corresponde correctamente al organismo seleccionado.
4. Alinear las secuencias con MAFFT:

mafft --auto <archivo.fasta> > <archivo_alineado.fasta>

5. Ejecutar IQ-TREE para inferir los árboles filogenéticos de cada gen alineado:

iqtree -s <archivo_alineado.fasta> -m TEST -bb 1000 -nt AUTO

6. Repetir el proceso para ambos genes: uno mitocondrial (*cytb*) y uno nuclear (*RAG1*).
7. Usar Astral para construir un árbol especie combinando árboles de genes individuales:

java -jar astral.jar -i genes_combinados.tree -o arbol_especie.tree

8. Visualizar los archivos `.treefile` generados en FigTree para comparar la topología filogenética entre los genes.
9. Analizar cómo difieren o coinciden los árboles según si el gen es mitocondrial o nuclear.
10. Subir los resultados a GitHub si es necesario:

git add .
git commit -m "Árboles mitocondrial y nuclear Panthera"
git push


![ ](https://www.petdarling.com/wp-content/uploads/2020/11/felinos-salvajes.jpg)
=======
# Idea proyecto
=======
##Análisis Comparativo de
Genes Mitocondriales  y Nucleares en Panthera
>>>>>>> fd581da ( new comment)

Edward Oña

Este proyecto compara las huellas evolutivas del tigre (Panthera tigris) y el león (Panthera leo) mediante el análisis filogenético de dos genes ortólogos obtenidos de NCBI:
el mitocondrial cytochrome b (MT-CYB) y el nuclear RAG1. Se exploran las diferencias y concordancias evolutivas reflejadas en ambos tipos de ADN, revelando cómo la herencia 
materna y biparental contribuyen al entendimiento de la historia evolutiva de estos grandes felinos.
#Como se realizará:
•Obtención de secuencias genéticas de Panthera tigris y Panthera leo atravez del NCBI para comparar tanto el gen mitocondrial como nuclear
•Alineación de secuencias
•Construcción de árboles filogenéticos
•Comparación de resultados en ambos tipos
 
¡ [ ] (https://cdn.pixabay.com/photo/2018/01/09/10/56/animal-3071324_1280.jpg)

## Requisitos para ejecutar el programa
•Esearch
•datasets
•MAFFT
•IQ-TREE
•Astral (Java)
•Git
•Figtree

## Como usar los programas? 
Descargar las secuencias de ADN nuclear y mitocondrial desde el NCBI en formato fasta posteriormente alineamos con MAFFT.
 Ejecutamos IQTREE para crear los arboles de ambos ADNs tanto el mitocondrial como el nuclear. 
Con ayuda de Astral creamos el árbol especie y finalmente abrimos Fig tree para para visualizar las filogenias y poder hacer
 la comparación de los ADNs.Finalmente subimos los resultados al git add, commit y push
## Flujo de trabajo del programa
Este repositorio contiene cuatro scripts principales para realizar un análisis filogenético comparativo
entre Panthera tigris y Panthera leo utilizando genes mitocondriales (cytochrome b)
y nucleares (RAG1). Cada script está diseñado para una etapa específica del pipeline.
Cada script está diseñado para una etapa específica del pipeline. Pueden ejecutarse por separado 
o integrarse en un script maestro (Master_Script.sh) que automatice todo el proceso en un entorno de cómputo como
 Hoffman2 u otro clúster compatible
# 1_descarga_datos.sh
Este es un script en bash que utiliza las herramientas esearch y efetch de Entrez Direct (NCBI) para descargar las secuencias de los genes cytochrome b (mitocondrial) y RAG1 (nuclear) de las especies seleccionadas: Panthera leo y Panthera tigris.

<<<<<<< HEAD
>>>>>>> 99b1d4b (Proyecto final)
=======
* Se descargan las secuencias en formato FASTA.

* Luego se combinan por gen (una secuencia por especie).

* Los archivos se guardan en una carpeta llamada datos/.
# 02_alineamiento_mafft.sh
Este script ejecuta MAFFT para alinear las secuencias descargadas en el paso anterior.

* Se alinean los archivos cytb.fasta y rag1.fasta.

* Se guarda un archivo alineado por cada gen en la carpeta alineamientos/.
# 03_arboles_iqtree.sh
Este script usa IQ-TREE 2 para generar árboles filogenéticos a partir de los alineamientos generados por MAFFT.

Se ejecuta un análisis para cada gen utilizando selección automática de modelo (-m TEST) y bootstrap ultrarrápido (-bb 1000).

Los archivos de salida incluyen el árbol (.treefile) y estadísticos del modelo.

Salida esperada en arboles/:

cytb.treefile, cytb.iqtree

rag1.treefile, rag1.iqtree
# 04_arbol_especie_astral.sh
Este script ejecuta ASTRAL, una herramienta basada en coalescencia para construir un árbol especie a partir de árboles de genes individuales.

Primero, concatena los archivos .treefile generados por IQ-TREE.

Luego ejecuta ASTRAL con ese archivo combinado para generar el árbol especie.

El resultado se guarda en astral/species_tree.tre.
>>>>>>> fd581da ( new comment)
