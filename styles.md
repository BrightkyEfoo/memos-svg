Les SVG acceptent une combinaison de styles hérités du CSS (comme pour le HTML) et de styles spécifiques à SVG. Ces styles peuvent être appliqués directement sous forme d’attributs sur les éléments SVG ou via des feuilles de style CSS.

---

### **1. Styles de base (CSS standard)**

Ces styles affectent les éléments SVG comme pour les balises HTML.

#### Exemple de styles courants :
```css
svg {
    background-color: lightgray; /* Fond de l'espace SVG */
    width: 200px;               /* Largeur */
    height: 200px;              /* Hauteur */
    border: 1px solid black;    /* Bordure */
}
```

---

### **2. Styles spécifiques à SVG**

Voici les principaux styles que l'on peut appliquer aux formes SVG :

#### **Remplissage et Contours**

1. **fill** : Définit la couleur de remplissage.
   ```xml
   <circle cx="50" cy="50" r="40" fill="red" />
   ```

2. **stroke** : Définit la couleur du contour.
   ```xml
   <circle cx="50" cy="50" r="40" stroke="blue" stroke-width="2" />
   ```

3. **stroke-width** : Épaisseur du contour.
   ```xml
   <rect x="10" y="10" width="100" height="50" stroke="black" stroke-width="4" />
   ```

4. **stroke-linecap** : Définit la forme des extrémités d’une ligne.
   - **butt** (par défaut) : Bords plats.
   - **round** : Extrémités arrondies.
   - **square** : Extrémités carrées dépassant la ligne.
   ```xml
   <line x1="10" y1="10" x2="100" y2="10" stroke="black" stroke-width="10" stroke-linecap="round" />
   ```

5. **stroke-linejoin** : Définit la forme des jonctions entre deux segments de ligne.
   - **miter** (par défaut) : Angle pointu.
   - **round** : Angle arrondi.
   - **bevel** : Angle tronqué.
   ```xml
   <polyline points="10,10 50,50 90,10" stroke="black" stroke-width="4" fill="none" stroke-linejoin="round" />
   ```

6. **stroke-dasharray** : Définit un motif de tirets pour le contour.
   ```xml
   <line x1="10" y1="50" x2="200" y2="50" stroke="black" stroke-width="4" stroke-dasharray="5,10" />
   ```

7. **stroke-dashoffset** : Décale le point de départ du motif de tirets.
   ```xml
   <line x1="10" y1="50" x2="200" y2="50" stroke="black" stroke-width="4" stroke-dasharray="5,10" stroke-dashoffset="10" />
   ```

---

#### **Styles de texte**
Appliqués aux éléments `<text>`.

1. **font-family** : Police de caractères.
   ```xml
   <text x="10" y="20" font-family="Arial" font-size="20">Hello SVG</text>
   ```

2. **font-size** : Taille de la police.
   ```xml
   <text x="10" y="20" font-size="30">SVG Text</text>
   ```

3. **text-anchor** : Alignement horizontal du texte.
   - **start** (par défaut) : Aligné à gauche.
   - **middle** : Centré.
   - **end** : Aligné à droite.
   ```xml
   <text x="100" y="50" text-anchor="middle" font-size="20">Centered</text>
   ```

4. **dominant-baseline** : Alignement vertical.
   - **auto** (par défaut) : Alignement automatique.
   - **middle** : Centré verticalement.
   - **hanging** ou **text-bottom** : Ajustements spécifiques.
   ```xml
   <text x="10" y="50" font-size="20" dominant-baseline="middle">Vertical Align</text>
   ```

5. **fill** et **stroke** : Couleurs du texte et de son contour.
   ```xml
   <text x="10" y="50" fill="blue" stroke="red" stroke-width="1">Styled Text</text>
   ```

---

#### **Couleurs et Opacité**

1. **opacity** : Transparence globale (0 à 1).
   ```xml
   <circle cx="50" cy="50" r="40" fill="green" opacity="0.5" />
   ```

2. **fill-opacity** et **stroke-opacity** : Transparence indépendamment pour le remplissage ou le contour.
   ```xml
   <circle cx="50" cy="50" r="40" fill="green" fill-opacity="0.5" stroke="black" stroke-opacity="1" />
   ```

---

#### **Transformations**

1. **transform** : Applique une transformation comme la rotation, le déplacement ou l'échelle.
   - **translate(x, y)** : Déplace l'élément.
   - **scale(sx, sy)** : Modifie la taille.
   - **rotate(angle, cx, cy)** : Tourne autour du point (cx, cy).
   ```xml
   <rect x="10" y="10" width="100" height="50" fill="blue" transform="rotate(45 60 35)" />
   ```

---

#### **Effets avancés**
Ces styles sont utilisés pour des effets graphiques complexes.

1. **filter** : Applique des filtres (flou, ombre portée, etc.).
   ```xml
   <filter id="blur">
       <feGaussianBlur in="SourceGraphic" stdDeviation="5" />
   </filter>
   <circle cx="50" cy="50" r="40" fill="blue" filter="url(#blur)" />
   ```

2. **clip-path** : Définit une zone visible.
   ```xml
   <clipPath id="cut-off">
       <rect x="0" y="0" width="50" height="50" />
   </clipPath>
   <circle cx="50" cy="50" r="40" fill="red" clip-path="url(#cut-off)" />
   ```

3. **mask** : Masque des parties d’un élément.
   ```xml
   <mask id="mask">
       <rect x="10" y="10" width="50" height="50" fill="white" />
       <circle cx="50" cy="50" r="20" fill="black" />
   </mask>
   <rect x="0" y="0" width="100" height="100" fill="blue" mask="url(#mask)" />
   ```

---

### **Appliquer des styles avec du CSS externe**
Tu peux utiliser des classes CSS comme pour du HTML.

#### Exemple :
```xml
<svg xmlns="http://www.w3.org/2000/svg" width="200" height="200">
    <style>
        .circle { fill: orange; stroke: black; stroke-width: 2; }
    </style>
    <circle cx="50" cy="50" r="40" class="circle" />
</svg>
```

---

Avec ces styles, tu peux personnaliser et enrichir tes graphiques SVG pour obtenir des rendus dynamiques et professionnels ! 😊