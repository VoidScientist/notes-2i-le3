> [!abstract] Résumé
> Ce TP était à propos de l'API JDBC qui permet de programmer en Java l'accès aux bases de données locales ou distantes avec des requêtes SQL.

## Connexion à une base de données

> [!tip] DriverManager
> Pour établir une connexion avec une base de données, il faut appeler la méthode statique `getConnection()` qui peut lever des erreurs de type `SQLException`.
> 

> [!example] .getConnection(String url, String username, String password)
> - **url:** de la base de donnée.
> - **username:** d'un utilisateur ayant accès à la base de donnée.
> - **password:** mot de passe de l'utilisateur.

### Exemple

```java
String urlBDD = "jdbc:mysql://localhost:3306/nomBDD";
String utilisateur = "nomUtilisateur";
String motDePasse = "motDePasse";

Connection connexionBdd = DriverManager.getConnection(urlBDD,
utilisateur, motDePasse);
```

## Requêtes statiques

Pour exécuter une requête statique sur un SGBD (système de gestion de bases de données) depuis une application Java on peut suivre les étapes suivantes.

1. Ecrire une requête SQL dans une chaîne de caractères
2. Appeler la méthode `createStatement()` sur un objet de type `Connection` (celui que l'on a initialisé pour se connecter à la base de données). Cette méthode renvoie un objet de type `Statement`.
3. Sur l’objet précédemment créé, appeler la méthode `executeQuery(String requete)` à laquelle on fournit la requête SQL sous forme de chaîne de caractères. Cette méthode renvoie un objet de type `ResultSet` contenant les informations sélectionnées, et peut provoquer une exception de type `SQLException`.

## Classe `ResultSet`

L'objet de type `ResultSet` fourni par la méthode `executeQuery()` dispose de méthodes permettant de le parcourir enregistrement par enregistrement, à l'aide d'un curseur.
### Méthodes

> [!note] .next()
> Fait progresser le curseur d'un enregistrement au suivant. 
> 
> Retourne `false` s'il n'y a plus d'enregistrements
> > [!tip] Remarque
> > il est nécessaire de l'appeler une fois afin que le curseur soit sur le premier enregistrement.
> 


> [!note] .getString(String col_name)
> Récupère la donnée d'une colonne de type `String` de l'enregistrement actuel.
> - **col_name:** nom de la colonne concernée dans la DB.

> [!note] .getInt(String col_name)
> Similaire à `getString()` mais avec une donnée de type `int`.
### Exemple de requête statique

> [!warning] Remarque
> Les objets de type `Statement` et `ResultSet` étant consommateurs de ressources, il est judicieux d'appeler leur méthode `.close()` après utilisation.

```java
String urlBDD = "jdbc:mysql://localhost:3306/nomBDD";
String utilisateur = "nomUtilisateur";
String motDePasse = "motDePasse";

Connection connexionBdd = DriverManager.getConnection(urlBDD,
utilisateur, motDePasse);

String requete = "SELECT nom, prenom, revenu FROM client";

Statement statement = connexionBdd.createStatement();
ResultSet result = statement.executeQuery(requete);

while (result.next()) {
	String nom = results.getString("nom");
	String prenom = result.getString("prenom");
	int revenu = result.getInt(revenu);
	// ...
}

// fermeture des objets de type `ResultSet` et `Statement`
result.close();
statement.close();
```

## Requêtes dynamiques

> [!note]
> Les requêtes dynamiques sont des requêtes dont les clauses sont fournies à l'exécution (ex: par l'entrée d'un utilisateur).

> [!danger] Injection SQL
> Il peut paraître être une bonne idée de modifier une chaîne de caractère avec des attributs passés par l'utilisateur et exécuter la requête. 
> 
> **MAUVAISE IDÉE: Crée une vulnérabilité aux attaques par injection SQL.**

> [!tip] Solution
> Utiliser la classe `PreparedStatement`.

## Classe `PreparedStatement`

Lors de l'écriture de la requête SQL dans une chaîne de caractères, les paramètres dont la valeur sera fixée par la suite sont remplacés par le symbole `?`. 

A la différence d'une requête usuelle, une requête préparée est transmise au SGBD à l'aide de la méthode `PrepareStatement(String requete)` de la classe `Connection`. 

Cette méthode prend en arguments la requête SQL sous forme de chaîne de caractères. 

Il est ensuite possible de préciser les valeurs des paramètres à l'aide des méthodes de la classe `PreparedStatement`: il s'agit de méthodes nommées `setXXX()` où `XXX` correspond au type de donnée du paramètre. 

Ces méthodes prennent en argument le rang du paramètre concerné (1 pour le premier) ainsi que la valeur du paramètre.

> [!note]
> Cette méthode empêche les attaques par **Injection SQL** et est plus performante, car la requête d'un `PreparedStatement` est compilée.

### Exemple de requête dynamique

```java
String requete = "SELECT nom, prenom, revenu FROM client "
				+ "WHERE UPPER(nom) = ?";
				  
PreparedStatement prepStatement =
connexionBdd.prepareStatement(requete);
prepStatement.setString(1, nomClient.toUpperCase());

ResultSet result = prepStatement.executeQuery();

while (result.next()) {
	String nom = results.getString("nom");
	String prenom = result.getString("prenom");
	int revenu = result.getInt(revenu);
	// ...
}

result.close();
prepStatement.close();
```

>[!tip] UPPER()
> On remarquera qu'on peut utiliser la fonction `UPPER()` du langage SQL et la méthode `toUpperCase()` afin d'éviter la casse.

## Requêtes de mise à jour

L'API `JDBC` permet de réaliser des requêtes de mise à jour d'une table (insertion, suppression, modification d'enregistrements).

Si l'on souhaite réaliser des requêtes de mise à jour sur la base de données (`INSERT, UPDATE, DELETE`): on utilise `executeUpdate()` de l'interface `Statement`. 

### Exemple de requête de mise à jour

```java
String requete = "INSERT INTO client(nom, prenom) VALUES
				(’dupont’, ’marta’)";
				
Statement statement = connexionBdd.createStatement();

int nbRows = statement.executeUpdate(requete);
System.out.println(nbRows + " enregistrement(s) ajouté(s)");

statement.close();
```

