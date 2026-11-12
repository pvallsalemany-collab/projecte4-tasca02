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


## Part 4: Recuperar versions anteriors (commits) del repositori

1. Configuro el fitxer .yaml la interfície enps03 a una IP estàtica
![enps03 confugurada a adreça est+atica](img/configura_enps03_ip_estàtica.png)

2. Ho afageicxo en el espai temporal de preparació i realitzo el commit

```
git add 00-installer-config.yaml
git commit -m "feat: configura interfície enps03 amb IP estàtica"
```
![Realitza un git add amb el nom del arxiu modificat i descripció atòmica](img/configura%20interfície%20enps03%20amb%20IP%20estàtica.png)

3. Edito de nou el fitxer `yaml` configurant la interfície **enps08** 

![Evidència de condiguraió en enps08 amb DHCP true](img/Configura_enps08_amb_DHCP_true.png)

4. Ara torno a realitzar un git add i un commit tipu feat del fitxer .yaml després de configurar la interície enps08
![configuració enps08 amb DHCP true](img/enps08_amb_DHCP_true.png)


5. Canviar la configuració per **actualitzar el DNS** a la configuració de la interfície `enps03` ja que la configuració inicial no funcionava (aquí el enps08 desapareix)

![Nova configuració i canvi de DNS ja que l'anterior no funcionaba](img/desapareix_enps08_pel_canvi_de_DNS.png)

6. Faig el commit desde la terminal tornant a fer aquest procés: git add i després commit amb un missatge descriptiu
![Canviar condiguració DNS en un commit](img/actualitzar_servidor_DNS.png)


7. Reviso el historial de versions executant
```
git log --oneline
```
![Executant git log --online en la terminal](img/git_log--oneline.png)

8. Faig revert en els 3 últims commits sense editar per fer-ho he d'executar:
```
git revert --no-edit 3ea5a53 2564294 8327b6f
```
Verificació: Git crearà tres nous commits de tipus `Revert "..."` sense demanar-te que editis missatges, i si obres el fitxer `00-installer-config.yaml`, tornarà a tenir només la configuració DHCP inicial per a `enps03`

![Revrteixo 3 ommits quina vbona pràctica la part tostona es uqe he de posar el hash de cada commit](img/git_revert_3commits.png)

Resultat en el fitxer .yaml després del revert <br>
![Conseqüència del revert en el fitxer .yaml](img/consequencia_revert_yaml.png)

Evidència amb el **Git Graph**
![Git Graph captura amb 3 fletxes indicant els 3 revers](img/git_graph_3_reverts.png)


9. Explorar el quart commit anterior usant la eina gràfica documentant-lo

- Dins de `source control` vaig a `View Git Graph(git log)`

![Ves a Source Cntrol mou el raolí fins trobar el Git Grapth a dalt de commit a la dreta](img/dins_source_control_vas_a_Git_Graph.png)

- Ara dins del Git Graph view faig clic a un commit i clico a la part dreta on surt (+2 | -4)
![Arbre de git graph](img/git_graph_arbre.png)

- Felicitats ja pots veure la comparativa actual amb el d'abans

![Comparativa abans i ara explorant amb l'eina Git Graph view](img/comparativa_abans_ara.png)

>Vermell: El que es va esborrar |
>Verd: El que s'ha afegit

## Part 5: Git Reset (no és recomenable per el procediment ni en treballs de grup)
**Abans de fer git reset:** La comanda `git reset --hard HEAD~1` elimina de manera permanent l'últim commit i qualsevol canvi no desat al directori de treball.
1. Desa tot el meu progrés fins ara amb un commit de seguretat:
```
git add solucions.md img/
git commit -m "docs: documenta punt 5 exploració de commit"
```
![commit de seguretat per realitzar el reset](img/commi_seguretat_part5_pendent.png)

2. Abans de fer el reset també comprovo el historial actual executant:
```
git log --oneline
```
![comprovació gi grapth el commit](img/git_log_--online_comprovació_part5.png)

3. Desa els canvis que tinc pendents en solucion..md
```
git add solucions.md
git commit -m "docs: afegeix captura prèvia al reset"
´´´


