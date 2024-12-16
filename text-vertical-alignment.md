Dans SVG, les attributs comme **`hanging`** et **`text-bottom`** sont des valeurs possibles pour l’attribut **`dominant-baseline`** ou utilisées dans le contexte des propriétés CSS comme **`alignment-baseline`**. Ces valeurs déterminent comment le texte est aligné verticalement par rapport à son conteneur ou à d'autres éléments.

---

### **1. `hanging` : Alignement suspendu**
La valeur **`hanging`** aligne le texte de manière à ce que sa ligne de base soit située au niveau de la ligne de suspension utilisée dans certains systèmes d'écriture, comme les écritures indiennes ou d'Asie du Sud-Est.

#### **Caractéristiques :**
- La ligne de suspension se situe légèrement **au-dessus de la ligne de base** utilisée par défaut pour les scripts latins.
- Cela permet au texte de sembler "suspendu", particulièrement utile pour les alphabets où les caractères pendants (comme les voyelles diacritiques) doivent rester équilibrés.

#### **Illustration :**
```xml
<svg width="300" height="100">
  <!-- Ligne de référence -->
  <line x1="0" y1="50" x2="300" y2="50" stroke="black" stroke-width="1" />
  
  <!-- Texte aligné à 'hanging' -->
  <text x="50" y="50" dominant-baseline="hanging" font-size="20">Hanging</text>
</svg>
```

Dans cet exemple :
- Le mot "Hanging" est aligné de manière à ce que le haut des lettres (comme la barre du H) soit proche de la ligne de suspension.

#### **Usage typique :**
- Utile pour des scripts qui nécessitent une suspension précise du texte (comme certains scripts Brahmi ou Thaï).
- Rarement utilisé avec des scripts latins, mais peut servir pour un alignement esthétique dans des compositions graphiques.

---

### **2. `text-bottom` : Alignement au bas du texte**
La valeur **`text-bottom`** aligne le texte de manière à ce que son bas corresponde à la limite inférieure du texte ou de la ligne de texte.

#### **Caractéristiques :**
- Elle est utilisée pour aligner le texte avec le **point le plus bas** d’un glyphe dans la ligne courante.
- Cela inclut souvent les caractères avec des descentes, comme `g`, `p`, ou `q`.

#### **Illustration :**
```xml
<svg width="300" height="100">
  <!-- Ligne de référence -->
  <line x1="0" y1="50" x2="300" y2="50" stroke="black" stroke-width="1" />
  
  <!-- Texte aligné à 'text-bottom' -->
  <text x="50" y="50" dominant-baseline="text-bottom" font-size="20">Text Bottom</text>
</svg>
```

Dans cet exemple :
- Le bas des caractères descendus (comme `g` dans "Text Bottom") est aligné avec la ligne de référence.

#### **Usage typique :**
- Alignement précis dans des compositions où le texte doit correspondre exactement au bas d'une cellule ou d'un conteneur.
- Utile dans des tableaux SVG ou pour des textes positionnés sur des graphiques.

---

### **Différences clés entre `hanging` et `text-bottom`**

| **Propriété**  | **`hanging`**                                      | **`text-bottom`**                                |
|-----------------|----------------------------------------------------|-------------------------------------------------|
| **Position**    | Aligne le texte à la ligne de suspension.          | Aligne le texte avec la partie la plus basse.   |
| **Usage**       | Scripts suspendus (e.g., Brahmi, Thaï).            | Scripts avec des descentes (e.g., latin).       |
| **Compatibilité**| Rare pour les scripts latins.                     | Fréquent pour les graphiques ou compositions.   |

---

### **3. Contexte et relations avec d'autres propriétés**

- **`alignment-baseline`** :
  Détermine comment une portion de texte individuelle est alignée.
  ```xml
  <text x="50" y="50" alignment-baseline="text-bottom">Sample</text>
  ```

- **`dominant-baseline`** :
  Définit la ligne de base principale d’un conteneur de texte (comme `<text>` ou `<tspan>`). Cela affecte tout le texte imbriqué.
  ```xml
  <text x="50" y="50" dominant-baseline="hanging">Sample</text>
  ```

---

### **4. Comparaison visuelle**
```xml
<svg width="500" height="150">
  <!-- Ligne de référence -->
  <line x1="0" y1="50" x2="500" y2="50" stroke="black" stroke-width="1" />

  <!-- Texte aligné à hanging -->
  <text x="10" y="50" dominant-baseline="hanging" font-size="20">Hanging</text>

  <!-- Texte aligné à text-bottom -->
  <text x="150" y="50" dominant-baseline="text-bottom" font-size="20">Text Bottom</text>

  <!-- Texte aligné à baseline par défaut -->
  <text x="300" y="50" font-size="20">Default Baseline</text>
</svg>
```

- **`Hanging`** : Le haut du texte est suspendu.
- **`Text Bottom`** : Le bas du texte est aligné à la ligne.
- **Default Baseline** : Utilise la ligne de base standard pour l’écriture latine.

---

### **5. Conclusion**
- **`hanging`** est spécifique à certains scripts non latins et peut servir pour des effets esthétiques ou graphiques.
- **`text-bottom`** est plus fréquemment utilisé dans des alignements précis dans des tableaux, des graphiques, ou des visualisations complexes.