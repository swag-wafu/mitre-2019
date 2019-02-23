# PGP - Crypto (50 pts)

## Description

Quatre fichiers sont fournis :
- key.enc (Fichier chiffré)
- flag.html.enc (Fichier chiffré)
- mitre-ctf-2019-private.enc (Clé privée PGP)
- passphrase (associé à la clé privée)

L'idée est d'apprendre à utiliser PGP.

## Soluce

- Première étape :
Utiliser *gpg2* ou un utilitaire graphique (*gpa*) pour importer la clé PGP privée (mitre-ctf-2019-private.enc).
Celle-ci permet ensuite de déchiffrer des fichiers chiffrés par PGP. En testant sur les différents fichiers, on voit que
key.enc peut être déchiffré. Aucun autre fichier ne semble pouvoir être déchiffré avec PGP.

- Deuxième étape :
En analysant le fichier key obtenu, on voit qu'il fait 256 octets, la taille d'une clé AES-256.
Le fichier chiffré flag.html.enc analysé via binwalk révèle qu'il s'agit d'une chaîne chiffré et salé via openssl.
En testant aes-256-cbc sur le fichier avec le fichier key grâce à la commande suivante, on obtient le contenu du fichier flag.html.enc

`openssl aes-256-cbc -kfile decrypted_key -d -in flag.html.enc -out flag`

Le flag obtenu est donc : 
`MCA{66b2f50cd2d6b9622c6be902ee2b0976badb4684}`
