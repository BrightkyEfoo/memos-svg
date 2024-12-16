En SVG, les **filtres** permettent d'appliquer des effets visuels comme le flou, l'ombrage, le décalage de couleur, ou encore des transformations complexes. Ils utilisent l'élément `<filter>` combiné avec des sous-éléments pour définir des étapes spécifiques d'un effet. Voici toutes les possibilités offertes par les filtres SVG.

---

### **1. Structure de base d'un filtre SVG**
Les filtres SVG sont définis dans un élément `<defs>` et appliqués à des éléments graphiques avec l'attribut `filter`.

```xml
<svg width="300" height="200">
  <defs>
    <!-- Définition d'un filtre -->
    <filter id="myFilter">
      <!-- Effets à appliquer -->
      <feGaussianBlur stdDeviation="5" />
    </filter>
  </defs>

  <!-- Utilisation du filtre -->
  <rect x="50" y="50" width="100" height="100" fill="blue" filter="url(#myFilter)" />
</svg>
```

---

### **2. Types de filtres SVG et leurs usages**

#### **2.1. `feGaussianBlur` (Flou gaussien)**
Applique un flou gaussien à l'élément.

**Attributs principaux :**
- `stdDeviation`: Le rayon de flou (en pixels).

```xml
<feGaussianBlur stdDeviation="5" />
```

---

#### **2.2. `feOffset` (Décalage)**
Décale l'élément en x et y, souvent utilisé pour créer des ombres.

**Attributs principaux :**
- `dx`: Décalage horizontal.
- `dy`: Décalage vertical.

```xml
<feOffset dx="10" dy="10" />
```

---

#### **2.3. `feColorMatrix` (Transformation de couleur)**
Transforme les couleurs en appliquant une matrice 4x5.

**Modes courants :**
- `type="saturate"` : Ajuste la saturation.
- `type="hueRotate"` : Fait tourner la teinte (en degrés).
- `type="luminanceToAlpha"` : Convertit la luminance en transparence.
- `type="matrix"` : Applique une matrice de transformation personnalisée.

**Exemple de désaturation :**
```xml
<feColorMatrix type="saturate" values="0" />
```

---

#### **2.4. `feFlood` (Couleur unie)**
Crée une couleur unie sur l'ensemble de l'élément.

**Attributs principaux :**
- `flood-color`: La couleur.
- `flood-opacity`: L'opacité.

```xml
<feFlood flood-color="black" flood-opacity="0.5" />
```

---

#### **2.5. `feComposite` (Combinaison)**
Combine deux images en fonction d'une opération mathématique (`over`, `in`, `out`, `xor`, etc.).

**Attributs principaux :**
- `operator`: Type de combinaison.
- `in`, `in2`: Entrées à combiner.

```xml
<feComposite in="SourceGraphic" in2="BackgroundImage" operator="over" />
```

---

#### **2.6. `feMerge` (Fusion de calques)**
Combine plusieurs entrées graphiques en une seule.

**Attributs principaux :**
- Chaque étape utilise `<feMergeNode>`.

```xml
<feMerge>
  <feMergeNode in="SourceGraphic" />
  <feMergeNode in="shadow" />
</feMerge>
```

---

#### **2.7. `feImage` (Image externe)**
Charge une image externe pour être utilisée dans le filtre.

**Attributs principaux :**
- `href`: URL de l'image.

```xml
<feImage href="image.jpg" />
```

---

#### **2.8. `feTile` (Tuilage)**
Répète une région graphique pour remplir une surface.

**Attributs principaux :**
- `in`: Entrée graphique à répéter.

```xml
<feTile in="SourceGraphic" />
```

---

#### **2.9. `feMorphology` (Morphologie)**
Dilate ou érode les bords d'une image.

**Attributs principaux :**
- `operator`: `dilate` ou `erode`.
- `radius`: Taille de l'effet.

```xml
<feMorphology operator="dilate" radius="2" />
```

---

#### **2.10. `feTurbulence` (Turbulence fractale)**
Génère une texture de bruit ou de turbulence.

**Attributs principaux :**
- `baseFrequency`: Fréquence du bruit (x et y).
- `numOctaves`: Nombre d'octaves.
- `type`: `fractalNoise` ou `turbulence`.

```xml
<feTurbulence baseFrequency="0.05" numOctaves="2" />
```

---

#### **2.11. `feDisplacementMap` (Carte de déplacement)**
Déforme une image en fonction d'une carte de déplacement.

**Attributs principaux :**
- `in`, `in2`: Image source et carte de déplacement.
- `scale`: Intensité de la déformation.

```xml
<feDisplacementMap in="SourceGraphic" in2="turbulence" scale="10" />
```

---

#### **2.12. `feConvolveMatrix` (Convolution)**
Applique un filtre convolutionnel (par exemple, pour détecter les contours).

**Attributs principaux :**
- `kernelMatrix`: La matrice utilisée pour la convolution.
- `divisor`: Normalisation.

```xml
<feConvolveMatrix kernelMatrix="0 1 0 1 -4 1 0 1 0" />
```

---

#### **2.13. `feDropShadow` (Ombre portée)**
Ajoute une ombre portée à l'élément.

**Attributs principaux :**
- `dx`, `dy`: Décalage de l'ombre.
- `stdDeviation`: Flou de l'ombre.
- `flood-color`: Couleur de l'ombre.

```xml
<feDropShadow dx="4" dy="4" stdDeviation="3" flood-color="black" />
```

---

### **3. Combinaison de filtres**
Les filtres SVG peuvent être combinés pour créer des effets complexes en connectant les étapes via leurs attributs `in` et `result`.

**Exemple d'ombre portée personnalisée :**
```xml
<svg width="300" height="200">
  <defs>
    <filter id="customShadow">
      <feOffset dx="5" dy="5" result="offset" />
      <feGaussianBlur in="offset" stdDeviation="3" result="blur" />
      <feMerge>
        <feMergeNode in="blur" />
        <feMergeNode in="SourceGraphic" />
      </feMerge>
    </filter>
  </defs>
  
  <rect x="50" y="50" width="100" height="100" fill="blue" filter="url(#customShadow)" />
</svg>
```

---

### **4. Où appliquer des filtres**
Les filtres peuvent être appliqués à :
- **Éléments graphiques** : `<rect>`, `<circle>`, `<path>`, etc.
- **Texte SVG** : `<text>`.
- **Groupes** : `<g>`.

---

### **5. Attributs globaux pour les filtres**
Lorsqu'un filtre est défini avec `<filter>`, il possède aussi des attributs globaux comme :
- **`x`, `y`** : Position du cadre du filtre.
- **`width`, `height`** : Dimensions du cadre du filtre (souvent plus grand que l'élément pour éviter la coupure des effets).
- **`filterUnits`** : Unités relatives (`userSpaceOnUse` ou `objectBoundingBox`).

---

### **6. Conclusion**
Les filtres SVG offrent une flexibilité impressionnante pour personnaliser et styliser des éléments graphiques. Ils permettent de créer des effets allant des ajustements simples (flou, ombre) à des transformations complexes (turbulence, déformations). En combinant ces filtres de manière créative, tu peux produire des effets uniques et visuellement saisissants.