> [!tip] Définition
> Un amplificateur différentiel est un amplificateur électronique dont le signal de sortie est proportionnel à la différence entre deux signaux d'entrée. 
> 
> C'est un comparateur linéaire à courant continu.

> [!example] Objectif
> Obtenir une tension de sortie référencée par rapport à la masse.

> [!note] Formule amplificateur différentiel idéal
> $$V_{out} - V_{off} = A_{VD} (v_1-v_2)$$
> $A_{VD}$ est appelé le gain différentiel. 
> $v_{off}$ est une tension de décalage imposée par un circuit externe.

> [!warning]
> Un amplificateur différentiel idéal n'existe pas, on doit alors changer les formules.

> [!note] Formule amplificateur différentiel réel
>  $$V_{out} - V_{off} = A_{VD} (v_1-v_{2}) + A_{MC} \frac{v_{1}+v_{2}}{2}$$
>  $A_{MC}$ est appelé le gain de mode commun.

> [!tip] Remarque
> Plutôt que le gain de mode commun $A_{MC}$, on préfère utiliser la notion de taux de réjection de mode commun. Le taux de réjection de mode commun (Common mode rejection ratio) est défini par:
> $\tau_{CMMR} = \frac{A_{VD}}{A_{MC}}$

> [!todo] Expression Finale
> $$V_{out} - V_{off} = A_{VD} [ (v_1-v_{2}) + \frac{v_1+v_{2}}{2 \tau_{CMMR}}]$$

