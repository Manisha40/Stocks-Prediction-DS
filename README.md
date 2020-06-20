# Stocks-Prediction-DS

import numpy as np
X=np.array(([2,9],[1,5],[3,6]),dtype=float)
y=np.array(([92],[100],[89]),dtype=float)

xPredicted=np.array(([4,8]),dtype=float)

X=X/np.amax(X,axis=0)
xPredicted=xPredicted/np.amax(xPredicted,axis=0)
y=y/100

class Neural_network(object);
   def_init_(self):
	self.inputSize =2
	self.outputSize =1
	self.hiddenSize =3

	self.W1 = np.random.randn(self.inputSize,self.hiddenSize)
	self.W2 = np.random.randn(self.hiddenSize,self.outputSize)

def forward(self,X);
	self.z=np.(X,self.W1)
	self.z2=self.sigmoid(selz.z)
	self.z3=np.dot(self.z2,self.W2)
	o=self.sigmoid(self.z3)
	return o

def sigmoid(self,s):
	return 1/(1+np.exp(-s))

def sigmoidPrime(self,s):
	return s*(1-s)

def backward(self,X,y,o):
	self.o_error=y-o
	self.o_delta=self.o_error*self.sigmoidPrime(o)
	
	self.z2_error=self.0_delta.dot(self.W2.T)
	self.z2_delta=self,z2_error*self.sigmoidPrime(self.z2)

	self.W1 +=X.T.dot(self.z2_delta)
	self.W2 +=self.z2.T.dot(self.o_delta)

def train(self,X,y):
	o=self.forward(X)
	self.backward(X,y,o)

def saveWeights(self):
	np.savetxt("w1.txt", self.W1,fmt="%s")
	np.savetxt("w2.txt", self.W2,fmt="%s")

def predict(self):
	print "Predicted data based on trained weights:"
	print "Input(scaled): \n"+str(xPredicted)
	print "Output:\n" +str(self.forward(xPredicted))

NN=Neural_Network()
for i in xrange(5000):
	print "#" +str(i)+"\n"
	print "Input(scaled):\n"+str(X)
	print "Actual Output: \n"+str(y)
	print "Predicted Output: \n"+str(NN.forward(X))
	print "Loss: \n" +str(np.mean(np.square(y-NN.forward(X))))
	print "\n"
	NN.train(X,y)

   NN.saveWeights()
   NN.predict()
