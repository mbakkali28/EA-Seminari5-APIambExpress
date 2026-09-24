### Secció d'Ús d'IA Generativa

**Eina i Model utilitzat**: Gemini 3.6 Flash via su WEB

---

### Prompts

#### Prompt 1:
* **Prompt literal**:
  > *"¿Existen funciones para que cuando haga funciones de quitar y añadir tag para que no me añada un tag cuando ya lo tiene y que no borre si no lo tiene?"*
* **Resposta de la IA**:
  Confirmació que MongoDB disposa d'operadors d'actualització natius molt eficients per gestionar arrays. S'ha detallat l'ús de `$addToSet` per afegir elements evitant duplicats a la base de dades i de `$pull` per eliminar-ne si existeixen sense generar cap error si no hi són, evitant així haver de llegir l'array prèviament des del backend.
* **Incoherències detectades**: 
  Cap incoherència tècnica.
* **Solució / Adaptació manual**: 
  S'han integrat els operadors `$addToSet` i `$pull` directament a les funcions del servei (`addTag` i `removeTag`) utilitzant `findByIdAndUpdate`.

---

#### Prompt 2:
* **Prompt literal**:
  > *"¿Por qué hace falta validar los tags con Joi al igual que en los books con addTag y replaceTags? Explícame un poco sobre Joi."*
* **Resposta de la IA**:
  Explicació sobre la importància de validar les peticions HTTP a la capa d'API REST mitjançant esquemes de Joi abans d'arribar a la base de dades. S'ha detallat l'ús de `Joi.string().valid(...)` per restringir els valors permesos d'un llistat definit de tags, l'aplicació de `.trim()` per netejar espais residuals i l'ús de `Joi.array().items(...)` amb `.unique()` per assegurar que no s'enviïn arrays amb duplicats.
* **Incoherències detectades**: 
  Cap incoherència tècnica.
* **Solució / Adaptació manual**: 
  S'ha creat l'objecte de validació de schemas amb Joi adaptat dels de books.
