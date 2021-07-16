# Derivation of the [[sigmoid]]

$$
\sigma(z) = \frac{1}{1 + e^{-z}}
$$

$$
\frac{\text{d}}{\text{d}z} \sigma(z) = - \frac{ \frac{\text{d}}{\text{d}z} (1 + e^{-z})}{(1 + e^{-z})^2}
$$

$$
\frac{\text{d}}{\text{d}z} \sigma(z) = \frac{e^{-z}}{(1 + e^{-z})^2}
$$

$$
\frac{\text{d}}{\text{d}z} \sigma(z) = \frac{1}{1 + e^{-z}}\frac{ -e^{-z}}{1 + e^{-z}}
$$

$$
\frac{\text{d}}{\text{d}z} \sigma(z) = \frac{1}{1 + e^{-z}}(\frac{1 + e^{-z}}{1 + e^{-z}} - \frac{1}{1 + e^{-z}})
$$

$$
\frac{\text{d}}{\text{d}z} \sigma(z) = 
\sigma(z) (1 - \sigma(z))
$$
