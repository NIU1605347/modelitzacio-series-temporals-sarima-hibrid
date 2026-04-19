# Modelització i anàlisi de sèries temporals per a la vigilància sindròmica mitjançant models SARIMA i híbrids SARIMA–NNAR

Aquest projecte desenvolupa un marc de predicció de sèries temporals aplicat a la vigilància sindròmica en atenció primària a Catalunya, amb l’objectiu de modelitzar la incidència de malalties infeccioses i analitzar la seva dinàmica temporal en dades reals.

La metodologia combina models estadístics clàssics (SARIMA) amb models híbrids, en què xarxes neuronals autoregressives (NNAR) s’utilitzen per capturar patrons no lineals presents en els residus.

L’anàlisi es basa en dades epidemiològiques setmanals entre 2012 i 2024, i ha estat desenvolupat com a Treball de Fi de Grau en Matemàtiques a la Universitat Autònoma de Barcelona.

---
## Objectiu del projecte

L’objectiu principal és modelitzar i predir sèries temporals epidemiològiques per tal de:

- Detectar patrons anòmals en la incidència de malalties
- Analitzar la dinàmica estacional i estructural
- Avaluar la robustesa dels models estadístics i híbrids
- Comparar el comportament dels models en diferents períodes (COVID i post-COVID)

---

## Metodologia

El projecte s’estructura en quatre blocs principals:

### 1. Anàlisi detallada de models SARIMA sobre sèries representatives
S’estudien en profunditat quatre sèries temporals epidemiològiques representatives seguint la metodologia de Box–Jenkins. Aquesta part inclou l’anàlisi exploratòria, l’estudi de l’estacionarietat, la identificació del model, l’ajust, el diagnòstic de residus, la predicció i l’avaluació.

### 2. Modelització híbrida (SARIMA + NNAR)
Per a cadascuna de les sèries representatives es construeix un model híbrid combinant:
- un model SARIMA per capturar l’estructura lineal
- un model de tipus NNAR aplicat als residus del SARIMA per capturar possibles dependències no lineals

La predicció final s’obté combinant la predicció del SARIMA amb la predicció dels residus generada pel model NNAR.

### 3. Automatització SARIMA a gran escala (180 sèries temporals)
La metodologia SARIMA s’estén a 180 sèries temporals mitjançant un pipeline automatitzat. Els models candidats s’exploren amb grid search i es seleccionen mitjançant validació rolling, conjuntament amb criteris d’informació i diagnòstic de residus.

Aquesta fase inclou:
- ajust automàtic de models SARIMA
- comparació entre models candidats
- validació rolling
- predicció i càlcul de mètriques
- emmagatzematge dels models seleccionats i dels resultats

### 4. Automatització híbrida a gran escala
A partir dels models SARIMA seleccionats, es construeix un segon pipeline automatitzat per ajustar models híbrids SARIMA–NNAR al conjunt complet de sèries.

Aquesta fase inclou:
- extracció dels residus del SARIMA després del burn-in
- entrenament de models de tipus NNAR sobre retards dels residus
- selecció d’hiperparàmetres mitjançant validació rolling
- predicció híbrida
- comparació del rendiment respecte del model SARIMA de referència
