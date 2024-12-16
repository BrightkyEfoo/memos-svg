### **`stroke-dasharray` et `stroke-dashoffset` expliqués en détail**

Ces deux propriétés permettent de créer des motifs de lignes en pointillés ou en tirets sur les contours d’un élément SVG.

---

### **1. `stroke-dasharray`**

Cette propriété définit un motif répétitif de tirets et d’espaces pour le contour (**stroke**) d’un élément. Elle accepte une liste de nombres, où :

- **Les nombres impairs** représentent les longueurs des segments visibles (tirets).
- **Les nombres pairs** représentent les longueurs des segments invisibles (espaces).

#### **Format :**
```css
stroke-dasharray: <valeur1>, <valeur2>, <valeur3>, ...;
```

#### **Exemple simple :**
```xml
<line x1="10" y1="50" x2="200" y2="50" 
      stroke="black" stroke-width="4" stroke-dasharray="10,5" />
```
- **`10`** : Longueur des tirets.
- **`5`** : Longueur des espaces.

---

#### **Exemple avec plusieurs valeurs :**
```xml
<line x1="10" y1="80" x2="200" y2="80" 
      stroke="blue" stroke-width="4" stroke-dasharray="10,5,2,5" />
```
- **`10`** : Longueur d’un premier long tiret.
- **`5`** : Longueur de l’espace après le premier tiret.
- **`2`** : Longueur d’un court tiret.
- **`5`** : Longueur de l’espace après le court tiret.
- Le motif **10-5-2-5** se répète tout au long de la ligne.

---

#### **Valeur unique :**
Si une seule valeur est spécifiée, elle s’applique comme **longueur de tous les tirets**, les espaces étant considérés à zéro.
```xml
<circle cx="50" cy="50" r="40" stroke="red" stroke-width="3" stroke-dasharray="10" />
```

---

### **2. `stroke-dashoffset`**

Cette propriété décale le motif de tirets le long du contour. Elle détermine **l’endroit où commence le motif**.

- **Valeurs positives** : Le motif se décale dans le sens des aiguilles d'une montre (ou le long du tracé).
- **Valeurs négatives** : Le motif se décale dans le sens inverse.

#### **Format :**
```css
stroke-dashoffset: <valeur>;
```

---

#### **Exemple de base :**
```xml
<circle cx="50" cy="50" r="40" 
        stroke="green" stroke-width="3" stroke-dasharray="10,5" stroke-dashoffset="20" />
```
- Le motif est décalé de **20 unités**.
- Cela décale les tirets et les espaces autour du cercle.

---

#### **Cas dynamique :**
`stroke-dashoffset` est très utile pour des animations dynamiques, comme une ligne qui se dessine progressivement. Voici un exemple :

```xml
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100">
    <circle cx="50" cy="50" r="40" 
            stroke="blue" fill="none" stroke-width="4" 
            stroke-dasharray="251.2" stroke-dashoffset="251.2">
        <animate attributeName="stroke-dashoffset" from="251.2" to="0" dur="2s" repeatCount="indefinite" />
    </circle>
</svg>
```

- **`stroke-dasharray="251.2"`** : 251.2 est la circonférence du cercle (2 × π × rayon).
- **`stroke-dashoffset="251.2"`** : Le cercle semble complètement vide au départ.
- **`animate`** : Fait décroître `stroke-dashoffset` pour "dessiner" le contour.

---

### **Différence visuelle : `stroke-dasharray` vs `stroke-dashoffset`**

1. **`stroke-dasharray`** : Définit **le motif de tirets et d’espaces** (le style).
2. **`stroke-dashoffset`** : Décale ce motif **sur le chemin du contour** (l’animation ou le positionnement).

---

### **Applications pratiques**

1. **Créer des graphiques en pointillés ou en tirets :**
   - Délimiter des zones avec des contours discontinus.

2. **Animations :**
   - Simuler un tracé progressif de formes ou de lignes.
   - Indiquer un chargement avec des motifs qui bougent.

3. **Stylisation avancée :**
   - Différencier des chemins, lignes ou courbes dans des graphiques complexes.

Avec ces outils, tu peux créer des animations fluides et stylées pour enrichir visuellement tes SVG.