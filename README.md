# 🧠 NLP-Projekt: Klassifizierung von Katastrophen-Tweets

Dieses Projekt entwickelt ein NLP-Modell, das Tweets automatisch als Katastrophe (1) oder Nicht-Katastrophe (0) einordnet. Dazu wurden umfangreiche Schritte zur Datenaufbereitung, mehrere Machine-Learning-Modelle (Logistische Regression, RandomForest, Neuronales Netz/MLP) sowie Optimierungsverfahren eingesetzt, um eine möglichst zuverlässige Klassifikation zu erreichen.

### Vorgehensweise
1. Datenaufbereitung

Die Textdaten wurden gründlich bereinigt. Dazu gehörten:

- Umwandlung in Kleinbuchstaben

- Entfernen von Satzzeichen & Sonderzeichen

- Entfernen englischer Stoppwörter

- Lemmatisierung (z. B. „running“ → „run“)

### 2. Vektorisierung

Die Texte wurden mit TF-IDF (TfidfVectorizer) in numerische Features umgewandelt.
Die Anzahl der Features wurde dabei auf 5.000 Merkmale begrenzt.

### 3. Modellauswahl

Es wurden drei Modelle trainiert und analysiert:

- Logistische Regression

- RandomForest

- Neuronales Netz (MLPClassifier)

### 4. Validierung & Optimierung

Cross-Validation:
5-fache Kreuzvalidierung zeigte eine robustere mittlere Genauigkeit von ca. 70 %.

Hyperparameter-Tuning (GridSearchCV):
Optimale Parameter für die Logistische Regression wurden bestimmt.
Das bestätigte, dass die Standardparameter bereits ein stabiles Setup lieferten.

## **Ergebnisse & Erkenntnisse**

### Gesamtgenauigkeit (Accuracy):

Logistische Regression: 79.84 %

Neuronales Netz (MLP): 79.71 %

Random Forest: 77.08 %

Die Logistische Regression und das MLP lieferten die besten Gesamtergebnisse.

### Modellvergleich & Bewertung

1. Analyse der Katastrophen-Klasse (Recall für Klasse 1)

**Ziel:** möglichst wenige echte Katastrophen übersehen (minimale False-Negatives)

- Random Forest: erkannte 209 Katastrophen → Recall: 0.68

- Logistische Regression: erkannte 212 Katastrophen → Recall: 0.67

- MLP: erkannte 222 Katastrophen → Recall: 0.66

Der Random Forest hat zwar geringere Gesamtgenauigkeit, ist aber am sensitivsten für echte Katastrophen.

2. Analyse der Nicht-Katastrophen-Klasse (Recall für Klasse 0)

Ziel: Fehlalarme vermeiden (minimale False-Positives)

- MLP: 87 Fehlalarme → Recall: 0.90

- Logistische Regression: 95 Fehlalarme → Recall: 0.89

- Random Forest: 140 Fehlalarme → Recall: 0.84

➡️ Das MLP ist das „vorsichtigste“ Modell und vermeidet am zuverlässigsten Fehlalarme.

## Zusammenfassung des Modellvergleichs

Es gibt keinen absoluten Gewinner — die Entscheidung hängt vom Ziel ab:

Wenn hohe Genauigkeit & geringe Fehlalarme wichtig sind:
➜ MLP oder Logistische Regression

Wenn möglichst viele echte Katastrophen erkannt werden sollen:
➜ Random Forest

