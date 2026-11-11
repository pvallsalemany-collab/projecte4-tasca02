## Part 1: Bones pràctiques en la documentació de commits
0. He creat el repositori públic <br> 
![Creació repo púbblic](img/Creació_del_repositori_públi.png) 

1. Fes el teu primer commit seguint la convenció de missatges de commit que hem vist abans:
```
docs: inicialitza la repositori de prova per tasca 2
```
He fet el ptimer commit
![Imatge primer_commit](img/primers_commits.png) <br>
<br>
<br>


2. He creat un fitxer `00-installer-config.yaml`
![Crea_fitxer_yaml_en_Github](img/crear_fitxer_yaml.png)

3. He inserit aquest text:
```
network:
  version: 2
  renderer: networkd
  ethernets:
    enps03:
      dhcp4: true
```

![inserir_text_yaml](img/Inserir_text_yaml.png)
<br>

4. Ho guardo executant:
```
git add 00-installer-config.yaml
```
![git add 00-installer-config.yaml](img/git_add_00-installer-config.yaml.png)

5. Ara fai el commit tipu `feat` executant la sagüent comanda:
```
git commit -m "feat: afegeix configuracio inicial de xarxa"
```
![primer commit tipu feat](img/primer_commit_tipu_feat.png)

6. Ara després del commit i posar el missatge faig un push executant:
```
git push
```
![git push part 1 només després de fer commit!](img/git_push_part1.png)


## Part 2 L'historial del repositori

1. He executat la comanda `git log` per visualitzar l'historial detallat del repositori.
```
git log
```
![veure historial general i resumit](img/git_log.png) <br>
Aquesta comanda mostra:
- L'identificador (hash) de cada commit.
- L'autor que ha realitzat el canvi.
- La data del commit.
- El missatge descriptiu associat.


2. He executat la comanda git log --oneline per visualitzar una versió resumida de l'historial.
```
git log --oneline
```
![veure versió resumida del histroial](img/git_log--oneline.png)
A diferència de `git log`, aquesta mostra cada commit en una sola línia amb:
- El hash abreujat.
- El missatge del commit.

3. He utilitzat Git Graph per visualitzar gràficament l'historial del repositori. Aquesta eina permet veure la seqüència de commits de manera més visual que la terminal. També permet identificar les branques existents i observar l'ordre en què s'han realitzat els commits.


![usant_git_graph](img/usant_git_graph.png)