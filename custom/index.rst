.. ImageAI documentation master file, created by
   sphinx-quickstart on Tue Jun 12 06:13:09 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Apprentissage personnalisŽ et prŽdiction des Classes
======================================
**ImageAI** fournit des classes puissante et nŽanmoins facile ˆ utiliser pour entrainer des algorithmes a la pointe de la technologies tel que **SqueezeNet**, **ResNet** , **InceptionV3** et  **DenseNet** sur votre propre base de donnŽes avec juste  **5 lignes de code** pour gŽnŽrer votre propre modle personnalisŽ. 
Une fois que vous avez entrainŽ votre propre modle, vous pouvez utiliser la classe **CustomImagePrediction** fournit par **ImageAI** pour utiliser votre modle pour reconnaitre et faire la dŽtection sur une image ou un ensemble dÕimages. 



**======= imageai.Prediction.Custom.ModelTraining =======**



La classe **ModelTraining** vous permet dÕentrainer un des quatre algorithme dÕapprentissage profond suivant (**SqueezeNet**, **ResNet**
, **InceptionV3** et **DenseNet**) sur votre base de donnŽes dÕimages pour gŽnŽrer votre propre modle. Votre base de donnŽes dÕimages doit contenir au moins deux diffŽrentes classes/types dÕimages (chat et chien) et vous devez ressembler au moins 500 images de chaque classe pour obtenir le maximum de prŽcision possible.  

Le processus dÕentrainement gŽnŽrŽ un fichier JSON qui fait une correspondance entre les types dÕobjets dans votre base dÕimages et crŽŽ des modles.
Vous ferez le choix du modle avec la prŽcision la plus ŽlevŽe et qui puisse faire la prŽdiction en utilisant le modle et le fichier JSON gŽnŽrŽ. 

Puisse la t‰che dÕapprentissage est gourmande en ressource, nous recommandons fortement de la faire ˆ lÕaide dÕun ordinateur ŽquipŽ dÕun GPU NVIDIA et ayant le version GPU de Tensorflow installŽe. Faire lÕapprentissage sur un CPU va demander beaucoup dÕheures et de jours. Avec un systme informatique ŽquipŽ dÕun GPU NVIDIA cela ne devrait prendre que quelques heures. Vous pouvez utiliser Google Colab pour cette expŽrience, puisquÕil est ŽquipŽ dÕun GPU NVIDIA K80.

Pour entrainer votre modle de prŽdiction, vous devez prŽparer les images que vous voulez utiliser pour entrainer votre modle. Vous prŽparerez les images comme suitÊ:

 

 -- CrŽer un dossier avec le nom que vous aimeriez donner avec votre base de donnŽes (ex: Chats) 

 -- Dans le dossier que vous avez prŽcŽdemment crŽe, crŽer un dossier que vous nommerez ÔtrainÕ 
 
 -- A cote du dossier train, crŽer un autre dossier et nommez le ÔtestÕ 
 
 -- Dans le dossier ÔtrainÕ, crŽez un dossier pour chaque type dÕobjets que vous aimeriez que votre modle reconnaisse et nomme le dossier selon la classe ˆ prŽdire (exÊ: chien, chat, Žcureuil, serpents) 
 
 -- Dans chaque dossier prŽsent dans votre dossier ÔtrainÕ, mettez-y les images de chaque objet ou classe. Ces images seront utilisŽes pour lÕapprentissage de votre modle.
 
 -- pour gŽnŽrer un modle qui puisse tre viable pour des applications robustes, Je vous recommande dÕavoir au moins 500 images ou de plus par objets. 1000 images per objets serait mieux.  
 
 -- Dans le dossier ÔTestÕ, crŽer des dossiers et nommez les selon les noms que vous avez utilisŽ pour le dossier ÔTrainÕ. Mettez environ 100 ˆ 200 images correspondantes dans chaque dossier. Ces images seront celle utilisŽes pour tester le modle aprs lÕavoir entrainŽ.
 
 -- Une fois que vous avez fait cela, la structure des dossiers de votre base dÕimages devrait tre comme suit::

    animaux//train//chien//chien-train-images
    animaux//train//chat// chat -train-images
    animaux//train//lion // lion -train-images
    animaux//train//serpent// serpent -train-images

    animaux//test//chien //chien-test-images
    animaux//test//chat // chat -test-images
    animaux//test//lion// lion -test-images
    animaux//test//serpent // serpent -test-images



Une fois que votre base de donnŽes est prte, vous pouvez crŽer une instance de la classe **ModelTraining**. Retrouver un exemple ci-dessousÊ:: 

    from imageai.Prediction.Custom import ModelTraining

    model_trainer = ModelTraining()

Une fois que vous avez crŽŽ lÕinstance ci-dessous, vous pouvez utiliser les fonctions ci-dessous pour commencer le processus dÕentrainement. 


* **.setModelTypeAsSqueezeNet()** , Cette fonction Žtablit comme type de modle pour votre instance dÕentrainement le modle **SqueezeNet**, ceci  veut dire que lÕalgorithme **SqueezeNet** sera utilisŽ pour entrainer votre modle. Trouver un exemple de code ci-dessousÊ::  

    model_trainer.setModelTypeAsSqueezeNet()


* **.setModelTypeAsResNet()** , Cette fonction Žtablit comme type de modle pour votre instance dÕentrainement le modle **ResNet**, ceci  veut dire que lÕalgorithme **ResNet** sera utilisŽ pour entrainer votre modle.  Trouver un exemple de code ci-dessous :: 

    model_trainer.setModelTypeAsResNet()


* **.setModelTypeAsInceptionV3()** , Cette fonction Žtablit comme type de modle pour votre instance dÕentrainement le modle ** InceptionV3**, ceci  veut dire que lÕalgorithme ** InceptionV3** sera utilisŽ pour entrainer votre modle. Trouver un exemple de code ci-dessousÊ:: 

    model_trainer.setModelTypeAsInceptionV3()


* **.setModelTypeAsDenseNet()** , Cette fonction Žtablit comme type de modle pour votre instance dÕentrainement le modle **DenseNet**, ceci  veut dire que lÕalgorithme **DenseNet** sera utilisŽ pour entrainer votre modle. Trouver un exemple de code ci-dessousÊ::  

    model_trainer.setModelTypeAsDenseNet()

* **.setDataDirectory()** ,  Cette fonction prend en argument une chaine de caractre qui doit tre le chemin vers le dossier qui contient les sous-dossiers **test** et **train** qui contiennent votre base dÕimages. Retrouver un exemple dÕutilisation de la fonction, et de ses paramtres ci-dessous ::

    prediction.setDataDirectory("C:/Users/Moses/Documents/Moses/AI/Custom Datasets/animaux")

 -- *parametre* **data_directory** (obligatoire) : Il sÕagit du chemin vers le dossier qui contient votre base dÕimages. 

* **.trainModel()** , Il sÕagit de la fonction qui commence le processus dÕentrainement.  Une fois commencŽ, il crŽera un fichier JSON dans le dossier **dataset/json** (ex **animaux/json**) qui contient la correspondance de chaque classe dans la base dÕimages. Le fichier JSON sera utilisŽ pendant la dŽtection personnalisŽe pour produire les rŽsultats. Trouvez un exemple de code ci-dessous ::

    model_trainer.trainModel(num_objects=4, num_experiments=100, enhance_data=True, batch_size=32, show_network_summary=True)


 -- *paramtre* **num_objects** (obligatoire) : Ceci fait rŽfŽrence au nombre de diffŽrentes classes dans votre base dÕimages.
 
 -- *paramtre* **num_experiments** (obligatoire) : Il reprŽsente le nombre de fois que lÕalgorithme sera entrainŽ sur la base dÕimages. La prŽcision de votre entrainement augmente avec le nombre dÕitŽrations ou dÕentrainement. Cependant la prŽcision atteint son maximum avec un certain nombre dÕitŽration et nombre dŽpend de la taille et de la nature de base de donnŽes.
 
 -- *paramtre* **enhance_data** (optionnel) : Ce paramtre est utilisŽ pour transformer votre base dÕimages en gŽnŽrant plus dÕŽchantillons pour la phase dÕentrainement. Par dŽfaut sa valeur est ÔFalseÕ. NŽanmoins, il est important de lui donner la valeur ÔTrueÕ lorsque votre base dÕimages contient moins de 1000 images par classe.

 -- *paramtre* **batch_size** (optionnel) : Pendant la phase dÕentrainement, LÕalgorithme est entrainŽ sur un ensemble dÕimages en parallle. A cause de cela, la valeur par dŽfaut est mise ˆ 32. Vous pouvez accroitre ou dŽcroitre cette valeur selon votre connaissance du systme que vous utilisez pour lÕapprentissage. Si vous envisagez de changer cette valeur, vous devrez utiliser des multiples de 8 pour optimiser le processus dÕapprentissage.   

 -- *paramtre* **show_network_summary** (optionnel) : Lorsque ce paramtre a la valeur ÔTrueÕ, il affiche la structure de lÕalgorithme que vous utilisez pour lÕapprentissage sur vos images dans une petite console avant de commencer lÕapprentissage. Sa valeur par dŽfaut est ÔFalseÕ. 
 
 -- *paramtre* **initial_learning_rate** (optionnel) : Ce paramtre a une haute valeur technique. Il dŽtermine et contr™le le comportement de votre apprentissage, ce qui est critique pour la prŽcision ˆ rŽaliser. Vous pouvez changer la valeur de ce paramtre si vous avez une pleine comprŽhension de sa fonctionnalitŽ.  

  -- *training_image_size* **initial_learning_rate** (optionnel) : Il reprŽsente la taille que vos images prendront pendant le processus dÕapprentissage, peu importe leur taille dÕorigine. La valeur par dŽfaut est de 224 et elle ne doit pas aller en dessous de 100. Augmenter sa valeur permettra de gagner en prŽcision mais augmentera aussi le temps dÕapprentissage et vice-versa.  



**Exemple de code pour un model apprentissage personnalise**

Trouvez ci-dessous un exemple de code lors de lÕapprentissage dÕun modle personnalisŽ sur votre base dÕimagesÊ:: 

    from imageai.Prediction.Custom import ModelTraining

    model_trainer = ModelTraining()
    model_trainer.setModelTypeAsResNet()
    model_trainer.setDataDirectory(r"C:/Users/Moses/Documents/Moses/AI/Custom Datasets/animaux")
    model_trainer.trainModel(num_objects=10, num_experiments=100, enhance_data=True, batch_size=32, show_network_summary=True)


Ci-dessous est un aperu de rŽsultat lorsque lÕapprentissage commenceÊ::

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

Expliquons les dŽtails ci-dessusÊ:

1. La ligne Epoch 1/100 signifie que le rŽseau fait le premier apprentissage sur les 100 voulus.  0

2. La ligne  1/25 [>.............................] - ETA: 52s - loss: 2.3026 - acc: 0.2500 reprŽsente le nombre de groupe qui ont ŽtŽ entrainŽ dans la prŽsente phase dÕapprentissage.  

3. La ligne  Epoch 00000: sauvegarde le modle ˆ lÕemplacement  C:\Users\User\PycharmProjects\ImageAITest\pets\models\modelex-000acc-0.100000.h5 ˆ la fin de la phase dÕapprentissage prŽsente.  ex_000 reprŽsente le niveau dÕapprentissage tandis que acc0.100000 et  valacc: 0.1000  reprŽsente la prŽcision du modle sur lÕensemble dÕimages ÔTestÕ aprs le prŽsent apprentissage(La valeur maximale de la prŽcision est de 1.0). Ce rŽsultat vous permet de connaitre le meilleur modle a utiliser pour la dŽtection sur vos images.

Une fois que vous avez terminŽ lÕapprentissage de votre modle termine, vous pouvez utiliser la classe **CustomImagePrediction**  dŽcrite si dessous pour la dŽtection avec votre modle. 




**======= imageai.Prediction.Custom.CustomImagePrediction =======**


Cette classe peut tre considŽrŽe comme une rŽplique de **imageai.Prediction.ImagePrediction** puis quÕelle a les mme fonctions, paramtres et rŽsultats. La seule diffŽrence est que cette classe fonctionne avec votre modle personnalisŽ. Vous aurez besoin de spŽcifier le chemin du fichier JSON gŽnŽrŽ pendant la phase dÕapprentissage et aussi de spŽcifier le nombre de classe dans votre base dÕimage lors du chargement du modle. Ci-dessous est un exemple de crŽation dÕinstance de la classeÊ::


    from imageai.Prediction.Custom import CustomImagePrediction
    
    prediction = CustomImagePrediction()

Une fois que vous avez crŽŽ lÕinstance, vous pouvez utiliser les fonctions ci-dessous pour configurer les propriŽtŽs de votre instance et commencer le processus de dŽtection et reconnaissance sur des images. 


* **.setModelTypeAsSqueezeNet()** , Cette fonction Žtablit comme type de modle pour votre instance de reconnaissance et dŽtection, le modle **SqueezeNet**, ceci  veut dire que lÕalgorithme **SqueezeNet** gŽnŽrŽ pendant votre phase dÕapprentissage personnalisŽe sera utilisŽ pour la tache de prŽdiction sur vos images. Trouver un exemple de code ci-dessousÊ::  


    prediction.setModelTypeAsSqueezeNet()


* **. setModelTypeAsResNet()** , Cette fonction Žtablit comme type de modle pour votre instance de reconnaissance et dŽtection, le modle ** ResNet**, ceci  veut dire que lÕalgorithme **ResNet** gŽnŽrŽ pendant votre phase dÕapprentissage personnalisŽe sera utilisŽ pour la tache de prŽdiction sur vos images. Trouver un exemple de code ci-dessousÊ::  


    prediction.setModelTypeAsResNet()

* **. setModelTypeAsInceptionV3 ()** , Cette fonction Žtablit comme type de modle pour votre instance de reconnaissance et dŽtection, le modle **InceptionV3**, ceci  veut dire que lÕalgorithme **InceptionV3** gŽnŽrŽ pendant votre phase dÕapprentissage personnalisŽe sera utilisŽ pour la tache de prŽdiction sur vos images. Trouver un exemple de code ci-dessousÊ::  


    prediction.setModelTypeAsInceptionV3()


* **. setModelTypeAsDenseNet()** , Cette fonction Žtablit comme type de modle pour votre instance de reconnaissance et dŽtection, le modle ** DenseNet**, ceci  veut dire que lÕalgorithme **DenseNet** gŽnŽrŽ pendant votre phase dÕapprentissage personnalisŽe sera utilisŽ pour la tache de prŽdiction sur vos images. Trouver un exemple de code ci-dessousÊ::  



    prediction.setModelTypeAsDenseNet()


* **.setModelPath()** , cette fonction accepte une chaine de caractre qui doit tre le chemin vers le fichier modle gŽnŽrŽ pendant votre phase dÕapprentissage et doit correspondre au type de modle que vous avez dŽfini pour votre instance de reconnaissance dÕimages. Trouver un exemple de code, et de paramtres de fonction ci-dessousÊ::


    prediction.setModelPath("resnet_model_ex-020_acc-0.651714.h5")

 -- *paramtre* **model_path** (requis) : Il sÕagit du chemin vers le fichier modle tŽlŽchargŽ.  


* **.setJsonPath()** , cette fonction prend en argument une chaine de caractre qui reprŽsente le chemin vers le fichier JSON gŽnŽrŽ pendant la phase dÕapprentissage du modle personnalisŽ. Trouvez ci-dessous un exemple de code et de paramtres de la fonctionÊ::

 
    prediction.setJsonPath("model_class.json")

 -- *paramtre* **model_path** (requis) : Il sÕagit du chemin vers le fichier modle tŽlŽchargŽ.  


* **.loadModel()** , Cette fonction charge le modle ˆ partir du chemin spŽcifiŽ dans votre appel de fonction ci-dessus pour votre instance de prŽdiction dÕimages. Au paramtre **num_objects** vous devrez donner la valeur correspondant au nombre de classes dans votre base dÕimages. Trouvez ci-dessous un exemple de code et de paramtres de la fonctionÊ::

    prediction.loadModel(num_objects=4)

 -- *paramtre* **num_objects** (requis) : La valeur de ce paramtre doit correspondre au nombre de classe dans votre base dÕimages.  


-- *paramtre* **prediction_speed** (optionnel) : Ce paramtre vous permet de rŽduire le temps de prŽdiction sur une image dÕenviron 80% ce qui conduit ˆ une lŽgre rŽduction de la prŽcision. Ce paramtre prend des valeurs de type chaine de caractre. Les valeurs disponibles sontÊ: 
"normal", "fast", "faster" et "fastest". La valeur par dŽfaut est "normal"


* **.predictImage()** , CÕest la fonction qui accomplit ˆ proprement parler la prŽdiction sur une image. Elle peut tre appeler plusieurs fois sur plusieurs images une fois que le modle a ŽtŽ charge dans lÕinstance de prŽdiction. Trouver ci-dessous un exemple de code, de paramtres de fonction ainsi que les valeurs renvoyŽesÊ::

    predictions, probabilities = prediction.predictImage("image1.jpg", result_count=2)

 -- *paramtre* **image_input** (requis) : Il fait rŽfŽrence au chemin vers votre image, le tableau de type Numpy de votre image ou le flux de votre image, dŽpendamment de type de valeur dÕentrŽe spŽcifiŽe. 


 -- *paramtre* **result_count** (optionnel) : il fait rŽfŽrence au nombre possible de prŽdiction qui peuvent tre donne. Ce paramtre a pour valeur par dŽfaut 5.   


 -- *paramtre* **input_type** (optionnel) :  Il fait rŽfŽrence au type de la valeur dÕentrŽe que vous passez au paramtre **image_input**. Il est de type ÔfileÕ par dŽfaut et accepte Ôstream Õet Ôarray Õaussi.

 -- *valeur retournŽe* **prediction_results** (une liste python) : 
La premire valeur retournŽe par la fonction **predictImage** est une liste qui contient tous les rŽsultats possibles de prŽdiction. Les rŽsultats sont ordonnŽs en ordre descendant de pourcentage de probabilitŽ.

 -- *valeur retournŽe* **prediction_probabilities** (une liste python) : 
La premire valeur retournŽe par la fonction **predictImage** est une liste qui contient les pourcentages de probabilitŽ correspondantes a toutes les prŽdictions possibles dans **prediction_results**


* **.predictMultipleImages()** , Cette fonction peut tre utilisŽe pour effectuer la tache de prŽdiction sur 2 ou plusieurs images en une seule fois. Trouvez ci-dessous un exemple de code, paramtres de fonction et de valeurs renvoyŽesÊ::

 
    results_array = multiple_prediction.predictMultipleImages(all_images_array, result_count_per_image=2)

    for each_result in results_array:
        predictions, percentage_probabilities = each_result["predictions"], each_result["percentage_probabilities"]
        for index in range(len(predictions)):
            print(predictions[index] , " : " , percentage_probabilities[index])
        print("-----------------------")

  -- *paramtre* **sent_images_array** (requis) : Il fait rŽfŽrence a une liste qui contient le chemin vers vos fichiers image, vos tableau Numpy de vos images ou vos fichiers de flux dÕimages, dŽpendamment du type de valeur dÕentrŽe spŽcifiŽe.   

  -- *paramtre* **result_count_per_image** (optionnel) : Il fait rŽfŽrence au nombre possible de prŽdictions qui doivent tre donnŽes pour chaque image. Ce paramtre a pour valeur par dŽfaut 2. 


-- *paramtre* **input_type** (optionnel) :  Il fait rŽfŽrence au format de vos images ont dans la liste du paramtre **sent_images_array**. Il est de type ÔfileÕ par dŽfaut et accepte Ôstream Õet Ôarray Õaussi. 


  -- *valeur retournŽe* **output_array** (une liste python) : 
La valeur retournŽe par la fonction **predictMultipleImages** est une liste qui contient des dictionnaires. Chaque dictionnaire correspond ˆ une image contenue dans le tableau envoyŽe ˆ **sent_images_array**. 
Chaque dictionnaire a une propriete "prediction_results" qui est une liste de tous les resultats de prediction pour lÕimage a cet indice aussi bien que la probabilite de prediction "prediction_probabilities" qui est une liste de pourcentage de probabilite correspondant a chaque resultat.

**Exemple de code**

Trouvez ci-dessous un Žchantillon de code pour la prŽdiction personnalisŽÊ::

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
