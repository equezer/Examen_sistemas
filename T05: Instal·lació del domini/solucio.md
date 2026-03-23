# Procediment pràctic

## Abans de començar amb la tasca Crear una VM amb Windows 11 amb 5 GB de RAM i disc suficient. La xarxa estarà en xarxa NAT. Un cop creat l’equip, agregeu-lo al domini.

<img width="642" height="377" alt="image" src="https://github.com/user-attachments/assets/9ba5f5ed-df48-42e3-b369-e3c1272d27f0" />

---

<img width="887" height="379" alt="image" src="https://github.com/user-attachments/assets/b129435e-d667-4381-8dc2-3dd936f520d5" />

---

<img width="617" height="375" alt="image" src="https://github.com/user-attachments/assets/a87f31a7-726a-4dd6-bc2a-95055fa2ae45" />


## 1. Crear una estructura d’unitats organitzatives que sigui coherent i justificar la decisió.

### Primer entrem a la part de "AD DS", fem clic dret a sobre del nostre server i anem a l'opció: "Active Directory Users and Computers".

<img width="920" height="447" alt="image" src="https://github.com/user-attachments/assets/30dd281c-068b-4e80-b2f4-108dc0ea92c6" />

---

### Dintre cliquem a "trasnslogic09.test" i creem una nova unitat organitzativa:

<img width="775" height="554" alt="image" src="https://github.com/user-attachments/assets/c833b5a8-4bca-46bf-974a-39de3d460670" />

---

### Creem dos OU's que en aquest cas seràn: Usuaris i Grups.

<img width="437" height="378" alt="image" src="https://github.com/user-attachments/assets/b688ea63-8a62-4646-9758-489f834dd6c8" />

<img width="434" height="375" alt="image" src="https://github.com/user-attachments/assets/abb8160f-8db9-47f3-be49-659b34210146" />

---

### En el cas de que volguis esborrar alguna d'aquestes haurem de anar a dalt a la part de "view">"Advanced features", Després a dintre farem clic dret a la carpeta que en aquest cas serà usuaris i cliquem a "properties". Per acabar a la part de "objects" treiem l'opció de "Protect Object from accidental deletion" i només ens quedarà clicar a l'opció de "delete":

<img width="504" height="319" alt="Captura de pantalla 2026-02-04 182032" src="https://github.com/user-attachments/assets/bfb258e4-c1fa-4e23-872e-edf3e47255f3" />

<img width="758" height="504" alt="Captura de pantalla 2026-02-04 182243" src="https://github.com/user-attachments/assets/5932054f-b87e-46a3-8eb9-7e3904fc1109" />

<img width="427" height="486" alt="image" src="https://github.com/user-attachments/assets/c42e2a90-9f8b-45d4-842c-ae6093e3009b" />

<img width="627" height="362" alt="image" src="https://github.com/user-attachments/assets/760da6c6-5656-4866-a122-1c4bfaaf1e55" />

## Al acabar recordar treure l'opció d'advanced features
---

## 2. Ara Definirem la següent estructura de grups:

- gestio
- magatzem
- gerencia
- personal (tots els grups anteriors han de ser membres d’aquest grup)

---

### Primer fem clic dret a la OU de Grups creada anteriorment, anem a "New" i "Group".

<img width="613" height="420" alt="image" src="https://github.com/user-attachments/assets/978a6d26-b7ec-4ef5-959d-77d1ecc8ae05" />

---

### Farem un grup Global que es dirà: personal, on aniràn tots els altres grups (important deixar marcada l'opció de Global) També crearem els demés grups que seràn: gerencia, gestio i magatzem:

<img width="447" height="393" alt="image" src="https://github.com/user-attachments/assets/6135530a-fb17-4066-b588-463583b40950" />

<img width="511" height="222" alt="image" src="https://github.com/user-attachments/assets/61c1b2b0-faba-4ed1-802b-9aa5168e7fcf" />


---


### Ara al grup personal creat fem clic dret i anem a Properties > Members > add :

<img width="353" height="259" alt="image" src="https://github.com/user-attachments/assets/e5b75864-7570-4239-aeaf-94fed4bd487b" />

<img width="424" height="474" alt="image" src="https://github.com/user-attachments/assets/4e5f3dda-641e-4a23-901e-ab72bb1eee44" />


### També a "Object Types" deixem només l'opció de "Groups"

<img width="518" height="314" alt="image" src="https://github.com/user-attachments/assets/2794c82e-0762-4b7e-885d-32912718aa05" />

---

### Afegim els grups escribint-los a mà:

<img width="473" height="292" alt="image" src="https://github.com/user-attachments/assets/88d7cf9c-c86c-45bf-a38c-f0ee5b25c3bf" />

### i Ens quedaria tal que aixi:

<img width="393" height="262" alt="image" src="https://github.com/user-attachments/assets/8139daa9-8f41-48a9-a235-80ca5136658d" />

---

## Crear la carpeta compartida per a carpetes personals que es dirà "homes" al Disk C:

<img width="674" height="412" alt="image" src="https://github.com/user-attachments/assets/e8858a5f-4492-4b4d-90fe-5a09b061ba7a" />

---

### Anem a les propiertats de la carpeta i a "sharing", després cliquem a share i dintre escribim: Domain Users, i donem permissos de lectura i escritura i per acabar "Share".

<img width="391" height="497" alt="image" src="https://github.com/user-attachments/assets/ba5acd24-73ba-4fb1-a9e0-ecfa6b873c6f" />

<img width="643" height="445" alt="image" src="https://github.com/user-attachments/assets/9aa5425f-9602-43da-a8da-5e92dc9f646f" />

---

### Ara anem a security i a "Advanced". Cliquem a sobre de "Domain Users" i edit.

<img width="405" height="495" alt="image" src="https://github.com/user-attachments/assets/9bbd7db8-9e70-4f88-b6f1-5c7446c5bf5f" />

<img width="756" height="516" alt="image" src="https://github.com/user-attachments/assets/67378292-a6a2-4c0b-9d9d-cc87716acbe7" />

---

### Cliquem a "select a principal" i dintre escribim: "Domain users"

<img width="731" height="448" alt="image" src="https://github.com/user-attachments/assets/f67632b1-0aae-43bd-b9ee-6b38bba0a8ce" />

<img width="491" height="305" alt="image" src="https://github.com/user-attachments/assets/73924a54-999f-4903-801e-8ba3483ac929" />

### Una vegada seleccionat anem a "Show Advanced permissions" i deixarem els següents permissos seleccionats:

- This folder only
- Traverse folder/Excectute
- List Folder/Read Data
- Read attributes
- Read extended attributes
- Read permissions

> *Important* Aplicar despres d'editar a "Apply"

<img width="885" height="573" alt="image" src="https://github.com/user-attachments/assets/4a20cf28-4213-4e1d-b000-5a2a33b900ae" />


---

### Mirem si s'ha aplicat seleccionant el principal "Domain Users" i clicant a "Effective Access" 

<img width="766" height="509" alt="image" src="https://github.com/user-attachments/assets/babf3964-f1bd-4a39-b2cf-5220d1e7ccb1" />

---

## 3. Ara crearem una plantilla d’usuari per cadascun dels grups:

- Gestio
- Magatzem
- Gerencia

---

### Com amb els grups el que farem serà entrar al apartat de AD DS, fer clc dret al nostre server i escollir l'opció de "Active Directory Users and Computers":

<img width="920" height="447" alt="image" src="https://github.com/user-attachments/assets/fe0a88db-3133-429b-8f70-3d90e3d28b23" />

---

### Per crear la plantilla dels usuaris anirem a la OU creada al principi que en aquest cas es la de "Usuaris" > New > User.

<img width="577" height="440" alt="image" src="https://github.com/user-attachments/assets/79f75291-ec96-414d-89e1-739ada7e43c2" />

---

### Possarem el nom de el usuari a la part de "Firts name", a "User Logon name" amb un guio baix perque ens sorti al principi i Next.

<img width="470" height="423" alt="image" src="https://github.com/user-attachments/assets/27a5646d-279e-4867-96da-1233f06a7071" />

---

### Treiem la opció de "User must change password at next logon" i deixem la de "Account is disabled", next i per acabar "Finish".

<img width="446" height="401" alt="image" src="https://github.com/user-attachments/assets/ce8d4966-a1ce-46a9-9333-62ed4db3a312" />

<img width="447" height="393" alt="image" src="https://github.com/user-attachments/assets/7c2f2ff9-34c8-461e-82ec-f961508109fa" />

---

### Afegim l'usuari al grup corresponent, en aquest cas seria Gestió:

<img width="475" height="281" alt="image" src="https://github.com/user-attachments/assets/6157293e-04d0-4784-9e03-a54daed61603" />

> **Important:** No t'oblidis Fer lo mateix amb els altres usuaris 

---

### Ara Configurem la carpeta personal anant a: properties > profile, i la carpeta en aquest cas serà la "F:"

<img width="797" height="633" alt="image" src="https://github.com/user-attachments/assets/d4ed8874-9e92-4459-b732-6367eb2d7610" />

<img width="456" height="591" alt="image" src="https://github.com/user-attachments/assets/dcf33cfb-d29c-4389-adbd-5035554c1b67" />

> *Importatnt* Fer lo mateix als altres usuaris

### Ens quedarà tal que aixi:

<img width="781" height="598" alt="image" src="https://github.com/user-attachments/assets/a6b50d7f-309e-45c8-85a1-310fa5b4f7d2" />

---

## 4. usuaris de prova a partir de les plantilles

### Per crear usuaris basats en plantilla, fem clic dret sobre la plantilla i Copy

<img width="557" height="461" alt="image" src="https://github.com/user-attachments/assets/17d35ffd-1dad-42ca-ab0c-64bd48d04b98" />

---

### L'usuari de prova per Gerencia que farem serà: Pau Martinez

<img width="488" height="457" alt="image" src="https://github.com/user-attachments/assets/4d785c1c-c153-4704-92ff-b6f8332ac531" />

---

### Li ficarem una contrasenya que en aquest cas serà: Jancito_10, i deixem l'opcio de "User must change password at next logon"

<img width="488" height="432" alt="image" src="https://github.com/user-attachments/assets/2ca593ce-2dd3-4a58-89ff-dd5a5e078078" />

---

### Ara ens quedarà clicar a "finish"

<img width="443" height="395" alt="image" src="https://github.com/user-attachments/assets/15c38e1a-19fd-48f7-9117-92d14fed40b4" />

---

### Fem un altre compte per Gestio que es dirà Pol Hernandez amb la mateixa contrasenya:

<img width="467" height="397" alt="image" src="https://github.com/user-attachments/assets/0aa7d6a7-0c94-4638-849c-b025c0fbf027" />

---

### i un altre compte per magatzem que es dirà Biel Perez amb la mateixa contrasenya:

<img width="458" height="394" alt="image" src="https://github.com/user-attachments/assets/f54aaf87-3bb7-42a2-b00f-49e760bc831a" />

---

### comprovem si s'han creat els arxius dintre de Homes:

<img width="727" height="428" alt="image" src="https://github.com/user-attachments/assets/a0ea9de9-d6b8-4f30-9b83-de0fc24087c9" />

---

## 5. Aprovisionar un equip "PC1" al domini

### Primer farem una nova OU que es dirà: equips. Dintra d'aquesta crearem un nou "Computer" d'aquesta forma:

<img width="832" height="563" alt="image" src="https://github.com/user-attachments/assets/87795b97-61b2-4fc5-bc27-73a3db08108e" />

<img width="488" height="404" alt="image" src="https://github.com/user-attachments/assets/223b771b-c4c2-4b1a-9823-730ddf01e030" />

---

### Anem al Server Manager del DNS on podem veure les IP del DC

<img width="709" height="265" alt="image" src="https://github.com/user-attachments/assets/845e1c9c-878f-4138-8b4d-fe38d5decb75" />

---

## Crear una VM Windows 11 i unir-la al domini

### Crear una VM amb:

- Windows 11
- 4 GB RAM
- Disc suficient
- Xarxa NAT (segons enunciat)

---

### Configurem el DNS del client apuntant al DC

<img width="552" height="676" alt="image" src="https://github.com/user-attachments/assets/1ef88630-b84b-4fd6-b454-dcd9d009698f" />

---

### Cambiem el nom del pc per: PC-1

<img width="747" height="465" alt="image" src="https://github.com/user-attachments/assets/aa03621e-15b4-419f-95f8-dfe97cd2f10d" />

---

### A lqa part de Sistema > Informació baixem fins trobar: Dominio o grupo de trabajo

<img width="644" height="604" alt="image" src="https://github.com/user-attachments/assets/0137135b-086d-48d1-b691-b0653aba7cd2" />

---

### Ens sortira una finestra amb les Propietats del sistema, anirem a l'apartat de "Nombre de equipo" i anirem a cambiar el domini del pc per el nostre cas: translogic09.test

<img width="404" height="493" alt="image" src="https://github.com/user-attachments/assets/aa6e53e6-4fc4-4b8a-aee2-fcf6e6f7d064" />

<img width="333" height="404" alt="image" src="https://github.com/user-attachments/assets/3f17e7ef-2f07-485e-9d10-770ac9c636e6" />

---

### Ens hauria de sortir una notificació en el cas de que es connecti correctament al domini:

<img width="402" height="191" alt="image" src="https://github.com/user-attachments/assets/dc4872db-0ad4-403a-b6a2-cd1e757cc329" />

---

### Per acabar haurem de reiniciar el PC per aplicar els cambis

<img width="377" height="207" alt="image" src="https://github.com/user-attachments/assets/a7931569-c9fe-4c2b-9217-a3bc70d4085d" />

---

## Comprovació: inici de sessió amb usuaris de prova

### Ho haurem de fer amb els tres usuaris:

---

### Primer ho Farem amb l'usuari Pau Martinez

<img width="709" height="659" alt="image" src="https://github.com/user-attachments/assets/e7a19ccb-0015-4a7f-a2c6-5bb01216769d" />

<img width="621" height="740" alt="image" src="https://github.com/user-attachments/assets/03922563-8602-4276-8c4a-7555179b5aa5" />

---

### Entrem al explorador d'arxius i veiem que s'ens ha creat un disc amb el nom d'usuari

<img width="788" height="586" alt="image" src="https://github.com/user-attachments/assets/a2c71226-d41a-4de9-9876-efd9308b69a1" />

---

### Ara ens connectarem amb la compte de Pol Hernandez

<img width="695" height="610" alt="image" src="https://github.com/user-attachments/assets/3e40f9f2-c40a-4570-9730-d1c63eca6697" />

cc.1234.cc


---

### Entrem al explorador d'arxius i veiem que s'ens ha creat un disc amb el nom d'usuari

<img width="815" height="624" alt="image" src="https://github.com/user-attachments/assets/2f070548-6905-41e6-b588-cc9676946c5a" />


---

### Ara ens connectarem amb la compte de Biel perez


<img width="549" height="586" alt="image" src="https://github.com/user-attachments/assets/13a4dc62-7e76-4059-bde6-b06572b5f6a2" />


---

### Entrem al explorador d'arxius i veiem que s'ens ha creat un disc amb el nom d'usuari

<img width="777" height="545" alt="image" src="https://github.com/user-attachments/assets/ca2c9afe-0c24-4e6d-a5a8-1a9b18fe5ce3" />



[torna a la pàgina principal](../README.md)


