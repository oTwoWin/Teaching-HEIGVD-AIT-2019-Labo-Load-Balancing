# Task 5

Pour cette partie du laboratoire, il nous est demandé de découvrir `HAProxy` et de prendre deux stratégies différentes afin de les analyser grâce à l'outil `JMeter`. Après avoir lu les différentes stratégies, nous avons choisi les stratégies **first** et **leastconn**. Nous traiterons différents cas que nous analyserons et dont on tirera une conclusions.

### 1. Configurations de HAProxy

#### 1.1 Stratégie *first*

Afin de configurer *HAProxy* avec la stratégie *first*, nous avons dû la spécifier dans le fichier de configuration *haproxy.cfg* mais nous avons dû également spécifier le nombre de connexions maximum simultanées sur chaque serveur. Nous avons décidé de mettre ce nombre à 5.

Ci-dessous, une partie du fichier haproxy.cfg contenant les modifiations

![image-20191130135522507](/home/ljebool/.config/Typora/typora-user-images/image-20191130135522507.png)

#### 1.2 Stratégie *leastconn*

Afin de configurer *HAProxy* avec la stratégie *fleastconn*, nous avons dû la spécifier dans le fichier de configuration *haproxy.cfg* 

Ci-dessous, une partie du fichier haproxy.cfg contenant les modifications:

![image-20191130135649597](/home/ljebool/.config/Typora/typora-user-images/image-20191130135649597.png)

### 2. 1er cas 

#### 1.1 Configurations des serveurs

- 0 ms sur les deux serveurs

  ![image-20191130135840601](/home/ljebool/.config/Typora/typora-user-images/image-20191130135840601.png)

#### 1.2 Configurations de JMeters

- 50 utilisateurs (threads)

- 100 requêtes chacuns

- Cookies activés 

  ![image-20191130140740734](/home/ljebool/.config/Typora/typora-user-images/image-20191130140740734.png)

#### 1.3 Résultats Jmeters

##### 		**first**:

​		![image-20191130141200848](/home/ljebool/.config/Typora/typora-user-images/image-20191130141200848.png)

​		**leastconn**:

![image-20191130141010888](/home/ljebool/.config/Typora/typora-user-images/image-20191130141010888.png)



### 2. 2ème cas 

#### 1.1 Configurations des serveurs

- 0 ms sur les deux serveurs

  ![image-20191130135840601](/home/ljebool/.config/Typora/typora-user-images/image-20191130135840601.png)

#### 1.2 Configurations de JMeters

- 50 utilisateurs (threads)

- 100 requêtes chacuns

- Cookies désactivés 

  ![image-20191130140740734](/home/ljebool/.config/Typora/typora-user-images/image-20191130140740734.png)

#### 1.3 Résultats Jmeters

##### 		**first**:

![image-20191130140936149](/home/ljebool/.config/Typora/typora-user-images/image-20191130140936149.png)

​		**leastconn**:

![image-20191130141053524](/home/ljebool/.config/Typora/typora-user-images/image-20191130141053524.png)



### 3. 3ème cas 

#### 1.1 Configurations des serveurs

- 200ms pour le serveur `s1`

- 50ms pour le serveur `s2`

  ![image-20191130141417296](/home/ljebool/.config/Typora/typora-user-images/image-20191130141417296.png)

#### 1.2 Configurations de JMeters

- 50 utilisateurs (threads)

- 10 requêtes chacuns

- Cookies activés 

  ![image-20191130141622417](/home/ljebool/.config/Typora/typora-user-images/image-20191130141622417.png)

#### 1.3 Résultats Jmeters

##### 		**first**:

![image-20191130141708294](/home/ljebool/.config/Typora/typora-user-images/image-20191130141708294.png)

​		**leastconn**:

![image-20191130141938887](/home/ljebool/.config/Typora/typora-user-images/image-20191130141938887.png)



### 4. 4ème cas 

#### 1.1 Configurations des serveurs

- 200ms pour le serveur `s1`

- 50ms pour le serveur `s2`

  ![image-20191130141417296](/home/ljebool/.config/Typora/typora-user-images/image-20191130141417296.png)

#### 1.2 Configurations de JMeters

- 50 utilisateurs (threads)

- 10 requêtes chacuns

- Cookies désactivés 

  ![image-20191130141622417](/home/ljebool/.config/Typora/typora-user-images/image-20191130141622417.png)

#### 1.3 Résultats Jmeters

##### 		**first**:

![image-20191130141910656](/home/ljebool/.config/Typora/typora-user-images/image-20191130141910656.png)

​		**leastconn**:

![image-20191130141949337](/home/ljebool/.config/Typora/typora-user-images/image-20191130141949337.png)



