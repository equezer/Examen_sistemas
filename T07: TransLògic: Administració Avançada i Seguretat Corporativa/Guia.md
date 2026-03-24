# **T07: TransLògic: Administració Avançada i Seguretat Corporativa**




## Abans de començar

En aquesta pràctica hem mantingut la configuració passada, únicament haurem de crear una OU per als usuaris de gerència

Això ho farem per poder afegir configuracions especials al grup de gerència, ja que són usuaris que és important afegir una capa extra de seguretat

---

1\. Polítiques de Seguretat i Contrasenyes (Seguretat Corporativa)

El primer pas que ens demana el client és obligar els usuaris a utilitzar contrasenyes més robustes

La forma més fàcil de fer-ho és modificar la GPO, per fer-ho el primer pas serà saber quines GPO s'apliquen a l'usuari; per fer-ho anirem a la màquina client i col·locarem la següent comanda a la terminal

```powershell
gpresult /R
```
Un cop que ja sabem quines GPO hem de modificar anirem al Windows Server i a l'apartat de Tools veurem "Group Policy Management"


En aquest modificarem la política de contrasenyes per a tots els usuaris de domini sense tenir en compte les GPO; per tant haurem d'anar a Default Domain i editar-lo

![img](img/2.png)

Un cop que estem dins haurem d'anar fins a "Password Policy"

![img](img/3.png)

Un cop que hem arribat haurem de modificar el següent 

![img](img/4.png)

![img](img/5.png)

Un cop que ja hem modificat les polítiques globals el següent pas serà obligar que els usuaris de Gerència tinguin una contrasenya de mínim 28 caràcters i que caduqui cada 28 dies

Per tant el que farem serà crear una OU exclusiva per als usuaris de gerència per poder aplicar totes les polítiques de gerència

![img](img/6.png)

Un cop que ja tenim la OU creada haurem d'afegir el grup de Gerència dins de la OU i els usuaris

![img](img/7.png)


Un cop fet això modificarem la política tal com hem fet abans, però ara ho farem amb la OU gerència.

Per fer-ho el primer pas serà crear la GPO

![img](img/8.png)

![img](img/9.png)

Un cop que ja tinguem la GPO creada el següent pas serà modificar la política; en aquest cas ens demana que la contrasenya sigui de 18 caràcters i caduqui cada 28 dies.

Haurem de modificar el següent

![img](img/10.png)

![img](img/11.png)

![img](img/12.png)

Com a bonus podríem afegir que en els grups de gerència tinguessin un bloqueig de pantalla automàtic per si de cas deixen l'ordinador sense bloquejar.

Per tant crearem una nova GPO en la OU de gerència; en aquest cas l'anomenarem salvapantalles

![img](img/13.png)

Un cop fet buscarem l'opció de machine inactivity limit i afegirem el temps; en aquest cas col·locarem 2 minuts

![img](img/14.png)


---

2\. Desplegament Automatitzat de Programari

Com a segona cosa que ens demana el client és automatitzar la instal·lació d'eines segons el departament.

Per començar ens demana que el grup de gestió tingui l'eina de compressió 7zip per gestionar factures.

Per començar haurem de crear una carpeta compartida on ubicarem l'eina de 7zip

En aquest cas anomenarem soft a la carpeta

![img](img/15.png)

En aquest cas compartirem perquè tothom pugui veure aquesta carpeta

![img](img/16.png)

Haurem d'instal·lar el paquet 7zip.msi d'internet i col·locar-lo a la carpeta

Un cop fet això el següent pas que farem serà crear la GPO; en aquest cas l'aplicarem a la OU de groups però que únicament apliqui a gestió

![img](img/17.png)

Un cop dins haurem de crear la directiva

![img](img/18.png)

Un cop fet això haurem de seleccionar la ruta; en aquest cas hem de seleccionar la ruta de xarxa ja que si no el client no la trobarà

![img](img/19.png)

I escollirem l'Advanced

![img](img/20.png)

Un cop fet això marquem que s'instal·li automàticament amb el logon de l'usuari

![img](img/21.png)

Un cop fet això l'aplicació s'instal·larà el següent cop que l'usuari iniciï sessió

Podem veure que 7Zip està instal·lat correctament

![img](img/36.png)


El següent pas que ens demana és fer el mateix però perquè el grup de gerència tingui un navegador més segur; en aquest cas ens demana Firefox, però en aquest cas l'usuari decideix si l'instal·la des del Tauler de Control.

Per tant el primer pas serà instal·lar el paquet Firefox d'internet

![img](img/22.png)

Un cop fet això haurem de crear la GPO, en aquest cas que únicament apliqui al grup de gerència

Haurem de fer el mateix que en el cas de 7zip però a l'hora d'establir les propietats les haurem de modificar de la següent forma

![img](img/23.png)

![img](img/24.png)

Un cop fet podem veure que podem instal·lar l'aplicació des del panell de control

![img](img/35.png)


Un cop fet això ens pregunta:

Com podem crear els nostres propis fitxers .msi si una aplicació només ve amb un .exe?

Per fer-ho tenim diversos mètodes; el primer és reempaquetar l'.exe en un .msi amb una aplicació com per exemple Advanced Installer o WiX Toolset.

Una altra opció és crear un MSI que executi l'exe


---

3\. Mobilitat d'Usuaris (Perfils Mòbils)

El següent pas que ens demana és habilitar els perfils mòbils ja que els usuaris del departament de gestió canvien sovint entre un portàtil o amb un equip d’escriptori.

Per tant el primer pas serà habilitar una carpeta compartida al servidor anomenada perfils

![img](img/25.png)

Un cop fet això compartim la carpeta i apliquem els permisos

![img](img/28.png)

![img](img/29.png)

Un cop que ja estigui això fet en aquest cas ens demana que els usuaris de gestió; per tant editarem la plantilla gestió

![img](img/26.png)

Un cop fet això crearem un usuari nou i iniciarem sessió per comprovar que funciona correctament

En aquest cas hem creat un usuari anomenat usuari mobil

![img](img/27.png)

Podem veure que si iniciem sessió amb l'usuari tenim la carpeta dins de perfils.

![img](img/30.png)


---

4\. Seguretat de Dades (Redirecció de Carpetes)

Un cop que ja tenim els perfils mòbils funcionant el següent pas que farem serà afegir una capa de seguretat per poder evitar pèrdua de dades.

Per fer-ho farem una redirecció de carpetes perquè la carpeta local Documents es redirigeixi a una ubicació de xarxa segura.

Per tant el primer pas serà anar a la GPO de domini

![img](img/31.png)

Un cop dins editarem les propietats de la carpeta Documents

![img](img/32.png)

Un cop fet això des del client podem veure que la carpeta Documents està compartida

![img](img/33.png)

![img](img/34.png)

---

5\. Delegació de Funcions (Helpdesk)

Per últim ens han avisat que han contractat un auxiliar de suport. 

Per tant ens demanen que creem un usuari per a ell; aquest usuari únicament ha de poder reiniciar contrasenyes dels treballadors i modificar la pertinença als grups.

El primer pas serà crear l'usuari dins de la OU d'usuaris; en aquest cas s'anomenarà adminOU 

![img](img/37.png)

Un cop que ja tenim l'usuari creat el següent pas serà aplicar la delegació

![img](img/38.png)


Per fer-ho haurem d'afegir l'usuari 

![img](img/39.png)

En aquest cas únicament ens demana que pugui reiniciar contrasenyes dels treballadors i modificar la pertinença als grups.

Per tant únicament haurem de marcar les següents caselles

![img](img/40.png)

Un cop fet això iniciem sessió a l'equip client per comprovar que podem canviar la contrasenya dels usuaris dins de la nostra OU

![img](img/41.png)

En canvi si ho intentem a la OU de gerència podem veure que no podrem

![img](img/42.png)

I també podem modificar els grups dels usuaris dins de la OU d'usuaris

![img](img/43.png)

I per últim podem veure que fora de la OU d'usuaris no podem crear usuaris i grups

![img](img/44.png)