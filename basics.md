Les fichiers SVG (Scalable Vector Graphics) sont utilisés pour décrire des images vectorielles en utilisant du XML. Ils sont parfaits pour créer des graphiques dynamiques et interactifs, qui restent nets à toutes les résolutions.

Voici une introduction pratique pour écrire et comprendre les SVG.

---

### **Structure de base d’un SVG**
Un fichier SVG commence par une balise `<svg>` qui contient tout le graphique.

#### Exemple :
```xml
<svg xmlns="http://www.w3.org/2000/svg" width="200" height="200">
    <!-- Contenu du SVG -->
</svg>
```

- **xmlns** : L'espace de noms pour indiquer qu'il s'agit d'un SVG.
- **width** et **height** : Dimensions de l'image SVG.

---

### **Les formes de base**

#### 1. **Rectangle**
```xml
<svg xmlns="http://www.w3.org/2000/svg" width="200" height="200">
    <rect x="10" y="10" width="100" height="50" fill="blue" />
</svg>
```

- **x**, **y** : Position du coin supérieur gauche du rectangle.
- **width**, **height** : Largeur et hauteur du rectangle.
- **fill** : Couleur de remplissage.

#### 2. **Cercle**
```xml
<svg xmlns="http://www.w3.org/2000/svg" width="200" height="200">
    <circle cx="50" cy="50" r="30" fill="red" />
</svg>
```

- **cx**, **cy** : Coordonnées du centre du cercle.
- **r** : Rayon.
- **fill** : Couleur de remplissage.

#### 3. **Ellipse**
```xml
<svg xmlns="http://www.w3.org/2000/svg" width="200" height="200">
    <ellipse cx="100" cy="50" rx="50" ry="25" fill="green" />
</svg>
```

- **rx**, **ry** : Rayons horizontal et vertical.

#### 4. **Ligne**
```xml
<svg xmlns="http://www.w3.org/2000/svg" width="200" height="200">
    <line x1="10" y1="10" x2="150" y2="100" stroke="black" stroke-width="2" />
</svg>
```

- **x1**, **y1**, **x2**, **y2** : Points de départ et d'arrivée.
- **stroke** : Couleur de la ligne.
- **stroke-width** : Épaisseur de la ligne.

#### 5. **Polygone**
```xml
<svg xmlns="http://www.w3.org/2000/svg" width="200" height="200">
    <polygon points="50,10 90,90 10,90" fill="purple" />
</svg>
```

- **points** : Liste de coordonnées `(x, y)` séparées par des espaces.

#### 6. **Polyligne**
```xml
<svg xmlns="http://www.w3.org/2000/svg" width="200" height="200">
    <polyline points="10,10 50,50 90,10" fill="none" stroke="blue" stroke-width="2" />
</svg>
```

- **fill="none"** : Pas de remplissage.

---

### **Ajouter du texte**
```xml
<svg xmlns="http://www.w3.org/2000/svg" width="200" height="200">
    <text x="50" y="50" font-size="20" fill="black">Hello SVG</text>
</svg>
```

- **x**, **y** : Position du texte.
- **font-size** : Taille de la police.

---

### **Groupes avec `<g>`**
Les groupes permettent de regrouper plusieurs éléments et leur appliquer des transformations ou des styles communs.

#### Exemple :
```xml
<svg xmlns="http://www.w3.org/2000/svg" width="200" height="200">
    <g fill="orange">
        <circle cx="50" cy="50" r="30" />
        <rect x="100" y="30" width="50" height="50" />
    </g>
</svg>
```

- Tous les éléments héritent de `fill="orange"`.

---

### **Transformations**
Vous pouvez transformer des éléments avec des propriétés comme **rotate**, **translate**, et **scale**.

#### Exemple :
```xml
<svg xmlns="http://www.w3.org/2000/svg" width="200" height="200">
    <rect x="50" y="50" width="50" height="50" fill="blue" transform="rotate(45 75 75)" />
</svg>
```

- **rotate(45 75 75)** : Tourne de 45° autour du point (75, 75).

---

### **Dégradés avec `<defs>`**
Vous pouvez définir des dégradés ou des formes réutilisables.

#### Exemple : Dégradé linéaire
```xml
<svg xmlns="http://www.w3.org/2000/svg" width="200" height="200">
    <defs>
        <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="0%">
            <stop offset="0%" style="stop-color:blue;stop-opacity:1" />
            <stop offset="100%" style="stop-color:red;stop-opacity:1" />
        </linearGradient>
    </defs>
    <rect x="10" y="10" width="180" height="100" fill="url(#grad1)" />
</svg>
```

---

### **Path : Tracer des formes complexes**
Le `<path>` est l’élément le plus puissant pour dessiner des formes.

#### Exemple :
```xml
<svg xmlns="http://www.w3.org/2000/svg" width="200" height="200">
    <path d="M10 10 H 90 V 90 H 10 Z" fill="cyan" stroke="black" />
</svg>
```

- **M** : Déplace le curseur (Move to).
- **H** : Ligne horizontale (Horizontal line to).
- **V** : Ligne verticale (Vertical line to).
- **Z** : Ferme la forme.

---

### **Animations avec `<animate>`**
```xml
<svg xmlns="http://www.w3.org/2000/svg" width="200" height="200">
    <circle cx="50" cy="50" r="30" fill="red">
        <animate attributeName="cx" from="50" to="150" dur="2s" repeatCount="indefinite" />
    </circle>
</svg>
```

- **attributeName** : Attribut à animer.
- **from**, **to** : Valeurs de début et de fin.
- **dur** : Durée de l'animation.
- **repeatCount** : Nombre de répétitions (`indefinite` pour en boucle).

---

### **Bonus : Intégrer dans HTML ou JS**
#### Directement dans HTML :
```html
<div>
    <svg width="100" height="100">
        <circle cx="50" cy="50" r="40" fill="blue"></circle>
    </svg>
</div>
```

#### Manipuler avec JavaScript :
```html
<svg id="mySVG" width="200" height="200">
    <circle id="myCircle" cx="50" cy="50" r="40" fill="blue"></circle>
</svg>

<script>
    const circle = document.getElementById("myCircle");
    circle.setAttribute("fill", "red");
</script>
```

---

Entraîne-toi en combinant ces concepts pour créer des visuels dynamiques ! Si tu as une idée spécifique, je peux te guider. 😊