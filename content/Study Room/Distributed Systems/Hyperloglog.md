---
title: Hyperloglog
tags:
  - database
  - datastructure
draft: false
date: 2025-02-12
---
# How to approximate the number of distinct elements in a multiset ?

1. **Initialization**:
	- Choose a parameter bb to determine the number of buckets m=2bm=2b.
    - Initialize an array $M$ of size $m$ with all elements set to 0.
2. **Hashing**:
    - Define a hash function $h$ that maps each element to a uniformly distributed binary string.
3. **Update Procedure**:
    - For each element $x$ in the dataset:
        - Compute the hash value $h(x)$.
        - Split the hash value into two parts: the first $b$ bits ==(bucket index)== and the remaining bits ==(leading zeros)==.
        - Update the corresponding bucket in $M$ with the maximum number of leading zeros observed.
4. **Estimation**:
    - Compute the harmonic mean of the values in $M$ to estimate the cardinality.
    - Apply a correction factor $α_m$​ to improve accuracy.
5. **Correction for Small Cardinalities**:
    - If the estimated cardinality is small, use linear counting to correct the estimate.
6. **Final Estimate**:
	- The final estimate of the number of distinct elements is derived from the harmonic mean or the corrected estimate.

```python
def hyperloglog(data, b):
    m = 2 ** b
    M = [0] * m
    alpha_m = 0.7213 / (1 + 1.079 / m)

    def hash_function(x):
        # Implement a hash function that returns a binary string of length L
        pass

    def leading_zeros(binary_string):
        # Count the number of leading zeros in the binary string
        pass

    for x in data:
        hash_value = hash_function(x)
        j = int(hash_value[:b], 2)  # First b bits for bucket index
        r = leading_zeros(hash_value[b:])  # Remaining bits for leading zeros
        M[j] = max(M[j], r)

    E = alpha_m * m ** 2 / sum(2 ** -M[j] for j in range(m))

    if E <= 5/2 * m:
        V = sum(1 for j in range(m) if M[j] == 0)
        E_corrected = m * log(m / V)
        return E_corrected
    else:
        return E

```