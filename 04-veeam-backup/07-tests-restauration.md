# Tests de restauration

Après la configuration des sauvegardes, plusieurs tests de restauration ont été réalisés.

Ces tests permettent de vérifier la capacité à récupérer les machines virtuelles en cas d'incident.

## Processus de restauration

La restauration d'une machine virtuelle peut être effectuée directement depuis la console Veeam.

![Restore Menu](screenshots/01-restore.png)

## Restauration d'une machine virtuelle

Exemple de restauration d'une machine virtuelle.

![Restore VM](screenshots/02-restore-menu.png)

## Résumé de la restauration

![Restore VM](screenshots/03-restore-summary.png)

## Validation de la restauration

Une fois la restauration terminée, la machine virtuelle peut être redémarrée et testée.

![Restore Success](screenshots/04-restore-success.png)

Vous pouvez constater sur la capture que l’entrée TESTDERESTAURATION, créée après la sauvegarde, n’apparaît plus. Cela confirme que la restauration a bien été effectuée et que la machine virtuelle a été remplacée par la version restaurée

![Restore Success](screenshots/05-restore-success.png)