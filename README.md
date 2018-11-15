# vector
just for practice
import numpy as np
from numbers import Number

class Vector3(object):
    def __init__(self, x = 0, y = 0, z = 0, dtype = "float32"):
        self._data = np.array([x,y,z], dtype = dtype)
        self.x = self._data[0]
        self.y = self._data[1]
        self.z = self._data[2]

    def __str__(self):
        return str("Vector3({0.x},{0.y},{0.z})".format(self))

    def __mul__(self, value):
        if isinstance(value, type(self)):
            result = self._data * value._data
        elif isinstance(value, Number):
            result = self._data * value
        return type(self)(x = result[0], y = result[1], z = result[2])

    def __rmul__(self, value):
        return self.__mul__(value) # Kommutativgesetz/commutative

    def __add__(self, value):
        if isinstance(value, type(self)):
            result = self._data + value._data
        elif isinstance(value, Number):
            result = self._data + value
        return type(self)(x = result[0], y = result[1], z = result[2])

    def __radd__(self, value):
        return self.__add__(value) # Kommutativgesetz/commutative

    def __sub__(self, value):
        if isinstance(value, type(self)):
            result = self._data - value._data
        elif isinstance(value, Number):
            result = self._data - value
        return type(self)(x = result[0], y = result[1], z = result[2])

    def __rsub__(self, value):
        if isinstance(value, type(self)):
            result = value._data - self._data
        elif isinstance(value, Number):
            result = value - self._data
        return type(self)(x = result[0], y = result[1], z = result[2])


#Test
if __name__ == "__main__":
    a = Vector3(5,5,5)
    b = Vector3(2,4,3)
    c = a * b
    d = 2 * a
    e = a * 2
    f = a + b
    g = a + 2
    h = 2 + a
    i = a - b
    j = 2 - a
    k = a - 2
    print(c,d,e,f,g,h,i,j,k, sep = "\n")
