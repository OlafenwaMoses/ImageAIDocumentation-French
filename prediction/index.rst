.. ImageAI documentation master file, created by
   sphinx-quickstart on Tue Jun 12 06:13:09 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Classes de prédiction
==================
**ImageAI** fournit un ensemble de classes puissantes et faciles à utiliser pour accomplir les tâches de *reconnaissance sur les images*.
Vous pouvez pourrez accomplir toutes ces taches de pointe de vision assistée par ordinateur avec du code python allant de 5 à 12 lignes de code. 
Une fois que le python installe, d’autres bibliothèques et **ImageAI** installes dans votre ordinateur, il n’y a aucune limite aux applications incroyables que vous pouvez créer. Trouvez ci-dessous les classes et leur fonction respective rendues disponibles pour votre utilisation.
Ces classes peuvent être intégrées dans n’importe quelle programme python traditionnel que vous développez, que cela soit un site internet, une application Windows/Linux/MacOS ou un système qui supporte ou fait partir d’un réseau local. 


**======= imageai.Prediction.ImagePrediction =======**

La classe **ImagePrediction** vous fournit des fonctions pour utiliser les modèles de reconnaissance d’images les plus pointus tel **SqueezeNet**, **ResNet**, **InceptionV3** et **DenseNet** qui ont été **pré-entraines** sur la base de données **ImageNet-1000**.  Ceci pour dire que vous pouvez utiliser ces classes pour détecter et reconnaitre plus de 1000 différents objets sur n’importe quelle image ou ensemble d’images. Pour initialiser la classe dans votre code, vous allez créer une instance dans votre code comme suit ::
    
    from imageai.Prediction import ImagePrediction
    prediction = ImagePrediction()


Nous avons fourni les modèles pré-entraines de reconnaissance d’images des algorithmes suivants **SqueezeNet**, **ResNet**, **InceptionV3** et **DenseNet** que vous allez utiliser dans la classe **ImagePrediction** pour faire la reconnaissance sur les images. Trouvez ci-dessous le lien pour télécharger les modèles. Vous pouvez télécharger le modèle que vous voulez utiliser. 

`Telechargez le modele SqueezeNet <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

`Téléchargez le modèle ResNet <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

` Téléchargez le modèle InceptionV3 <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

` Téléchargez le modèle DenseNet <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

Après avoir créé une nouvelle instance de la classe **ImagePrediction**, Vous pouvez utiliser les fonctions ci-dessous pour définir les valeurs des propriétés et commencer la reconnaissance.   

* **.setModelTypeAsSqueezeNet()** , cette fonction établit comme modèle pour votre instance de reconnaissance d’image que vous avez créé, le modèle **SqueezeNet** ; ce qui veut dire que vous accomplirez vos taches de prédiction en utilisant les modèles pré-entrainés de **SqueezeNet** que vous avez téléchargé avec le lien ci-dessus. Trouvez le code ci-dessous ::


    prediction.setModelTypeAsSqueezeNet()


* **.setModelTypeAsResNet()** , cette fonction établit comme modèle pour votre instance de reconnaissance d’image que vous avez créé, le modèle **ResNet** ; ce qui veut dire que vous accomplirez vos taches de prédiction en utilisant les modèles pré-entrainés de **ResNet** que vous avez téléchargé avec le lien ci-dessus. Trouvez le code ci-dessous ::


    prediction.setModelTypeAsResNet()


* **.setModelTypeAsInceptionV3()** , cette fonction établit comme modèle pour votre instance de reconnaissance d’image que vous avez créé, le modèle **InceptionV3** ; ce qui veut dire que vous accomplirez vos taches de prédiction en utilisant les modèles pré-entrainés de **InceptionV3** que vous avez téléchargé avec le lien ci-dessus. Trouvez le code ci-dessous ::



    prediction.setModelTypeAsInceptionV3()


* **.setModelTypeAsDenseNet()** , cette fonction établit comme modèle pour votre instance de reconnaissance d’image que vous avez créé, le modèle **DenseNet** ; ce qui veut dire que vous accomplirez vos taches de prédiction en utilisant les modèles pré-entrainés de **DenseNet** que vous avez téléchargé avec le lien ci-dessus. Trouvez le code ci-dessous ::

    prediction.setModelTypeAsDenseNet()


* **.setModelPath()** , cette fonction accepte une chaine de caractère qui doit être le chemin vers le fichier modèle que vous avez téléchargé, il doit correspondre au type de modèle que vous avez choisi pour votre instance de prédiction/détection sur image. Trouvez un exemple de code, et paramètres de fonction ci-dessous ::
    prediction.setModelPath("resnet50_weights_tf_dim_ordering_tf_kernels.h5")

 -- *paramètre* **model_path** (requis) : Il s’agit du chemin vers votre fichier modèle téléchargé.  

* **.loadModel()** , Cette fonction charge le modèle à partir du chemin que vous avez spécifié dans l’appel de fonction ci-dessus dans votre instance de prédiction. Trouvez un exemple de code ci-dessous ::

    prediction.loadModel()

 -- *paramètre* **prediction_speed** (optionnel) : Ce paramètre vous permet de réduire jusqu’à 80% le temps qu’il faut pour la tache de prédiction sur une image, ce qui conduit à une légère réduction de la précision. Ce paramètre accepte les chaines de caractères. Les valeurs disponibles sont "normal", "fast", "faster" et "fastest". La valeur par défaut est "normal". 


* **.predictImage()** , C’est la fonction qui effectue la tache de prédiction a proprement parle sur une image.  Elle peut être appelée plusieurs fois sur plusieurs images une fois que le modèle a été charge dans l’instance de prédiction. Trouvez un exemple de code, et paramètres de fonction ci-dessous ::
     
    predictions, probabilities = prediction.predictImage("image1.jpg", result_count=10)


 -- *paramètre* **image_input** (requis) : Il fait référence au chemin vers votre fichier images, tableau Numpy de votre image ou le fichier flux de votre image, dépendamment du type que vous avez choisi. 


 -- *paramètre* **result_count** (optionnel) : Il fait référence au nombre possible de prédictions qui doivent être retourne. Le paramètre a une valeur par défaut de 5. 


 -- *paramètre* **input_type** (optionnel) : Il fait référence au type de la valeur d’entrée dans le paramètre **image_input**. Il est ‘file’ par défaut et accepte ‘array’ et ‘stream’ aussi.  


 -- *valeur retournée* **prediction_results** (une liste python) : La première valeur renvoyée par la fonction **predictImage** est une liste qui contient tous les résultats possibles de prédiction. Les résultats sont arrangés dans l’ordre descendant de probabilité de pourcentage. 

 -- *valeur retournée* **prediction_probabilities** (une liste python) :
La seconde valeur renvoyée par la fonction **predictImage** est une liste qui contient les pourcentages de probabilité correspondant à toutes les prédictions possibles dans **prediction_results**


* **.predictMultipleImages()** , Cette fonction pour accomplir la prédictions sur 2 ou plusieurs images à la fois. Trouvez un exemple de code, et paramètres de fonction ci-dessous ::
 


    results_array = multiple_prediction.predictMultipleImages(all_images_array, result_count_per_image=5)

    for each_result in results_array:
        predictions, percentage_probabilities = each_result["predictions"], each_result["percentage_probabilities"]
        for index in range(len(predictions)):
            print(predictions[index] , " : " , percentage_probabilities[index])
        print("-----------------------")

  -- *paramètre* **sent_images_array** (requis) : Il fait référence a une liste qui contient le chemin vers les fichiers images, les tableaux Numpy de vos images ou les fichiers de flux de vos images, dépendamment de type spécifie pour la valeur d’entrée. 


  -- *paramètre* **result_count_per_image** (optionnel) : Il fait référence au nombre de possible de prédictions renvoyées pour chaque image. Ce paramètre a pour valeur par défaut 2. 


  -- *paramètre* **input_type** (optionnel) : Il fait référence au format dans lequel vos images sont représentées dans la liste contenu dans le paramètre **sent_images_array**. Il est par défaut ‘file’ et accepte aussi ‘array’ et ‘stream’. 


  -- *valeur retournée* **output_array** (une liste python) : La valeur retournée par la fonction **predictMultipleImages** est une liste qui contient des dictionnaires. Chaque dictionnaire correspond à une image contenue dans le tableau transmis a **sent_images_array**. Chaque dictionnaire a une propriété "prediction_results" qui est la liste de tous les résultats de prédictions sur l’image a cet indice ainsi que la ‘prediction_probabilities’ qui est la liste correspondant au pourcentage de probabilité de chaque résultat. 


**Exemple de code**

Trouver ci-dessous un échantillon de code pour la prédiction sur une image :: 

    from imageai.Prediction import ImagePrediction
    import os

    execution_path = os.getcwd()

    prediction = ImagePrediction()
    prediction.setModelTypeAsResNet()
    prediction.setModelPath(os.path.join(execution_path, "resnet50_weights_tf_dim_ordering_tf_kernels.h5"))
    prediction.loadModel()

    predictions, probabilities = prediction.predictImage(os.path.join(execution_path, "image1.jpg"), result_count=10)
    for eachPrediction, eachProbability in zip(predictions, probabilities):
        print(eachPrediction , " : " , eachProbability)

Trouvez ci-dessous un échantillon de code pour la détection/prédiction sur plusieurs images ::

    from imageai.Prediction import ImagePrediction
    import os

    execution_path = os.getcwd()

    multiple_prediction = ImagePrediction()
    multiple_prediction.setModelTypeAsResNet()
    multiple_prediction.setModelPath(os.path.join(execution_path, "resnet50_weights_tf_dim_ordering_tf_kernels.h5"))
    multiple_prediction.loadModel()

    all_images_array = []

    all_files = os.listdir(execution_path)
    for each_file in all_files:
        if(each_file.endswith(".jpg") or each_file.endswith(".png")):
            all_images_array.append(each_file)

    results_array = multiple_prediction.predictMultipleImages(all_images_array, result_count_per_image=5)

    for each_result in results_array:
        predictions, percentage_probabilities = each_result["predictions"], each_result["percentage_probabilities"]
        for index in range(len(predictions)):
            print(predictions[index] , " : " , percentage_probabilities[index])
        print("-----------------------")








.. toctree::
   :maxdepth: 2
   :caption: Contents:

   


