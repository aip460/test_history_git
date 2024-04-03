# test_history_git

Pasos para eliminar una subida a github erronea (público, para poder ver la pérdida de información):

1. Subir un fichero password.txt, junto con otros basura.txt
2. Probar a eliminar el fichero passwrod.txt y hacer un commit, seguire teniendo el rastro de dicho fichero.
3. Probar a deshacer el commit, eliminando el rastro. Para ello, basta con resetear al commit del punto 1:
   * git reset --hard hast del commit (alternativa: HEAD~2, es decir: deshará los dos últimos commits)
   * git push --force
     
4. Et Voila, ya no hay rastro del commit con el fichero erroneo. Para hacer la resubida, añadir dicho fichero a un .gitignore y revisar antes de hacer el commit+push
