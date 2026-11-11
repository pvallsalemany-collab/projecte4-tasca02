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

4. Ho afageixo a **l'àrea dels canvis temporals** executant:
```
git add 00-installer-config.yaml
```
![git add 00-installer-config.yaml](img/git_add_00-installer-config.yaml.png)

5. Ara faig el commit tipu `feat` executant la sagüent comanda:
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


4. He executat la comanda git show HEAD per veure la informació del darrer commit i els canvis realitzats. Per fer-ho he executat:
```
git show HEAD
```
![git show HEAD una comanda que permet veure els commits i els canvis que s'han fet en cada commit](img/git_show_HEAD(ensenyar_últims_commits).png)
> HEAD és un punter que apunta al commit més recent de la branca actual.






## Part 3 Recuperar versions anteriors del working directory

1. Simular l'error humà canviant enp0s3 per a eth0 dins del fitxer `00-installer-config`
```
network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:
      dhcp4: true
```
![error humà de canviar enp0s3 a eth0](img/error_huma_eth0.png)

2. Miro l'estat actual dels fitxers executant:
```
git status
```
![git status per comprovar l'estat dels fitxers en la part 3 d'aquesta actuvitat](img/git_status_part3.png)

> [!NOTE]
> He modificat el fitxer `00-installer-config.yaml` simulant un error en la configuració.
> Mitjançant la comanda `git status` he comprovat que Git detecta els canvis realitzats respecte a l'últim commit.


3. Ara he de recuperar el fitxer tal com estava a l'últim commit i elimina els canvis que he fet al Working Directory. Amb el restore

```
git restore 00-installer-config.yaml
```


![fent un git restore](img/git_restore.png)

El canvi que he vist
![canvi](img/consequencia_git_restore.png)

> [!NOTE]
> Després d'executar `git restore 00-installer-config.yaml`, el fitxer ha tornat a l'estat de l'últim commit. Es pot observar que la interfície torna a aparèixer com a `enps03`, recuperant la configuració original. 
4. Veure l'estat executant
```
git status
```
![git restore consequència en que desapareix la modificació en 00-installer-config.yaml](img/git_restore_consequencia_historial.png)


