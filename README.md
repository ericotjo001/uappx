# kaBEDONN: posthoc eXplainable Artificial Intelligence with Data Ordered Neural Network

This is the main repo for the apper of the same title: kaBEDONN: posthoc eXplainable Artificial Intelligence with Data Ordered Neural Network.

Objectives:
1. Relevant data as explanations as shown in fig. 1(A).
2. Adjustment of Explanation for debugging, like fig. 2(B).
3. Predictive correctness flag for debugging.

<img src="https://drive.google.com/uc?export=view&id=1MyohSQ6UAvI0mPfWHV0taUTc4HUrDiSF"></img>
Fig. 1. (A) Relevant data as explanation (B) Class ordered data (C) kaBEDONN.

## Experiments
Commands to obtain the results can be found in examples/entry.py.

Here are some of them. First, train the CNN. This will be used to provide latent encoders for kaBEDONN. 
```
python main.py --mode example --data mnist --submode train_dnn --epoch 4 --batch_size 16
```

The following will first construct kaBEDONN for class-selective explanation. The results are saved (like fig. 5 in the paper)
```
python main.py --mode example --data mnist --submode ces --classes 4 9 --firstn 240 240
python main.py --mode example --data mnist --submode ces --classes 4 9 --firstn 240 240 --assess 4 0  4 130 4 152 4 777 9 0  9 239 9 555
python main.py --mode example --data mnist --submode ces --classes 4 9 --firstn 240 240 --assess freeinput
```

The following plots the MNIST part of fig. 6 in the paper. The process treats data ordering as hyperparameter.
```
python main.py --mode example --data mnist --submode hyper
```

The following uses the entire MNIST dataset for constructing kaBEDONN. 
```
python main.py --mode example --data mnist --submode train --kwidth 16 
python main.py --mode example --data mnist --submode eval_train --kwidth 16 
python main.py --mode example --data mnist --submode eval --kwidth 16  
python main.py --mode example --data mnist --submode result --kwidth 16  

python main.py --mode example --data mnist --submode showcase --kwidth 16 --classes 0 1 2 3 4 5 --idx 0 0 0 0 0 0  

```

## kaBEDONN, user feedback and developer debugging
<img src="https://drive.google.com/uc?export=view&id=1kH7SaWtotPp3HJZ2uV7EYLKoxTf5f7tt"></img>
Fig. 2. (A) kaBEDONN in normal case. (B) kaBEDONN helps debugging.