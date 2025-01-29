# tp_spark

1. charger un fichier txt en rdd
rdd = sc.textFile('/workspaces/...')

2. type de la variable
type(rdd) #pour l'objet rdd

rdd_type = rdd.map(lambda x: type(x))
rdd_type.take(n) #Pour les types des éléements dans le rdd

df.printSchema() #affiche le schéma complet du data frame dont le type des colonnes
df.shema["nomColonne"].dataType #affiche le type spécifique pour une colonne du data frame

3. première ligne 
rdd.first()

4. combien il y a de ligne dans un fichier
rdd.count()

5. le nombre de ligne contenant un certain mot
rdd_ligne = rdd.filter(lambda ligne: "mot" in ligne.lower())
rdd_ligne.count()

7. la longueur d'un mot
len('mot')

8. l'occurence pour un mot
rdd_map = rdd.flatMap(lambda line: line.split(" "))
rdd_map.take(n)  #Pour déclencher la transformation on applique une action
rdd_couple = rdd_map.map(lambda mot: (mot,1))
rdd_count = rdd_couple.reduceByKey(lambda x,y: x+y)
rdd_count.take(n) #Résultat du map reduce des n premiers résultats

9. comment faire un cache et comment le déclencher
rdd.persist()
rdd.count()
