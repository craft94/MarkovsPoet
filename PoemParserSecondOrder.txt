import numpy as np
import random as rand
Shakespeare = open("ShakespeareSonnetsOneLine.txt", "r")
ShakeBank = Shakespeare.read()

def PoemParser(PoemAsString):
	PoemLower = PoemAsString.lower()
	PoemAsString = PoemLower.split()
	return PoemAsString
	
def UniqueWordList(List):
	unique = set(List)
	return unique
			
def BiconditionalDictionary(UniqueList, ForwardOrBackward):
	if(ForwardOrBackward == 0):
		#return number to word dictionary
		return dict(enumerate(UniqueList))
	else:
		#return word to number dictionary
		return {v: k for k, v in dict(enumerate(UniqueList)).items()}
	
def TransitionCreator(UniqueList):
	return np.zeros([len(UniqueList),len(UniqueList)])

def IndexOfWordInBank(UniqueWordNumber, UniqueWordList, ListOfAllWords):
	indices = [j for j, m in enumerate(ListOfAllWords) if m == UniqueWordNumber]
	return indices

def NextWord(PlaceOfWordVector):
	return np.array(PlaceOfWordVector) + 1
	
def TransitionRowPopulator(RowNumber, RowAsVector, ListOfAllWords):
	
	return 0
	
def Main():
	List = PoemParser(ShakeBank)
	unique = UniqueWordList(List)
	Num2WordDict = BiconditionalDictionary(unique,0)
	Word2NumDict = BiconditionalDictionary(unique,1)
	CurrentWord = rand.randint(0,len(List)-1)
	#print(List[CurrentWord])
	#for i in unique:
	#	PlaceOfWord = IndexOfWordInBank(i, unique, List)
	#	NextWordinNumber = NextWord(PlaceOfWord)
	#	for n in NextWordinNumber:
	#		print(List[n%len(List)])
	for l in range(0,16):
		for w in range(0,6):
			print(List[CurrentWord] + " ", end="")
			PlaceOfWord = np.where(np.asarray(List)==List[CurrentWord])
			#IndexOfWordInBank(CurrentWord, unique, List)
			#print(PlaceOfWord[0])
			NextWordinNumber = (PlaceOfWord[0] + 1)%(len(List)-1)
			CurrentWord = rand.choice(NextWordinNumber)
		print("")
	print("")
	x = input("How was that?")
	
	
Main()