# Classification Using Perception And Adaptive Neurons

When we were trying to determine as how the human brain works, scientists proposed a theory. They proposed that the nerve cells within our brain is a binary gate, on which several inputs can be applied. Only when the cell input exceeds a certain threshold, then the neurons fire an output. 

This was further enhanced by theory of perception later. An algorithm was proposed, which showed that the neurons can automatically learn the weight coefficients that can be then multiplied with the input features in order to make the decision whether the neuron will fire or not. 

## What Is An Artificial Neuron

We can think of artificial neurons in the context of binary classification. We can think that artificial neurons take an input of `x`, say $[x_{1}, x_{2}, x_{3} \dots x_{n}]$ and multiply that by the weights say $[w_{1}, w_{2}, w_{3} \dots w_{n}]$. When we do this we get `z` = $w_{1}.x_{1} + w_{2}.x_{2} + \dots + w_{n}.x_{n}$. The process of finding these `w` or weights is called training. 

If the final value of `z` is greater that a threshold, say $\Theta$, we assign the class `1` to it, else we assign `0`. 

We can simplify this equation further. We can take a value of `b` which is equal to $-\Theta$, the negative value of the threshold. Then we can add that directly to the equation. 

$z = w_{1}.x_{1} + w_{2}.x_{2} + \dots + w_{n}.x_{n} + b$

So, we can now say that the target class will be 0 if `z` is less than zero, and 1 if `z` is greater than zero. 

Thus, `z` can be visualised as follows:

![](../../assets/Pasted%20image%2020221115094708.png)




