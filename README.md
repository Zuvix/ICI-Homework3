# ICI-Homework3
Calculations

I used entropy to measure how mixed each group is. Entropy is 0 when all examples have the same answer. It is close to 1 when the numbers of Yes and No examples are almost equal. I used log base 2.

```text
Entropy = - sum of (probability x log2(probability))
```

For each attribute, I split the data into groups. Then I calculated the weighted entropy of those groups. I used a weighted value because a larger group should count more than a smaller group.

```text
Weighted entropy after = sum of (group size / total size) x group entropy

Information Gain = entropy before - weighted entropy after
```

There are 5 Yes examples and 6 No examples. The entropy before the first split is:

```text
H(S) = -(5/11) log2(5/11) - (6/11) log2(6/11) = 0.9940
```

## Information gain for Shape

For Shape, the Convex group has 2 Yes and 3 No examples. Its entropy is 0.9710. The Depressed group has 3 Yes and 3 No examples. Its entropy is 1.0000. Both groups are still mixed, so I expected Shape to have a low information gain.

```text
Weighted entropy = (5/11 x 0.9710) + (6/11 x 1.0000) = 0.9868

Gain(Shape) = 0.9940 - 0.9868 = 0.0072
```

## Information gain for Color

For Color, Brown has 3 Yes and 2 No examples. Its entropy is 0.9710. Red has only one No example, so its entropy is 0. White has 2 Yes and 2 No examples, so its entropy is 1.0000. Yellow also has only one No example, so its entropy is 0.

```text
Weighted entropy = (5/11 x 0.9710) + (1/11 x 0)
                 + (4/11 x 1.0000) + (1/11 x 0)
                 = 0.8050

Gain(Color) = 0.9940 - 0.8050 = 0.1891
```

## Information gain for Odor

For Odor, Normal has 3 Yes and 0 No examples. Its entropy is 0. Funky has 2 Yes and 3 No examples. Its entropy is 0.9710. Stinks has 0 Yes and 3 No examples, so its entropy is also 0.

```text
Weighted entropy = (3/11 x 0) + (5/11 x 0.9710) + (3/11 x 0)
                 = 0.4413

Gain(Odor) = 0.9940 - 0.4413 = 0.5527
```

## Choosing the root

| Attribute | Weighted entropy | Information gain |
|:----------|-----------------:|-----------------:|
| Shape | 0.9868 | 0.0072 |
| Color | 0.8050 | 0.1891 |
| Odor | 0.4413 | 0.5527 |

I used Odor for the root because it has the highest information gain. Normal can be classified as Yes straight away. Stinks can be classified as No. Only the Funky group is still mixed.

## The Funky branch

The Funky group has 2 Yes and 3 No examples. Its entropy is 0.9710. I repeated the calculation with the attributes that were still available.

```text
Gain(Funky, Shape) = 0.0200

Gain(Funky, Color) = 0.5710
```

I used Color because it has the larger information gain. Red and Yellow lead to No. White leads to Yes. The Brown group still has one Yes and one No, so I used Shape for the last test. Brown and Convex leads to Yes. Brown and Depressed leads to No.
