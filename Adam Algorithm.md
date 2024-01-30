(**Ada**ptive **M**oment Estimation)
An optimization (learning) algorithm that is an alternative to [[Gradient descent]]. It is faster.

It will increase or decrease the learning rate ($\alpha$) for you, by instead of using one learning rate, it will have one for each parameter. 

```python
model.compile(optimizer=tf.keras.optimizers.Adam(learning_rate=1e-3),loss=tf.keras.losses.SparseCategoricalCrossentropy(from_logits=True))
```

