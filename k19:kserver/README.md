# Kerberos kserver
## @edt ASIX M11-SAD Curs 2019-2020

**edtasixm11/k19:kserver** servidor kerberos detach. Crea els usuaris pere
  pau, jordi, anna, marta, marta/admin, julia, user01..user05, super (rol admin)
  i amin (rol admin)
  Assignar-li el nom de host: *kserver.edt.org*

Servidor kerberos. Aquest servidor crea els principals corresponents als clàssics
usuaris que tenim també a ldap.

Les característiques principals són:
 * s'ha d'anomenar kserver.edt.org
 * crea els principals pere(kpere) pau(kpau), jordi(kjordi), 
   anna (kanna), marta (kmarta), marta/admin (kmarta rol:admin), julia (kjulia) 
   , admin (kadmin rol:admin) i super (ksuper rol admin).
   Crea també els principals user01...user06 amb passwd (kuser01...kuser06).
 * es crea un principal de host corresponent al servidor host/sshd.edt.org.
 * tot el procés és automatitzat i el servidor s'executa detach.

### Execució:

Execució local
```
docker run --rm --name kserver.edt.org -h kserver.edt.org --net mynet -s edtasixm11/k19:kserver
```

Execució en AWS EC2
```
docker run --rm --name kserver.edt.org -h kserver.edt.org -p 88:88 -p 749:749 -p 464:464 --net mynet  -d edtasixm11/k19:kserver
```

Test de verificació:

 * des de un host client instal·lar krb5-worksation
 * configurar /etc/krb5.conf
 * kinit usuari

