# sudoku

import numpy as np
x = np.random.random((5,5))
print("Original Array:")
print(x) 
xmin, xmax = x.min(), x.max()
print("Minimum and Maximum Values:")
print(xmin, xmax)

def check_location(sudoku,row,col,num):
	for i in range(5):
		if(sudoku[i][col]==num):		
			return False
	for i in range(5):
		if(sudoku[row][i]==num):		
			return False
			

def solve(sudoku):
	row,col=0,0
	for i in range(5):
		flag=1                                                            
		for j in range(5):
			if(sudoku[i][j]==0):
				row,col=i,j
				flag=0
				break
		if(flag==0):
			break
	if(sudoku[i][j]!=0):
		return True
	for i in range(1,4):
		#print(i)
		if(check_location(sudoku,row,col,i)):
			sudoku[row][col]=i
			#print(sudoku)
			if(solve(sudoku)==True):
				return True
			sudoku[row][col]=0
	return False
  
  
