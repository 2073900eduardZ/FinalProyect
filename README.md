
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
