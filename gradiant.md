Les dégradés en SVG (Scalable Vector Graphics) permettent de créer des transitions douces de couleurs entre deux ou plusieurs points dans un élément graphique. Cela est utile pour obtenir des effets de profondeur, de lumière ou de texture. Il existe principalement deux types de dégradés en SVG : **les dégradés linéaires** et **les dégradés radiaux**.

---

### **1. Dégradé Linéaire (Linear Gradient)**

Un dégradé linéaire crée une transition de couleurs le long d’une ligne droite. Cette ligne peut être définie par des points spécifiques, ou par un angle.

#### **Structure de base :**
```xml
<svg width="200" height="200">
  <defs>
    <linearGradient id="myLinearGradient" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color: red; stop-opacity: 1" />
      <stop offset="100%" style="stop-color: yellow; stop-opacity: 1" />
    </linearGradient>
  </defs>
  
  <!-- Appliquer le dégradé à un élément -->
  <rect x="10" y="10" width="180" height="180" fill="url(#myLinearGradient)" />
</svg>
```

#### **Explication :**
- `<linearGradient>` : Définit le dégradé linéaire. L'attribut `id` permet de l'identifier et de l'appliquer à un élément.
- `x1`, `y1`, `x2`, `y2` : Définissent les points de départ et de fin du dégradé, en pourcentage ou en coordonnées absolues (par exemple, `x1="0%" y1="0%"` pour un dégradé de l'angle supérieur gauche à l'angle inférieur droit).
- `<stop>` : Définit un point d'arrêt du dégradé. Chaque point d'arrêt a une couleur (`stop-color`) et une opacité (`stop-opacity`), ainsi qu’un offset pour déterminer sa position dans le dégradé.

#### **Valeurs pour `x1`, `y1`, `x2`, `y2` :**
- **(0%, 0%)** : Coin supérieur gauche.
- **(100%, 100%)** : Coin inférieur droit.
- **(50%, 50%)** : Centre de l’élément.

Tu peux aussi utiliser des coordonnées absolues comme `x1="10" y1="10"`, mais l'utilisation de pourcentages est plus courante.

#### **Exemple de dégradé linéaire avec un angle spécifique :**
```xml
<linearGradient id="myLinearGradient" angle="45deg">
  <stop offset="0%" style="stop-color: blue; stop-opacity: 1" />
  <stop offset="100%" style="stop-color: green; stop-opacity: 1" />
</linearGradient>
```

---

### **2. Dégradé Radial (Radial Gradient)**

Un dégradé radial crée une transition de couleurs qui s'étend en cercles concentriques, partant d'un point central.

#### **Structure de base :**
```xml
<svg width="200" height="200">
  <defs>
    <radialGradient id="myRadialGradient" cx="50%" cy="50%" r="50%" fx="50%" fy="50%">
      <stop offset="0%" style="stop-color: blue; stop-opacity: 1" />
      <stop offset="100%" style="stop-color: white; stop-opacity: 1" />
    </radialGradient>
  </defs>
  
  <!-- Appliquer le dégradé à un élément -->
  <circle cx="100" cy="100" r="80" fill="url(#myRadialGradient)" />
</svg>
```

#### **Explication :**
- `<radialGradient>` : Définit le dégradé radial. L'attribut `id` permet de l'identifier.
- `cx`, `cy` : Définissent le centre du dégradé. Par défaut, il est centré au milieu de l'élément (`50%`).
- `r` : Définit le rayon du dégradé. Il peut être un pourcentage de la taille de l’élément (par exemple, `r="50%"` pour couvrir la moitié de la largeur).
- `fx`, `fy` : Définissent la position du foyer du dégradé. Le foyer détermine où la couleur la plus intense du dégradé commence. Si `fx` et `fy` sont égaux à `cx` et `cy`, le dégradé est symétrique.

#### **Exemple de dégradé radial avec différentes positions :**
```xml
<radialGradient id="myRadialGradient" cx="50%" cy="50%" r="50%" fx="70%" fy="30%">
  <stop offset="0%" style="stop-color: yellow; stop-opacity: 1" />
  <stop offset="100%" style="stop-color: purple; stop-opacity: 1" />
</radialGradient>
```

---

### **3. Dégradé avec Plusieurs Arrêts (Multiple Stops)**

Tu peux ajouter plusieurs arrêts dans un dégradé pour créer des transitions plus complexes. Chaque arrêt peut avoir une couleur et une position spécifiques.

#### **Exemple avec plusieurs arrêts :**
```xml
<svg width="200" height="200">
  <defs>
    <linearGradient id="multiStopGradient">
      <stop offset="0%" style="stop-color: red; stop-opacity: 1" />
      <stop offset="50%" style="stop-color: green; stop-opacity: 1" />
      <stop offset="100%" style="stop-color: blue; stop-opacity: 1" />
    </linearGradient>
  </defs>
  
  <rect x="10" y="10" width="180" height="180" fill="url(#multiStopGradient)" />
</svg>
```

#### **Explication :**
- Ici, il y a trois arrêts, ce qui crée un dégradé qui passe de rouge à vert, puis à bleu.

---

### **4. Utilisation des Dégradés avec des Éléments SVG**

Les dégradés peuvent être appliqués non seulement aux formes simples comme les rectangles et cercles, mais aussi à des éléments plus complexes comme des chemins (`<path>`) ou des images.

#### **Exemple avec un `<path>` :**
```xml
<svg width="200" height="200">
  <defs>
    <linearGradient id="pathGradient" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color: orange; stop-opacity: 1" />
      <stop offset="100%" style="stop-color: purple; stop-opacity: 1" />
    </linearGradient>
  </defs>
  
  <path d="M10,10 C50,80 150,80 190,10" stroke="url(#pathGradient)" fill="none" />
</svg>
```

**Explication :**
- Le dégradé est appliqué au `stroke` de la courbe définie par `<path>`, créant une transition de couleurs le long de la ligne.

---

### **5. Dégradé avec Opacité**

Tu peux aussi manipuler l’opacité d’un dégradé pour obtenir des effets de transparence.

#### **Exemple de dégradé avec opacité :**
```xml
<svg width="200" height="200">
  <defs>
    <linearGradient id="opacityGradient">
      <stop offset="0%" style="stop-color: red; stop-opacity: 1" />
      <stop offset="100%" style="stop-color: blue; stop-opacity: 0" />
    </linearGradient>
  </defs>
  
  <rect x="10" y="10" width="180" height="180" fill="url(#opacityGradient)" />
</svg>
```

**Explication :**
- Le dégradé va de rouge à bleu, avec une transition de l’opacité complète à une opacité nulle (transparent).

---

### **Résumé des Attributs Principaux des Dégradés en SVG**

- **`<stop>`** : Définit les points d'arrêt dans un dégradé (couleur et opacité).
- **`offset`** : Position de l’arrêt dans le dégradé (exprimé en pourcentage ou en unités absolues).
- **`stop-color`** : Définie la couleur à cet arrêt.
- **`stop-opacity`** : Définit l'opacité de la couleur.
- **`x1`, `y1`, `x2`, `y2` (pour `<linearGradient>`)** : Définissent la direction du dégradé.
- **`cx`, `cy`, `r`, `fx`, `fy` (pour `<radialGradient>`)** : Définissent la position et l’étendue du dégradé radial.

---

Les dégradés en SVG permettent une personnalisation avancée des visuels et sont très utilisés pour les interfaces graphiques, les icônes, les arrière-plans et les animations.