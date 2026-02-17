# 🎭 Face Recognition Pipeline: De la Détection à l'Identification

Ce projet implémente un système complet de traitement d'images faciales, structuré en un pipeline à deux étapes : la **détection** (localisation) et la **reconnaissance** (identification). 

Réalisé par : **Jessica Rasoamanana** & **Alexandre Baudin**

## 📂 Structure du Dépôt

Le projet s'appuie sur une démarche progressive documentée dans trois Notebooks :
* **`Full project.ipynb`** : Le cœur du projet. Il consolide le pipeline final et les benchmarks avancés (CNN inclus). Une version HTML est fournie pour une consultation rapide sans exécution.
* **`TP_Enonce_Facedetection.ipynb`** : Travaux préparatoires sur la détection classique (Haar Cascades) et les flux vidéo temps réel.
* **`Face recognition.ipynb`** : Études préliminaires sur l'extraction de caractéristiques (HOG, PCA) et les classifieurs classiques.

## 🚀 Étape 1 : Détection de Visages
L'objectif est de comparer la robustesse des algorithmes pour localiser un visage dans une image brute.

* **Méthodes comparées :** Haar Cascades (Viola-Jones) vs MediaPipe (Deep Learning).
* **Dataset :** CelebA (sous-ensemble de 600 images). *Note : Importé localement pour garantir la stabilité de l'accès aux données.*
* **Métrique :** **IoU (Intersection over Union)**.
* **Résultat :** **MediaPipe** s'est révélé nettement supérieur avec un score IoU moyen de **0.49** et un taux de détection précise de **72%** (contre 47% pour Haar).



## 🧠 Étape 2 : Reconnaissance Faciale
Une fois le visage détecté et recadré, nous identifions l'individu parmi 40 classes.

* **Dataset :** Olivetti Faces (400 images, 40 individus).
* **Modèles testés :**
    * **ACP (Eigenfaces) + Arbre de décision**
    * **HOG + Arbre de décision**
    * **HOG + Random Forest** (Modèle retenu : **82.5% d'accuracy**, **0.94 F1-score** en CV)
    * **CNN (Convolutional Neural Network)** : Architecture Keras Conv2D/MaxPooling.



## 🛠️ Stack Technique

* **Computer Vision :** OpenCV, MediaPipe, Scikit-Image.
* **Machine Learning & Deep Learning :** Scikit-Learn, TensorFlow, Keras.
* **Analyse de données :** NumPy, Pandas, Matplotlib.

## 📊 Synthèse des Performances

| Pipeline de Reconnaissance | Accuracy (Test) | F1-Score (CV) |
| :--- | :---: | :---: |
| ACP + Decision Tree | 45.0% | 0.52 |
| HOG + Decision Tree | 36.7% | 0.41 |
| **HOG + Random Forest** | **82.5%** | **0.94** |
| **CNN** | **78.3%** | **-** |

## ⚙️ Installation & Utilisation

1.  **Prérequis :**
    Assurez-vous d'avoir le dossier `Dataset CelebA` à la racine du projet (contenant les images et les labels YOLO).
2.  **Dépendances :**
    ```bash
    pip install mediapipe opencv-python tensorflow scikit-learn scikit-image datasets
    ```
3.  **Exécution :**
    Ouvrez `Full project.ipynb` pour tester le pipeline complet. Pour une détection via WebCam, utilisez le script dédié dans le notebook de détection.

---
*Projet réalisé dans le cadre du cursus ingénieur à l'EFREI Paris (Majeure Imagerie & Réalité Virtuelle / IA).*
