# Decision trees

## Growing decision trees

Decide split by one of two metrics:

1. Information gain (algorithms: ID3 or C4.5)
2. Gini (algorithm: CART)
### Information gain: the tree’s loss function

Information gain is a reduction in entropy. Entropy is a measure of the impurity of a certain set:

**Purest set:** entropy = 0, all elements belong to one class

**Least pure set:** high entropy, elements are evenly distributed among many different classes

By default, the entropy of a set is the weighted sum of the self-informations (in bits/Shannons) of all possible outcomes: 

![AD_4nXfe6dCKVDS42OGWFr_-30paNcxFoBs_JUOAhshfS1tQkP1g3rQ8pY2mTKwosabwEfVr95LSqb1XCXikUBAekDmJfVcVv92IJE7jqAcLgjaNaGR-BzcuLyUrCLtrChgoTveQ4kZ7kw.png](blob:capacitor://localhost/4a4817c1-3f88-4795-8ccd-fe51321d4508)

Example (with Defaulter Borrower as the outcome variable):![AD_4nXc21zf4uegHP14hNNBXTJM8DhDIwXvKBdmQm27803Rt-br147mLtcC9pg3gzYQ7E7HT2ej81AeV0Rq-S3NNy2eFihDyZXjj13ZGFCwdSxjRx9-FITjwDxSEfc25kc7xnN_RSpPhew.png](blob:capacitor://localhost/a98a094e-1114-42f9-909a-2b81f0eded88)

A growing decision tree seeks to have the purest possible leaf nodes — its objective function is the weighted sum of the entropies of its leaf nodes:![AD_4nXchzihCr0NVTFrfcb49GW1mGGbZW6Xy0eFE-tJOHRE0uHE8iDtJ4sQvweT3dxPqvEAfCG60PSDIoQylCTlq90rOw5VS4Ko9DglgP6WPDwFnRsyyOnAwqly9fbwnvDqvvAk--7ghWA.png](blob:capacitor://localhost/0f01fff1-5fde-4356-8590-55a0c78d481f)![AD_4nXdh5TJeLBOmiU0PEn2Y99DtK4iLkvrvn9nK1YRGOg_U9ZEzoEWTZ3CyTDHXhvyTQaJlnuiWn7gJATzRytVQLmQjDfxDLBeo6myZkVLAe4BSqFpSEvPsokqVk2iFv_30D_xoNTof.png](blob:capacitor://localhost/82da5e00-4188-4e1b-9882-f7b17fb4e821)


### Gini coefficient

Entropy is computationally

### What about continuous variables? 

Make two categories out of the continuous variables, defined by a threshold; split the data into two categories depending on whether 

The threshold (in this example, 100k) is not chosen arbitrarily: it is chosen to maximize entropy/gini.

  

  

## Trimming decision trees

You can grow decision trees all the way and trim off the node that minimize the # of mistakes saved/removed by # of nodes added. Iterate until the whole tree is trimmed off, at each step saving the tree for testing; at the end, test all trees on training and dev set and select the tree which performs best on the dev set.