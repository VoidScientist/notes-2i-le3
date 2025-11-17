> [!abstract] Résumé.
> Ce TP donne suite au [[Notes TP 1|TP 1]] et vise à y ajouter une interface grâce à l'API `Swing` de Java.

> [!note] Où trouver des informations ?
> Par manque de temps, et de contenu dans le TP, il est conseillé d'aller faire un tour sur la  [documentation officielle](https://docs.oracle.com/javase/8/docs/api/index.html?javax/swing/package-summary.html) pour plus de détails.

## Gestionnaires de mise en page.

Les objets de type `JPanel` possèdent une méthode `add()` qui permet d'ajouter des objets graphiques (qui héritent de `JComponent`) sur le panneau.

Pour mettre en page ces éléments on utilise des `LayoutManager` avec la méthode `setLayout()` des `JPanel`.

### Gestionnaire de type `BorderLayout`

Permet de disposer des composants graphiques de telle sorte qu'il y ait un composant central entouré de 4 composants au dessus, en dessous, à gauche et à droite.

On ajoute des composants avec `add()`. Le deuxième paramètre permet la spécification d'une localisation.

#### Exemples

```java
JPanel panel = new JPanel();
BorderLayout layout = new BorderLayout();
panel.setLayout(layout);
panel.add(new JLabel("A"), BorderLayout.NORTH);
panel.add(new JLabel("B"), BorderLayout.SOUTH);
panel.add(new JLabel("C"), BorderLayout.EAST);
panel.add(new JLabel("D"), BorderLayout.WEST);
panel.add(new JLabel("E"), BorderLayout.CENTER);
```

Il est possible de créer des éléments invisibles de taille fixe afin de s'en servir comme marges.

```java
JPanel panel = new JPanel();
BorderLayout layout = new BorderLayout();
panel.setLayout(layout);
panel.add(new JButton("Bouton central", BorderLayout.CENTER);
// structures invisibles de taille fixes horizontales
panel.add(Box.createHorizontalStrut(50), BorderLayout.NORTH);
panel.add(Box.createHorizontalStrut(50), BorderLayout.SOUTH);
// structures invisibles de taille fixes verticales
panel.add(Box.createVerticalStrut(50), BorderLayout.EAST);
panel.add(Box.createVerticalStrut(50), BorderLayout.WEST);
```


> [!tip] Remarque
> Par défaut les `JFrame` utilisent un gestionnaire de mise en page de type `BorderLayout`

## Remplir une JList avec un modèle de données.

Une manière propre d'indiquer quels sont les éléments à afficher sur un objet graphique de type `JList` est d'utiliser un modèle de données.

Pour une `JList` un modèle de donnée doit être une classe implémentant l'interface `ListModel`. 

Pour un modèle de donnée standard on utiliserait `DefaultListModel`.

Si on souhaite créer un modèle plus spécifique on crée une nouvelle classe avec `AbstractListModel`.

### Exemple

```java
List<TypeObjet> elements = .... // elements a afficher dans la JList

JList<TypeObjet> list = new JList<>();
DefaultListModel<TypeObjet> model = new DefaultListModel<>();

for(TypeObjet obj : elements) {
	model.addElement(obj);
}

list.setModel(model);
```


## Écouteurs d'événements

Ce que l’on appelle événements de bas niveau sont des actions physiques de
l’utilisateur sur le clavier ou la souris ; c’est par exemple le cas d’un clic dans
une fenêtre. 

Les événements de bas niveau peuvent être classifiés en quatre
catégories :

- **Les événements liés à la souris :** appui sur un bouton, relâchement d’un bouton, double clic, glisser de la souris, etc...
- **Les événements liés au clavier :** appui sur une touche, relâchement d’une touche, etc...
- **Les événements de focalisation.**
- **Les événements de gestion des fenêtres.**

L'objet graphique qui crée des événements est appelé `source`.

L'objet `écouteur` traite l'événement au lieu de la `source`. Il doit s'inscrire auprès de l'objet `source` qui déclenche ces événements.

### Exemple avec l'interface `KeyListener`

Définition de l'`écouteur`:

```java
public class MyListener extends KeyListener {
	@Override
	public void keyTyped(KeyEvent e) {
		System.out.println("appui sur une touche");
	}
	
	@Override
	public void keyPressed(KeyEvent e) {
		System.out.println("une touche est enfoncee");
	}
	
	@Override
	public void keyReleased(KeyEvent e) {
		System.out.println("relachement d’une touche");
	}
}
```

Inscription de l'`écouteur`:

```java
JTextField champTexte = new JTextField(50);
champTexte.addKeyListener(ecouteur);
```

## Objets pour définir le rendu graphique

Il est possible de définir la manière dont sont affichés les éléments d'un composant graphique qui contient une liste d'items, en l'occurrence un `JList`.

`JList` possède la méthode `setCellRenderer()` qui prend en argument un objet implémentant l'interface `ListCellRenderer<TypeObject>`.

Cette interface décrit une seule méthode `getListCellRendererComponent()` qui possède **5 paramètres**:
- La `JList` sur laquelle on veut définir le rendu
- Une valeur de la liste (type: `TypeObjet`)
- L'indice dans la liste de cette valeur
- Un booléen si valeur est actuellement sélectionnée
- Un booléen pour indiquer si cette valeur a le focus

Cette méthode renvoie un objet de type `Component`, dont la méthode `paint` sera appelée pour faire le rendu de la cellule.

### Exemple

```java
public class MyRenderer implements ListCellRenderer<TypeObjet> {
@Override
	public Component getListCellRendererComponent(
			JList<? extends TypeObjet> list,
			TypeObjet value,
			int index,
			boolean isSelected,
			boolean cellHasFocus) {
			
		JLabel label = new JLabel();
		label.setText(value.textToDisplay());
		
		if(cellHasFocus) {
			label.setForeground(Color.BLACK);
			label.setOpaque(true);
			label.setBackground(Color.RED);
		} else {
			label.setForeground(Color.GREEN);
		}
		
		return label;
		
	}
}
```

