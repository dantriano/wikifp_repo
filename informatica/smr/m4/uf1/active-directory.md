---
title: Instal·lació del servei d'Active Directory
description: 
published: true
date: 2022-02-10T16:24:43.300Z
tags: 
editor: markdown
dateCreated: 2022-02-10T16:24:43.300Z
---

<!--- [:clipboard: Solucions *Accedeix als resultats dels exercicis (Només professors)*](solucions)
{.links-list}-->
# :pencil: Pràctica

### Realitzeu la configuració següent per promoure el servidor. 
Documenta corrèctament el procés i els exercicis plantejats a continuació. L'entrega deurà complir amb les normes d'estil i ser entregada en format pdf o markdown.

1. Configurar l’equip Windows Server com un controlador de domini.
2. Muntarem una infraestructura de domini per a l’empresa CFEDTXX(Cicles Formatius Escola del Treball XX=num de PC)
*NOTA: Recordeu elaborar una documentació del procés d’instal·lació dels serveis amb captures dels passos realitzats.*
3. Instal·la els serveis de Domini d’Active Directory. El que farem serà assignar un rol a l’equip, concretament el de Controlador de domini. Fixeu-vos bé en tot allò que necessita.
4. Veurem que tenim instal·lats els serveis però l’equip encara no es un controlador de domini.

### Promoure l’equip a controlador de domini.
1. Executa el programa que ens guiarà en el procés de promoció a controlador de domini. Cerqueu com fer-ho tant per entorn gràfic com per terminal. *No cal realitzar les dues formes, sols cercar com fer-ho.*
2. A la primera pantalla de configuració seleccionem crear un domini nou a un bosc nou.
3. Introduirem el nom complet del nostre domini arrel, que és el primer del bosc.
   *En el nostre cas introduirem CFEDTXX.es. On XX serà el nombre de la màquina física.*
4. Comprovar el nom a la següent pantalla, introduïm com integrarem el nostre domini amb altes dominis amb el Nivell funcional del bosc. Seleccionarem el Windows Server més actual.

# :pencil: Preguntes
1. A l’apartat de revisió de la configuració falta algun dels elements que ens avisa l’instal·lador, quin és? *Nota: no cal activar-lo.*
2. En cas de tenir algun altre servidor amb windows 2003 instal·lat, quin nivell funcional hauríem d’utilitzar?
3. Podem modificar el destí? I el seu nom?. És també obligatori que la partició sigui de tipus NTFS? 