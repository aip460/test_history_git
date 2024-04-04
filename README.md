# test_history_git

Pasos para eliminar una subida a github erronea (público, para poder ver la pérdida de información):
## Forma resetear a un commit ok:
1. Subir un fichero password.txt, junto con otros basura.txt
2. Probar a eliminar el fichero passwrod.txt y hacer un commit, seguire teniendo el rastro de dicho fichero.
3. Probar a deshacer el commit, eliminando el rastro. Para ello, basta con resetear al commit del punto 1:
   * git reset --hard hast del commit (alternativa: HEAD~2, es decir: deshará los dos últimos commits)
   * git push --force
     
4. Et Voila, ya no hay rastro del commit con el fichero erroneo. Para hacer la resubida, añadir dicho fichero a un .gitignore y revisar antes de hacer el commit+push

## Forma eliminar de la traza (sin perder commits) el fichero:
Sin volver a un estado correcto anterior, eliminar la traza de un fichero a lo largo del historial de commits. Es decir, mantendremos todos los cambios, incluidos los del commit con información sensible pero excluyendo el fichero que filtra información (https://docs.github.com/es/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository). Pasos:
1. Instalar **it filter-repo**,```$ pip install git-filter-repo```, necesario tener python y mejor activo un entorno virtual
2. Forzar el eliminado y su traza del fichero: ```$ git filter-repo-force --invert-paths -path fichero.txt```
3. El remoto se pierde y por tanto, hay que volver a enlazarlo: ``` $ git remote add origin url_github_repo```
4. Forzar un push de la nueva situación: ```git push --force```
