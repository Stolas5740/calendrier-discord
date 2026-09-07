# Calendrier Discord

Ce dépôt contient les événements affichés par l'extension Chrome **Calendrier Discord**.

Le fichier [`events.json`](events.json) est la seule chose à modifier. L'extension le
relit à chaque ouverture du popup : une modification est visible par tout le monde
immédiatement, sans réinstaller quoi que ce soit.

## Ajouter un événement

Ouvre `events.json`, clique sur l'icône crayon (**Edit this file**), ajoute un bloc,
puis **Commit changes** en haut à droite.

```json
{
  "name": "Nom de l'événement",
  "color": "blue",
  "url": "https://discord.com/channels/ID_SERVEUR/ID_SALON",
  "slots": [
    { "date": "2026-10-12", "time": "20:00" },
    { "date": "2026-10-13", "time": "21:30" }
  ]
}
```

## Les règles

| Champ | Format | Exemple |
|---|---|---|
| `name` | texte libre | `Raid nocturne` |
| `color` | un nom de la liste ci-dessous | `purple` |
| `url` | lien vers le salon Discord | `https://discord.com/channels/123.../456...` |
| `date` | `AAAA-MM-JJ` | `2026-10-12` |
| `time` | `HH:MM` sur 24 heures | `09:00` et non `9:00` |

**Les couleurs reflètent le potentiel du call**, jamais son risque :

| Couleur | Sens |
|---|---|
| `purple` | 🟣 Excellent |
| `green` | 🟢 Bon |
| `yellow` | 🟡 Moyen |
| `orange` | 🟠 Petit |
| `red` | 🔴 Faible |
| `white` | ⚪ échéance d'inscription (signup) |

`blue` est disponible mais n'est attribué à rien pour l'instant.

Un événement peut avoir autant de créneaux que nécessaire, y compris plusieurs le
même jour. L'ordre n'a pas d'importance : le tri se fait à l'affichage.

Pour récupérer le lien d'un salon : clic droit sur le salon dans Discord →
**Copier le lien**.

## Les deux pièges

1. **La virgule entre les blocs.** Il en faut une entre deux événements, jamais
   après le dernier. C'est l'erreur la plus fréquente.
2. **Un fichier mal formé ne provoque pas d'erreur visible.** L'extension retombe
   silencieusement sur sa copie de secours et continue d'afficher d'anciennes
   données. Si tes modifications n'apparaissent pas, c'est le premier truc à
   vérifier.

## Vérifier que c'est bon

Après avoir enregistré, ouvre le popup de l'extension : la modification doit y être.
Si rien ne change, c'est que le JSON est invalide — colle son contenu sur
<https://jsonlint.com> pour repérer la ligne fautive.
