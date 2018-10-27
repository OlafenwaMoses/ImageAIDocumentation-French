.. ImageAI documentation master file, created by
   sphinx-quickstart on Tue Jun 12 06:13:09 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Apprentissage personnalisé et prédiction des Classes
======================================
**ImageAI** fournit des classes puissante et néanmoins facile à utiliser pour entrainer des algorithmes a la pointe de la technologies tel que **SqueezeNet**, **ResNet** , **InceptionV3** et  **DenseNet** sur votre propre base de données avec juste  **5 lignes de code** pour générer votre propre modèle personnalisé. 
Une fois que vous avez entrainé votre propre modèle, vous pouvez utiliser la classe **CustomImagePrediction** fournit par **ImageAI** pour utiliser votre modèle pour reconnaitre et faire la détection sur une image ou un ensemble d’images. 



**======= imageai.Prediction.Custom.ModelTraining =======**



La classe **ModelTraining** vous permet d’entrainer un des quatre algorithme d’apprentissage profond suivant (**SqueezeNet**, **ResNet**
, **InceptionV3** et **DenseNet**) sur votre base de données d’images pour générer votre propre modèle. Votre base de données d’images doit contenir au moins deux différentes classes/types d’images (chat et chien) et vous devez ressembler au moins 500 images de chaque classe pour obtenir le maximum de précision possible.  

Le processus d’entrainement généré un fichier JSON qui fait une correspondance entre les types d’objets dans votre base d’images et créé des modèles.
Vous ferez le choix du modèle avec la précision la plus élevée et qui puisse faire la prédiction en utilisant le modèle et le fichier JSON généré. 

Puisse la tâche d’apprentissage est gourmande en ressource, nous recommandons fortement de la faire à l’aide d’un ordinateur équipé d’un GPU NVIDIA et ayant le version GPU de Tensorflow installée. Faire l’apprentissage sur un CPU va demander beaucoup d’heures et de jours. Avec un système informatique équipé d’un GPU NVIDIA cela ne devrait prendre que quelques heures. Vous pouvez utiliser Google Colab pour cette expérience, puisqu’il est équipé d’un GPU NVIDIA K80.

Pour entrainer votre modèle de prédiction, vous devez préparer les images que vous voulez utiliser pour entrainer votre modèle. Vous préparerez les images comme suit :

 

 -- Créer un dossier avec le nom que vous aimeriez donner avec votre base de données (ex: Chats) 

 -- Dans le dossier que vous avez précédemment crée, créer un dossier que vous nommerez ‘train’ 
 
 -- A cote du dossier train, créer un autre dossier et nommez le ‘test’ 
 
 -- Dans le dossier ‘train’, créez un dossier pour chaque type d’objets que vous aimeriez que votre modèle reconnaisse et nomme le dossier selon la classe à prédire (ex : chien, chat, écureuil, serpents) 
 
 -- Dans chaque dossier présent dans votre dossier ‘train’, mettez-y les images de chaque objet ou classe. Ces images seront utilisées pour l’apprentissage de votre modèle.
 
 -- pour générer un modèle qui puisse être viable pour des applications robustes, Je vous recommande d’avoir au moins 500 images ou de plus par objets. 1000 images per objets serait mieux.  
 
 -- Dans le dossier ‘Test’, créer des dossiers et nommez les selon les noms que vous avez utilisé pour le dossier ‘Train’. Mettez environ 100 à 200 images correspondantes dans chaque dossier. Ces images seront celle utilisées pour tester le modèle après l’avoir entrainé.
 
 -- Une fois que vous avez fait cela, la structure des dossiers de votre base d’images devrait être comme suit::

    animaux//train//chien//chien-train-images
    animaux//train//chat// chat -train-images
    animaux//train//lion // lion -train-images
    animaux//train//serpent// serpent -train-images

    animaux//test//chien //chien-test-images
    animaux//test//chat // chat -test-images
    animaux//test//lion// lion -test-images
    animaux//test//serpent // serpent -test-images



Une fois que votre base de données est prête, vous pouvez créer une instance de la classe **ModelTraining**. Retrouver un exemple ci-dessous :: 

    from imageai.Prediction.Custom import ModelTraining

    model_trainer = ModelTraining()

Une fois que vous avez créé l’instance ci-dessous, vous pouvez utiliser les fonctions ci-dessous pour commencer le processus d’entrainement. 


* **.setModelTypeAsSqueezeNet()** , Cette fonction établit comme type de modèle pour votre instance d’entrainement le modèle **SqueezeNet**, ceci  veut dire que l’algorithme **SqueezeNet** sera utilisé pour entrainer votre modèle. Trouver un exemple de code ci-dessous ::  

    model_trainer.setModelTypeAsSqueezeNet()


* **.setModelTypeAsResNet()** , Cette fonction établit comme type de modèle pour votre instance d’entrainement le modèle **ResNet**, ceci  veut dire que l’algorithme **ResNet** sera utilisé pour entrainer votre modèle.  Trouver un exemple de code ci-dessous :: 

    model_trainer.setModelTypeAsResNet()


* **.setModelTypeAsInceptionV3()** , Cette fonction établit comme type de modèle pour votre instance d’entrainement le modèle ** InceptionV3**, ceci  veut dire que l’algorithme ** InceptionV3** sera utilisé pour entrainer votre modèle. Trouver un exemple de code ci-dessous :: 

    model_trainer.setModelTypeAsInceptionV3()


* **.setModelTypeAsDenseNet()** , Cette fonction établit comme type de modèle pour votre instance d’entrainement le modèle **DenseNet**, ceci  veut dire que l’algorithme **DenseNet** sera utilisé pour entrainer votre modèle. Trouver un exemple de code ci-dessous ::  

    model_trainer.setModelTypeAsDenseNet()

* **.setDataDirectory()** ,  Cette fonction prend en argument une chaine de caractère qui doit être le chemin vers le dossier qui contient les sous-dossiers **test** et **train** qui contiennent votre base d’images. Retrouver un exemple d’utilisation de la fonction, et de ses paramètres ci-dessous ::

    prediction.setDataDirectory("C:/Users/Moses/Documents/Moses/AI/Custom Datasets/animaux")

 -- *parametre* **data_directory** (obligatoire) : Il s’agit du chemin vers le dossier qui contient votre base d’images. 

* **.trainModel()** , Il s’agit de la fonction qui commence le processus d’entrainement.  Une fois commencé, il créera un fichier JSON dans le dossier **dataset/json** (ex **animaux/json**) qui contient la correspondance de chaque classe dans la base d’images. Le fichier JSON sera utilisé pendant la détection personnalisée pour produire les résultats. Trouvez un exemple de code ci-dessous ::

    model_trainer.trainModel(num_objects=4, num_experiments=100, enhance_data=True, batch_size=32, show_network_summary=True)


 -- *paramètre* **num_objects** (obligatoire) : Ceci fait référence au nombre de différentes classes dans votre base d’images.
 
 -- *paramètre* **num_experiments** (obligatoire) : Il représente le nombre de fois que l’algorithme sera entrainé sur la base d’images. La précision de votre entrainement augmente avec le nombre d’itérations ou d’entrainement. Cependant la précision atteint son maximum avec un certain nombre d’itération et nombre dépend de la taille et de la nature de base de données.
 
 -- *paramètre* **enhance_data** (optionnel) : Ce paramètre est utilisé pour transformer votre base d’images en générant plus d’échantillons pour la phase d’entrainement. Par défaut sa valeur est ‘False’. Néanmoins, il est important de lui donner la valeur ‘True’ lorsque votre base d’images contient moins de 1000 images par classe.

 -- *paramètre* **batch_size** (optionnel) : Pendant la phase d’entrainement, L’algorithme est entrainé sur un ensemble d’images en parallèle. A cause de cela, la valeur par défaut est mise à 32. Vous pouvez accroitre ou décroitre cette valeur selon votre connaissance du système que vous utilisez pour l’apprentissage. Si vous envisagez de changer cette valeur, vous devrez utiliser des multiples de 8 pour optimiser le processus d’apprentissage.   

 -- *paramètre* **show_network_summary** (optionnel) : Lorsque ce paramètre a la valeur ‘True’, il affiche la structure de l’algorithme que vous utilisez pour l’apprentissage sur vos images dans une petite console avant de commencer l’apprentissage. Sa valeur par défaut est ‘False’. 
 
 -- *paramètre* **initial_learning_rate** (optionnel) : Ce paramètre a une haute valeur technique. Il détermine et contrôle le comportement de votre apprentissage, ce qui est critique pour la précision à réaliser. Vous pouvez changer la valeur de ce paramètre si vous avez une pleine compréhension de sa fonctionnalité.  

  -- *training_image_size* **initial_learning_rate** (optionnel) : Il représente la taille que vos images prendront pendant le processus d’apprentissage, peu importe leur taille d’origine. La valeur par défaut est de 224 et elle ne doit pas aller en dessous de 100. Augmenter sa valeur permettra de gagner en précision mais augmentera aussi le temps d’apprentissage et vice-versa.  



**Exemple de code pour un model apprentissage personnalise**

Trouvez ci-dessous un exemple de code lors de l’apprentissage d’un modèle personnalisé sur votre base d’images :: 

    from imageai.Prediction.Custom import ModelTraining

    model_trainer = ModelTraining()
    model_trainer.setModelTypeAsResNet()
    model_trainer.setDataDirectory(r"C:/Users/Moses/Documents/Moses/AI/Custom Datasets/animaux")
    model_trainer.trainModel(num_objects=10, num_experiments=100, enhance_data=True, batch_size=32, show_network_summary=True)


Ci-dessous est un aperçu de résultat lorsque l’apprentissage commence ::

    Epoch 1/100
    1/25 [>.............................] - ETA: 52s - loss: 2.3026 - acc: 0.2500
    2/25 [=>............................] - ETA: 41s - loss: 2.3027 - acc: 0.1250
    3/25 [==>...........................] - ETA: 37s - loss: 2.2961 - acc: 0.1667
    4/25 [===>..........................] - ETA: 36s - loss: 2.2980 - acc: 0.1250
    5/25 [=====>........................] - ETA: 33s - loss: 2.3178 - acc: 0.1000
    6/25 [======>.......................] - ETA: 31s - loss: 2.3214 - acc: 0.0833
    7/25 [=======>......................] - ETA: 30s - loss: 2.3202 - acc: 0.0714
    8/25 [========>.....................] - ETA: 29s - loss: 2.3207 - acc: 0.0625
    9/25 [=========>....................] - ETA: 27s - loss: 2.3191 - acc: 0.0556
    10/25 [===========>..................] - ETA: 25s - loss: 2.3167 - acc: 0.0750
    11/25 [============>.................] - ETA: 23s - loss: 2.3162 - acc: 0.0682
    12/25 [=============>................] - ETA: 21s - loss: 2.3143 - acc: 0.0833
    13/25 [==============>...............] - ETA: 20s - loss: 2.3135 - acc: 0.0769
    14/25 [===============>..............] - ETA: 18s - loss: 2.3132 - acc: 0.0714
    15/25 [=================>............] - ETA: 16s - loss: 2.3128 - acc: 0.0667
    16/25 [==================>...........] - ETA: 15s - loss: 2.3121 - acc: 0.0781
    17/25 [===================>..........] - ETA: 13s - loss: 2.3116 - acc: 0.0735
    18/25 [====================>.........] - ETA: 12s - loss: 2.3114 - acc: 0.0694
    19/25 [=====================>........] - ETA: 10s - loss: 2.3112 - acc: 0.0658
    20/25 [=======================>......] - ETA: 8s - loss: 2.3109 - acc: 0.0625
    21/25 [========================>.....] - ETA: 7s - loss: 2.3107 - acc: 0.0595
    22/25 [=========================>....] - ETA: 5s - loss: 2.3104 - acc: 0.0568
    23/25 [==========================>...] - ETA: 3s - loss: 2.3101 - acc: 0.0543
    24/25 [===========================>..] - ETA: 1s - loss: 2.3097 - acc: 0.0625Epoch 00000: saving model to C:\Users\Moses\Documents\Moses\W7\AI\Custom Datasets\IDENPROF\idenprof-small-test\idenprof\models\model_ex-000_acc-0.100000.h5

    25/25 [==============================] - 51s - loss: 2.3095 - acc: 0.0600 - val_loss: 2.3026 - val_acc: 0.1000

Expliquons les détails ci-dessus :

1. La ligne Epoch 1/100 signifie que le réseau fait le premier apprentissage sur les 100 voulus.  0

2. La ligne  1/25 [>.............................] - ETA: 52s - loss: 2.3026 - acc: 0.2500 représente le nombre de groupe qui ont été entrainé dans la présente phase d’apprentissage.  

3. La ligne  Epoch 00000: sauvegarde le modèle à l’emplacement  C:\Users\User\PycharmProjects\ImageAITest\pets\models\modelex-000acc-0.100000.h5 à la fin de la phase d’apprentissage présente.  ex_000 représente le niveau d’apprentissage tandis que acc0.100000 et  valacc: 0.1000  représente la précision du modèle sur l’ensemble d’images ‘Test’ après le présent apprentissage(La valeur maximale de la précision est de 1.0). Ce résultat vous permet de connaitre le meilleur modèle a utiliser pour la détection sur vos images.

Une fois que vous avez terminé l’apprentissage de votre modèle termine, vous pouvez utiliser la classe **CustomImagePrediction**  décrite si dessous pour la détection avec votre modèle. 




**======= imageai.Prediction.Custom.CustomImagePrediction =======**


Cette classe peut être considérée comme une réplique de **imageai.Prediction.ImagePrediction** puis qu’elle a les même fonctions, paramètres et résultats. La seule différence est que cette classe fonctionne avec votre modèle personnalisé. Vous aurez besoin de spécifier le chemin du fichier JSON généré pendant la phase d’apprentissage et aussi de spécifier le nombre de classe dans votre base d’image lors du chargement du modèle. Ci-dessous est un exemple de création d’instance de la classe ::


    from imageai.Prediction.Custom import CustomImagePrediction
    
    prediction = CustomImagePrediction()

Une fois que vous avez créé l’instance, vous pouvez utiliser les fonctions ci-dessous pour configurer les propriétés de votre instance et commencer le processus de détection et reconnaissance sur des images. 


* **.setModelTypeAsSqueezeNet()** , Cette fonction établit comme type de modèle pour votre instance de reconnaissance et détection, le modèle **SqueezeNet**, ceci  veut dire que l’algorithme **SqueezeNet** généré pendant votre phase d’apprentissage personnalisée sera utilisé pour la tache de prédiction sur vos images. Trouver un exemple de code ci-dessous ::  


    prediction.setModelTypeAsSqueezeNet()


* **. setModelTypeAsResNet()** , Cette fonction établit comme type de modèle pour votre instance de reconnaissance et détection, le modèle ** ResNet**, ceci  veut dire que l’algorithme **ResNet** généré pendant votre phase d’apprentissage personnalisée sera utilisé pour la tache de prédiction sur vos images. Trouver un exemple de code ci-dessous ::  


    prediction.setModelTypeAsResNet()

* **. setModelTypeAsInceptionV3 ()** , Cette fonction établit comme type de modèle pour votre instance de reconnaissance et détection, le modèle **InceptionV3**, ceci  veut dire que l’algorithme **InceptionV3** généré pendant votre phase d’apprentissage personnalisée sera utilisé pour la tache de prédiction sur vos images. Trouver un exemple de code ci-dessous ::  


    prediction.setModelTypeAsInceptionV3()


* **. setModelTypeAsDenseNet()** , Cette fonction établit comme type de modèle pour votre instance de reconnaissance et détection, le modèle ** DenseNet**, ceci  veut dire que l’algorithme **DenseNet** généré pendant votre phase d’apprentissage personnalisée sera utilisé pour la tache de prédiction sur vos images. Trouver un exemple de code ci-dessous ::  



    prediction.setModelTypeAsDenseNet()


* **.setModelPath()** , cette fonction accepte une chaine de caractère qui doit être le chemin vers le fichier modèle généré pendant votre phase d’apprentissage et doit correspondre au type de modèle que vous avez défini pour votre instance de reconnaissance d’images. Trouver un exemple de code, et de paramètres de fonction ci-dessous ::


    prediction.setModelPath("resnet_model_ex-020_acc-0.651714.h5")

 -- *paramètre* **model_path** (requis) : Il s’agit du chemin vers le fichier modèle téléchargé.  


* **.setJsonPath()** , cette fonction prend en argument une chaine de caractère qui représente le chemin vers le fichier JSON généré pendant la phase d’apprentissage du modèle personnalisé. Trouvez ci-dessous un exemple de code et de paramètres de la fonction ::

 
    prediction.setJsonPath("model_class.json")

 -- *paramètre* **model_path** (requis) : Il s’agit du chemin vers le fichier modèle téléchargé.  


* **.loadModel()** , Cette fonction charge le modèle à partir du chemin spécifié dans votre appel de fonction ci-dessus pour votre instance de prédiction d’images. Au paramètre **num_objects** vous devrez donner la valeur correspondant au nombre de classes dans votre base d’images. Trouvez ci-dessous un exemple de code et de paramètres de la fonction ::

    prediction.loadModel(num_objects=4)

 -- *paramètre* **num_objects** (requis) : La valeur de ce paramètre doit correspondre au nombre de classe dans votre base d’images.  


-- *paramètre* **prediction_speed** (optionnel) : Ce paramètre vous permet de réduire le temps de prédiction sur une image d’environ 80% ce qui conduit à une légère réduction de la précision. Ce paramètre prend des valeurs de type chaine de caractère. Les valeurs disponibles sont : 
"normal", "fast", "faster" et "fastest". La valeur par défaut est "normal"


* **.predictImage()** , C’est la fonction qui accomplit à proprement parler la prédiction sur une image. Elle peut être appeler plusieurs fois sur plusieurs images une fois que le modèle a été charge dans l’instance de prédiction. Trouver ci-dessous un exemple de code, de paramètres de fonction ainsi que les valeurs renvoyées ::

    predictions, probabilities = prediction.predictImage("image1.jpg", result_count=2)

 -- *paramètre* **image_input** (requis) : Il fait référence au chemin vers votre image, le tableau de type Numpy de votre image ou le flux de votre image, dépendamment de type de valeur d’entrée spécifiée. 


 -- *paramètre* **result_count** (optionnel) : il fait référence au nombre possible de prédiction qui peuvent être donne. Ce paramètre a pour valeur par défaut 5.   


 -- *paramètre* **input_type** (optionnel) :  Il fait référence au type de la valeur d’entrée que vous passez au paramètre **image_input**. Il est de type ‘file’ par défaut et accepte ‘stream ’et ‘array ’aussi.

 -- *valeur retournée* **prediction_results** (une liste python) : 
La première valeur retournée par la fonction **predictImage** est une liste qui contient tous les résultats possibles de prédiction. Les résultats sont ordonnés en ordre descendant de pourcentage de probabilité.

 -- *valeur retournée* **prediction_probabilities** (une liste python) : 
La première valeur retournée par la fonction **predictImage** est une liste qui contient les pourcentages de probabilité correspondantes a toutes les prédictions possibles dans **prediction_results**


* **.predictMultipleImages()** , Cette fonction peut être utilisée pour effectuer la tache de prédiction sur 2 ou plusieurs images en une seule fois. Trouvez ci-dessous un exemple de code, paramètres de fonction et de valeurs renvoyées ::

 
    results_array = multiple_prediction.predictMultipleImages(all_images_array, result_count_per_image=2)

    for each_result in results_array:
        predictions, percentage_probabilities = each_result["predictions"], each_result["percentage_probabilities"]
        for index in range(len(predictions)):
            print(predictions[index] , " : " , percentage_probabilities[index])
        print("-----------------------")

  -- *paramètre* **sent_images_array** (requis) : Il fait référence a une liste qui contient le chemin vers vos fichiers image, vos tableau Numpy de vos images ou vos fichiers de flux d’images, dépendamment du type de valeur d’entrée spécifiée.   

  -- *paramètre* **result_count_per_image** (optionnel) : Il fait référence au nombre possible de prédictions qui doivent être données pour chaque image. Ce paramètre a pour valeur par défaut 2. 


-- *paramètre* **input_type** (optionnel) :  Il fait référence au format de vos images ont dans la liste du paramètre **sent_images_array**. Il est de type ‘file’ par défaut et accepte ‘stream ’et ‘array ’aussi. 


  -- *valeur retournée* **output_array** (une liste python) : 
La valeur retournée par la fonction **predictMultipleImages** est une liste qui contient des dictionnaires. Chaque dictionnaire correspond à une image contenue dans le tableau envoyée à **sent_images_array**. 
Chaque dictionnaire a une propriete "prediction_results" qui est une liste de tous les resultats de prediction pour l’image a cet indice aussi bien que la probabilite de prediction "prediction_probabilities" qui est une liste de pourcentage de probabilite correspondant a chaque resultat.

**Exemple de code**

Trouvez ci-dessous un échantillon de code pour la prédiction personnalisé ::

    from imageai.Prediction.Custom import CustomImagePrediction
    import os

    execution_path = os.getcwd()

    prediction = CustomImagePrediction()
    prediction.setModelTypeAsResNet()
    prediction.setModelPath(os.path.join(execution_path, "resnet_model_ex-020_acc-0.651714.h5"))
    prediction.setJsonPath(os.path.join(execution_path, "model_class.json"))
    prediction.loadModel(num_objects=4)

    predictions, probabilities = prediction.predictImage(os.path.join(execution_path, "4.jpg"), result_count=5)

    for eachPrediction, eachProbability in zip(predictions, probabilities):
        print(eachPrediction , " : " , eachProbability)




.. toctree::
   :maxdepth: 2
   :caption: Contents:
