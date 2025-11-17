> [!note] Deux grands domaines de l'électronique
> - Analogique 
> 	- Infinité de valeurs dans un intervalle donné
> 	- Grandeur temporelle continue
> - Numérique
> 	- Nombre fini de valeurs dans un intervalle donné
> 	- Grandeur temporelle échantillonnée

> [!note] Convertisseurs
> - Numérique -> Analogique (DAC)
> - Analogique -> Numérique (ADC)

> [!example] Caractéristiques d'un ADC
> - Nombre de bits
> - Plage de conversion (ou tension de pleine échelle)
> - Quantum
> - Formule entre tension de pleine échelle et quantum
> - Règle de conversion
> - Durée de conversion

>[!note] Erreurs
>- Erreur d'offset (DC Offset Error)
>- Erreur de gain (DC Gain Error)
>
>- Non linéarité intégrale (Integral Non Linearity : INL)
>- Non linéarité différentielle (Differential Non Linearity : DNL)

> [!example] Erreur d'offset
> Le code binaire 0 ne correspond pas forcément à une tension voisine de zéro en entrée. Cette tension est la tension de décalage ou erreur de décalage ou erreur d'offset.

> [!example] Erreur de gain
> L'erreur de gain (DC Gain Error) est la différence de pente de conversion (exprimée sur la dernière transition)

> [!example] Non linéarité intégrale
> L'erreur de linéarité est l'erreur qui reste après correction des deux précédentes.

> [!note] Durée de conversion
> Lorsqu'on numérise un signal, on envoie à l'ADC un ordre de conversion (START), et on récupère la valeur binaire en sortie au terme d'un délai appelé durée de conversion. 
> 
> Pour maintenir constante la tension en entrée de l'ADC durant toute la durée de conversion, on insère un échantillonneur bloqueur avant le convertisseur.

