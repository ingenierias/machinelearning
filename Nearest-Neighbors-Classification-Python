import csv
import random
import math
import operator

def loadCsv(filename):
	lines = csv.reader(open(filename, "rb"))
	dataset = list(lines)
	n_feature = len(dataset[0])-1
	for x in range(len(dataset)-1):
		for y in range(n_feature):
			dataset[x][y] = float(dataset[x][y])
	return dataset

def splitDataset(dataset, splitRatio):
	trainSize = int(len(dataset) * splitRatio)
	trainSet = []
	copy = list(dataset)
	while len(trainSet) -1 < trainSize:
		index = random.randrange(len(copy))
		trainSet.append(copy.pop(index))
	return [trainSet, copy]


def euclidiana(valor1, valor2):
	distance = 0
	n_features = len(valor2)
	for x in range(n_features):
		distance += pow(float(valor1[x]) - float(valor2[x]), 2)
	return math.sqrt(distance)

def vecino(dataset,prueba):
	distancia = 0
	distances = []
	for n in range(len(dataset)):
		distancia = euclidiana(dataset[n],prueba)
		distances.append((dataset[n],distancia))
	distances.sort(key=operator.itemgetter(1))
	return distances

def getAccuracy(testSet, predictions):
	correct = 0
	for x in range(len(testSet)):
		if testSet[x][-1] is predictions[x]:
			correct += 1
	return (correct/float(len(testSet))) * 100.0
	
def main():
	archivo = 'iris.data'
	limiar = 0.7
	datos = loadCsv(archivo)
	datos_entrenamiento, testData = splitDataset(datos,limiar)
	prueba_single = [4.7, 3.2, 1.3, 0.2]#iris
	distancias = vecino(datos_entrenamiento,prueba_single)
	print distancias
main()
