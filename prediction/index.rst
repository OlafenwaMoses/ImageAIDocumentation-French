.. ImageAI documentation master file, created by
   sphinx-quickstart on Tue Jun 12 06:13:09 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Classes de prŽdiction
==================
**ImageAI** fournit un ensemble de classes puissantes et faciles ˆ utiliser pour accomplir les t‰ches de *reconnaissance sur les images*.
Vous pouvez pourrez accomplir toutes ces taches de pointe de vision assistŽe par ordinateur avec du code python allant de 5 ˆ 12 lignes de code. 
Une fois que le python installe, dÕautres bibliothques et **ImageAI** installes dans votre ordinateur, il nÕy a aucune limite aux applications incroyables que vous pouvez crŽer. Trouvez ci-dessous les classes et leur fonction respective rendues disponibles pour votre utilisation.
Ces classes peuvent tre intŽgrŽes dans nÕimporte quelle programme python traditionnel que vous dŽveloppez, que cela soit un site internet, une application Windows/Linux/MacOS ou un systme qui supporte ou fait partir dÕun rŽseau local. 


**======= imageai.Prediction.ImagePrediction =======**

La classe **ImagePrediction** vous fournit des fonctions pour utiliser les modles de reconnaissance dÕimages les plus pointus tel **SqueezeNet**, **ResNet**, **InceptionV3** et **DenseNet** qui ont ŽtŽ **prŽ-entraines** sur la base de donnŽes **ImageNet-1000**.  Ceci pour dire que vous pouvez utiliser ces classes pour dŽtecter et reconnaitre plus de 1000 diffŽrents objets sur nÕimporte quelle image ou ensemble dÕimages. Pour initialiser la classe dans votre code, vous allez crŽer une instance dans votre code comme suitÊ::
    
    from imageai.Prediction import ImagePrediction
    prediction = ImagePrediction()


Nous avons fourni les modles prŽ-entraines de reconnaissance dÕimages des algorithmes suivants **SqueezeNet**, **ResNet**, **InceptionV3** et **DenseNet** que vous allez utiliser dans la classe **ImagePrediction** pour faire la reconnaissance sur les images. Trouvez ci-dessous le lien pour tŽlŽcharger les modles. Vous pouvez tŽlŽcharger le modle que vous voulez utiliser. 

`Telechargez le modele SqueezeNet <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

`TŽlŽchargez le modle ResNet <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

` TŽlŽchargez le modle InceptionV3 <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

` TŽlŽchargez le modle DenseNet <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

Aprs avoir crŽŽ une nouvelle instance de la classe **ImagePrediction**, Vous pouvez utiliser les fonctions ci-dessous pour dŽfinir les valeurs des propriŽtŽs et commencer la reconnaissance.   

* **.setModelTypeAsSqueezeNet()** , cette fonction Žtablit comme modle pour votre instance de reconnaissance dÕimage que vous avez crŽŽ, le modle **SqueezeNet**Ê; ce qui veut dire que vous accomplirez vos taches de prŽdiction en utilisant les modles prŽ-entrainŽs de **SqueezeNet** que vous avez tŽlŽchargŽ avec le lien ci-dessus. Trouvez le code ci-dessousÊ::


    prediction.setModelTypeAsSqueezeNet()


* **.setModelTypeAsResNet()** , cette fonction Žtablit comme modle pour votre instance de reconnaissance dÕimage que vous avez crŽŽ, le modle **ResNet**Ê; ce qui veut dire que vous accomplirez vos taches de prŽdiction en utilisant les modles prŽ-entrainŽs de **ResNet** que vous avez tŽlŽchargŽ avec le lien ci-dessus. Trouvez le code ci-dessousÊ::


    prediction.setModelTypeAsResNet()


* **.setModelTypeAsInceptionV3()** , cette fonction Žtablit comme modle pour votre instance de reconnaissance dÕimage que vous avez crŽŽ, le modle **InceptionV3**Ê; ce qui veut dire que vous accomplirez vos taches de prŽdiction en utilisant les modles prŽ-entrainŽs de **InceptionV3** que vous avez tŽlŽchargŽ avec le lien ci-dessus. Trouvez le code ci-dessousÊ::



    prediction.setModelTypeAsInceptionV3()


* **.setModelTypeAsDenseNet()** , cette fonction Žtablit comme modle pour votre instance de reconnaissance dÕimage que vous avez crŽŽ, le modle **DenseNet**Ê; ce qui veut dire que vous accomplirez vos taches de prŽdiction en utilisant les modles prŽ-entrainŽs de **DenseNet** que vous avez tŽlŽchargŽ avec le lien ci-dessus. Trouvez le code ci-dessousÊ::

    prediction.setModelTypeAsDenseNet()


* **.setModelPath()** , cette fonction accepte une chaine de caractre qui doit tre le chemin vers le fichier modle que vous avez tŽlŽchargŽ, il doit correspondre au type de modle que vous avez choisi pour votre instance de prŽdiction/dŽtection sur image. Trouvez un exemple de code, et paramtres de fonction ci-dessousÊ::
    prediction.setModelPath("resnet50_weights_tf_dim_ordering_tf_kernels.h5")

 -- *paramtre* **model_path** (requis) : Il sÕagit du chemin vers votre fichier modle tŽlŽchargŽ.  

* **.loadModel()** , Cette fonction charge le modle ˆ partir du chemin que vous avez spŽcifiŽ dans lÕappel de fonction ci-dessus dans votre instance de prŽdiction. Trouvez un exemple de code ci-dessousÊ::

    prediction.loadModel()

 -- *paramtre* **prediction_speed** (optionnel) : Ce paramtre vous permet de rŽduire jusquÕˆ 80% le temps quÕil faut pour la tache de prŽdiction sur une image, ce qui conduit ˆ une lŽgre rŽduction de la prŽcision. Ce paramtre accepte les chaines de caractres. Les valeurs disponibles sont "normal", "fast", "faster" et "fastest". La valeur par dŽfaut est "normal". 


* **.predictImage()** , CÕest la fonction qui effectue la tache de prŽdiction a proprement parle sur une image.  Elle peut tre appelŽe plusieurs fois sur plusieurs images une fois que le modle a ŽtŽ charge dans lÕinstance de prŽdiction. Trouvez un exemple de code, et paramtres de fonction ci-dessousÊ::
     
    predictions, probabilities = prediction.predictImage("image1.jpg", result_count=10)


 -- *paramtre* **image_input** (requis) : Il fait rŽfŽrence au chemin vers votre fichier images, tableau Numpy de votre image ou le fichier flux de votre image, dŽpendamment du type que vous avez choisi. 


 -- *paramtre* **result_count** (optionnel) : Il fait rŽfŽrence au nombre possible de prŽdictions qui doivent tre retourne. Le paramtre a une valeur par dŽfaut de 5. 


 -- *paramtre* **input_type** (optionnel) : Il fait rŽfŽrence au type de la valeur dÕentrŽe dans le paramtre **image_input**. Il est ÔfileÕ par dŽfaut et accepte ÔarrayÕ et ÔstreamÕ aussi. Ê


 -- *valeur retournŽe* **prediction_results** (une liste python) : La premire valeur renvoyŽe par la fonction **predictImage** est une liste qui contient tous les rŽsultats possibles de prŽdiction. Les rŽsultats sont arrangŽs dans lÕordre descendant de probabilitŽ de pourcentage. 

 -- *valeur retournŽe* **prediction_probabilities** (une liste python) :
La seconde valeur renvoyŽe par la fonction **predictImage** est une liste qui contient les pourcentages de probabilitŽ correspondant ˆ toutes les prŽdictions possibles dans **prediction_results**


* **.predictMultipleImages()** , Cette fonction pour accomplir la prŽdictions sur 2 ou plusieurs images ˆ la fois. Trouvez un exemple de code, et paramtres de fonction ci-dessousÊ::
 


    results_array = multiple_prediction.predictMultipleImages(all_images_array, result_count_per_image=5)

    for each_result in results_array:
        predictions, percentage_probabilities = each_result["predictions"], each_result["percentage_probabilities"]
        for index in range(len(predictions)):
            print(predictions[index] , " : " , percentage_probabilities[index])
        print("-----------------------")

  -- *paramtre* **sent_images_array** (requis) : Il fait rŽfŽrence a une liste qui contient le chemin vers les fichiers images, les tableaux Numpy de vos images ou les fichiers de flux de vos images, dŽpendamment de type spŽcifie pour la valeur dÕentrŽe. 


  -- *paramtre* **result_count_per_image** (optionnel) : Il fait rŽfŽrence au nombre de possible de prŽdictions renvoyŽes pour chaque image. Ce paramtre a pour valeur par dŽfaut 2. 


  -- *paramtre* **input_type** (optionnel) : Il fait rŽfŽrence au format dans lequel vos images sont reprŽsentŽes dans la liste contenu dans le paramtre **sent_images_array**. Il est par dŽfaut ÔfileÕ et accepte aussi ÔarrayÕ et ÔstreamÕ. 


  -- *valeur retournŽe* **output_array** (une liste python) : La valeur retournŽe par la fonction **predictMultipleImages** est une liste qui contient des dictionnaires. Chaque dictionnaire correspond ˆ une image contenue dans le tableau transmis a **sent_images_array**. Chaque dictionnaire a une propriŽtŽ "prediction_results" qui est la liste de tous les rŽsultats de prŽdictions sur lÕimage a cet indice ainsi que la Ôprediction_probabilitiesÕ qui est la liste correspondant au pourcentage de probabilitŽ de chaque rŽsultat. 


**Exemple de code**

Trouver ci-dessous un Žchantillon de code pour la prŽdiction sur une imageÊ:: 

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

Trouvez ci-dessous un Žchantillon de code pour la dŽtection/prŽdiction sur plusieurs imagesÊ::

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

   


