.. ImageAI documentation master file, created by
   sphinx-quickstart on Tue Jun 12 06:13:09 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Apprentissage personnalis� et pr�diction des Classes
======================================
**ImageAI** fournit des classes puissante et n�anmoins facile � utiliser pour entrainer des algorithmes a la pointe de la technologies tel que **SqueezeNet**, **ResNet** , **InceptionV3** et  **DenseNet** sur votre propre base de donn�es avec juste  **5 lignes de code** pour g�n�rer votre propre mod�le personnalis�. 
Une fois que vous avez entrain� votre propre mod�le, vous pouvez utiliser la classe **CustomImagePrediction** fournit par **ImageAI** pour utiliser votre mod�le pour reconnaitre et faire la d�tection sur une image ou un ensemble d�images. 



**======= imageai.Prediction.Custom.ModelTraining =======**



La classe **ModelTraining** vous permet d�entrainer un des quatre algorithme d�apprentissage profond suivant (**SqueezeNet**, **ResNet**
, **InceptionV3** et **DenseNet**) sur votre base de donn�es d�images pour g�n�rer votre propre mod�le. Votre base de donn�es d�images doit contenir au moins deux diff�rentes classes/types d�images (chat et chien) et vous devez ressembler au moins 500 images de chaque classe pour obtenir le maximum de pr�cision possible.  

Le processus d�entrainement g�n�r� un fichier JSON qui fait une correspondance entre les types d�objets dans votre base d�images et cr�� des mod�les.
Vous ferez le choix du mod�le avec la pr�cision la plus �lev�e et qui puisse faire la pr�diction en utilisant le mod�le et le fichier JSON g�n�r�. 

Puisse la t�che d�apprentissage est gourmande en ressource, nous recommandons fortement de la faire � l�aide d�un ordinateur �quip� d�un GPU NVIDIA et ayant le version GPU de Tensorflow install�e. Faire l�apprentissage sur un CPU va demander beaucoup d�heures et de jours. Avec un syst�me informatique �quip� d�un GPU NVIDIA cela ne devrait prendre que quelques heures. Vous pouvez utiliser Google Colab pour cette exp�rience, puisqu�il est �quip� d�un GPU NVIDIA K80.

Pour entrainer votre mod�le de pr�diction, vous devez pr�parer les images que vous voulez utiliser pour entrainer votre mod�le. Vous pr�parerez les images comme suit�:

 

 -- Cr�er un dossier avec le nom que vous aimeriez donner avec votre base de donn�es (ex: Chats) 

 -- Dans le dossier que vous avez pr�c�demment cr�e, cr�er un dossier que vous nommerez �train� 
 
 -- A cote du dossier train, cr�er un autre dossier et nommez le �test� 
 
 -- Dans le dossier �train�, cr�ez un dossier pour chaque type d�objets que vous aimeriez que votre mod�le reconnaisse et nomme le dossier selon la classe � pr�dire (ex�: chien, chat, �cureuil, serpents) 
 
 -- Dans chaque dossier pr�sent dans votre dossier �train�, mettez-y les images de chaque objet ou classe. Ces images seront utilis�es pour l�apprentissage de votre mod�le.
 
 -- pour g�n�rer un mod�le qui puisse �tre viable pour des applications robustes, Je vous recommande d�avoir au moins 500 images ou de plus par objets. 1000 images per objets serait mieux.  
 
 -- Dans le dossier �Test�, cr�er des dossiers et nommez les selon les noms que vous avez utilis� pour le dossier �Train�. Mettez environ 100 � 200 images correspondantes dans chaque dossier. Ces images seront celle utilis�es pour tester le mod�le apr�s l�avoir entrain�.
 
 -- Une fois que vous avez fait cela, la structure des dossiers de votre base d�images devrait �tre comme suit::

    animaux//train//chien//chien-train-images
    animaux//train//chat// chat -train-images
    animaux//train//lion // lion -train-images
    animaux//train//serpent// serpent -train-images

    animaux//test//chien //chien-test-images
    animaux//test//chat // chat -test-images
    animaux//test//lion// lion -test-images
    animaux//test//serpent // serpent -test-images



Une fois que votre base de donn�es est pr�te, vous pouvez cr�er une instance de la classe **ModelTraining**. Retrouver un exemple ci-dessous�:: 

    from imageai.Prediction.Custom import ModelTraining

    model_trainer = ModelTraining()

Une fois que vous avez cr�� l�instance ci-dessous, vous pouvez utiliser les fonctions ci-dessous pour commencer le processus d�entrainement. 


* **.setModelTypeAsSqueezeNet()** , Cette fonction �tablit comme type de mod�le pour votre instance d�entrainement le mod�le **SqueezeNet**, ceci  veut dire que l�algorithme **SqueezeNet** sera utilis� pour entrainer votre mod�le. Trouver un exemple de code ci-dessous�::  

    model_trainer.setModelTypeAsSqueezeNet()


* **.setModelTypeAsResNet()** , Cette fonction �tablit comme type de mod�le pour votre instance d�entrainement le mod�le **ResNet**, ceci  veut dire que l�algorithme **ResNet** sera utilis� pour entrainer votre mod�le.  Trouver un exemple de code ci-dessous :: 

    model_trainer.setModelTypeAsResNet()


* **.setModelTypeAsInceptionV3()** , Cette fonction �tablit comme type de mod�le pour votre instance d�entrainement le mod�le ** InceptionV3**, ceci  veut dire que l�algorithme ** InceptionV3** sera utilis� pour entrainer votre mod�le. Trouver un exemple de code ci-dessous�:: 

    model_trainer.setModelTypeAsInceptionV3()


* **.setModelTypeAsDenseNet()** , Cette fonction �tablit comme type de mod�le pour votre instance d�entrainement le mod�le **DenseNet**, ceci  veut dire que l�algorithme **DenseNet** sera utilis� pour entrainer votre mod�le. Trouver un exemple de code ci-dessous�::  

    model_trainer.setModelTypeAsDenseNet()

* **.setDataDirectory()** ,  Cette fonction prend en argument une chaine de caract�re qui doit �tre le chemin vers le dossier qui contient les sous-dossiers **test** et **train** qui contiennent votre base d�images. Retrouver un exemple d�utilisation de la fonction, et de ses param�tres ci-dessous ::

    prediction.setDataDirectory("C:/Users/Moses/Documents/Moses/AI/Custom Datasets/animaux")

 -- *parametre* **data_directory** (obligatoire) : Il s�agit du chemin vers le dossier qui contient votre base d�images. 

* **.trainModel()** , Il s�agit de la fonction qui commence le processus d�entrainement.  Une fois commenc�, il cr�era un fichier JSON dans le dossier **dataset/json** (ex **animaux/json**) qui contient la correspondance de chaque classe dans la base d�images. Le fichier JSON sera utilis� pendant la d�tection personnalis�e pour produire les r�sultats. Trouvez un exemple de code ci-dessous ::

    model_trainer.trainModel(num_objects=4, num_experiments=100, enhance_data=True, batch_size=32, show_network_summary=True)


 -- *param�tre* **num_objects** (obligatoire) : Ceci fait r�f�rence au nombre de diff�rentes classes dans votre base d�images.
 
 -- *param�tre* **num_experiments** (obligatoire) : Il repr�sente le nombre de fois que l�algorithme sera entrain� sur la base d�images. La pr�cision de votre entrainement augmente avec le nombre d�it�rations ou d�entrainement. Cependant la pr�cision atteint son maximum avec un certain nombre d�it�ration et nombre d�pend de la taille et de la nature de base de donn�es.
 
 -- *param�tre* **enhance_data** (optionnel) : Ce param�tre est utilis� pour transformer votre base d�images en g�n�rant plus dՎchantillons pour la phase d�entrainement. Par d�faut sa valeur est �False�. N�anmoins, il est important de lui donner la valeur �True� lorsque votre base d�images contient moins de 1000 images par classe.

 -- *param�tre* **batch_size** (optionnel) : Pendant la phase d�entrainement, L�algorithme est entrain� sur un ensemble d�images en parall�le. A cause de cela, la valeur par d�faut est mise � 32. Vous pouvez accroitre ou d�croitre cette valeur selon votre connaissance du syst�me que vous utilisez pour l�apprentissage. Si vous envisagez de changer cette valeur, vous devrez utiliser des multiples de 8 pour optimiser le processus d�apprentissage.   

 -- *param�tre* **show_network_summary** (optionnel) : Lorsque ce param�tre a la valeur �True�, il affiche la structure de l�algorithme que vous utilisez pour l�apprentissage sur vos images dans une petite console avant de commencer l�apprentissage. Sa valeur par d�faut est �False�. 
 
 -- *param�tre* **initial_learning_rate** (optionnel) : Ce param�tre a une haute valeur technique. Il d�termine et contr�le le comportement de votre apprentissage, ce qui est critique pour la pr�cision � r�aliser. Vous pouvez changer la valeur de ce param�tre si vous avez une pleine compr�hension de sa fonctionnalit�.  

  -- *training_image_size* **initial_learning_rate** (optionnel) : Il repr�sente la taille que vos images prendront pendant le processus d�apprentissage, peu importe leur taille d�origine. La valeur par d�faut est de 224 et elle ne doit pas aller en dessous de 100. Augmenter sa valeur permettra de gagner en pr�cision mais augmentera aussi le temps d�apprentissage et vice-versa.  



**Exemple de code pour un model apprentissage personnalise**

Trouvez ci-dessous un exemple de code lors de l�apprentissage d�un mod�le personnalis� sur votre base d�images�:: 

    from imageai.Prediction.Custom import ModelTraining

    model_trainer = ModelTraining()
    model_trainer.setModelTypeAsResNet()
    model_trainer.setDataDirectory(r"C:/Users/Moses/Documents/Moses/AI/Custom Datasets/animaux")
    model_trainer.trainModel(num_objects=10, num_experiments=100, enhance_data=True, batch_size=32, show_network_summary=True)


Ci-dessous est un aper�u de r�sultat lorsque l�apprentissage commence�::

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

Expliquons les d�tails ci-dessus�:

1. La ligne Epoch 1/100 signifie que le r�seau fait le premier apprentissage sur les 100 voulus.  0

2. La ligne  1/25 [>.............................] - ETA: 52s - loss: 2.3026 - acc: 0.2500 repr�sente le nombre de groupe qui ont �t� entrain� dans la pr�sente phase d�apprentissage.  

3. La ligne  Epoch 00000: sauvegarde le mod�le � l�emplacement  C:\Users\User\PycharmProjects\ImageAITest\pets\models\modelex-000acc-0.100000.h5 � la fin de la phase d�apprentissage pr�sente.  ex_000 repr�sente le niveau d�apprentissage tandis que acc0.100000 et  valacc: 0.1000  repr�sente la pr�cision du mod�le sur l�ensemble d�images �Test� apr�s le pr�sent apprentissage(La valeur maximale de la pr�cision est de 1.0). Ce r�sultat vous permet de connaitre le meilleur mod�le a utiliser pour la d�tection sur vos images.

Une fois que vous avez termin� l�apprentissage de votre mod�le termine, vous pouvez utiliser la classe **CustomImagePrediction**  d�crite si dessous pour la d�tection avec votre mod�le. 




**======= imageai.Prediction.Custom.CustomImagePrediction =======**


Cette classe peut �tre consid�r�e comme une r�plique de **imageai.Prediction.ImagePrediction** puis qu�elle a les m�me fonctions, param�tres et r�sultats. La seule diff�rence est que cette classe fonctionne avec votre mod�le personnalis�. Vous aurez besoin de sp�cifier le chemin du fichier JSON g�n�r� pendant la phase d�apprentissage et aussi de sp�cifier le nombre de classe dans votre base d�image lors du chargement du mod�le. Ci-dessous est un exemple de cr�ation d�instance de la classe�::


    from imageai.Prediction.Custom import CustomImagePrediction
    
    prediction = CustomImagePrediction()

Une fois que vous avez cr�� l�instance, vous pouvez utiliser les fonctions ci-dessous pour configurer les propri�t�s de votre instance et commencer le processus de d�tection et reconnaissance sur des images. 


* **.setModelTypeAsSqueezeNet()** , Cette fonction �tablit comme type de mod�le pour votre instance de reconnaissance et d�tection, le mod�le **SqueezeNet**, ceci  veut dire que l�algorithme **SqueezeNet** g�n�r� pendant votre phase d�apprentissage personnalis�e sera utilis� pour la tache de pr�diction sur vos images. Trouver un exemple de code ci-dessous�::  


    prediction.setModelTypeAsSqueezeNet()


* **. setModelTypeAsResNet()** , Cette fonction �tablit comme type de mod�le pour votre instance de reconnaissance et d�tection, le mod�le ** ResNet**, ceci  veut dire que l�algorithme **ResNet** g�n�r� pendant votre phase d�apprentissage personnalis�e sera utilis� pour la tache de pr�diction sur vos images. Trouver un exemple de code ci-dessous�::  


    prediction.setModelTypeAsResNet()

* **. setModelTypeAsInceptionV3 ()** , Cette fonction �tablit comme type de mod�le pour votre instance de reconnaissance et d�tection, le mod�le **InceptionV3**, ceci  veut dire que l�algorithme **InceptionV3** g�n�r� pendant votre phase d�apprentissage personnalis�e sera utilis� pour la tache de pr�diction sur vos images. Trouver un exemple de code ci-dessous�::  


    prediction.setModelTypeAsInceptionV3()


* **. setModelTypeAsDenseNet()** , Cette fonction �tablit comme type de mod�le pour votre instance de reconnaissance et d�tection, le mod�le ** DenseNet**, ceci  veut dire que l�algorithme **DenseNet** g�n�r� pendant votre phase d�apprentissage personnalis�e sera utilis� pour la tache de pr�diction sur vos images. Trouver un exemple de code ci-dessous�::  



    prediction.setModelTypeAsDenseNet()


* **.setModelPath()** , cette fonction accepte une chaine de caract�re qui doit �tre le chemin vers le fichier mod�le g�n�r� pendant votre phase d�apprentissage et doit correspondre au type de mod�le que vous avez d�fini pour votre instance de reconnaissance d�images. Trouver un exemple de code, et de param�tres de fonction ci-dessous�::


    prediction.setModelPath("resnet_model_ex-020_acc-0.651714.h5")

 -- *param�tre* **model_path** (requis) : Il s�agit du chemin vers le fichier mod�le t�l�charg�.  


* **.setJsonPath()** , cette fonction prend en argument une chaine de caract�re qui repr�sente le chemin vers le fichier JSON g�n�r� pendant la phase d�apprentissage du mod�le personnalis�. Trouvez ci-dessous un exemple de code et de param�tres de la fonction�::

 
    prediction.setJsonPath("model_class.json")

 -- *param�tre* **model_path** (requis) : Il s�agit du chemin vers le fichier mod�le t�l�charg�.  


* **.loadModel()** , Cette fonction charge le mod�le � partir du chemin sp�cifi� dans votre appel de fonction ci-dessus pour votre instance de pr�diction d�images. Au param�tre **num_objects** vous devrez donner la valeur correspondant au nombre de classes dans votre base d�images. Trouvez ci-dessous un exemple de code et de param�tres de la fonction�::

    prediction.loadModel(num_objects=4)

 -- *param�tre* **num_objects** (requis) : La valeur de ce param�tre doit correspondre au nombre de classe dans votre base d�images.  


-- *param�tre* **prediction_speed** (optionnel) : Ce param�tre vous permet de r�duire le temps de pr�diction sur une image d�environ 80% ce qui conduit � une l�g�re r�duction de la pr�cision. Ce param�tre prend des valeurs de type chaine de caract�re. Les valeurs disponibles sont�: 
"normal", "fast", "faster" et "fastest". La valeur par d�faut est "normal"


* **.predictImage()** , C�est la fonction qui accomplit � proprement parler la pr�diction sur une image. Elle peut �tre appeler plusieurs fois sur plusieurs images une fois que le mod�le a �t� charge dans l�instance de pr�diction. Trouver ci-dessous un exemple de code, de param�tres de fonction ainsi que les valeurs renvoy�es�::

    predictions, probabilities = prediction.predictImage("image1.jpg", result_count=2)

 -- *param�tre* **image_input** (requis) : Il fait r�f�rence au chemin vers votre image, le tableau de type Numpy de votre image ou le flux de votre image, d�pendamment de type de valeur d�entr�e sp�cifi�e. 


 -- *param�tre* **result_count** (optionnel) : il fait r�f�rence au nombre possible de pr�diction qui peuvent �tre donne. Ce param�tre a pour valeur par d�faut 5.   


 -- *param�tre* **input_type** (optionnel) :  Il fait r�f�rence au type de la valeur d�entr�e que vous passez au param�tre **image_input**. Il est de type �file� par d�faut et accepte �stream �et �array �aussi.

 -- *valeur retourn�e* **prediction_results** (une liste python) : 
La premi�re valeur retourn�e par la fonction **predictImage** est une liste qui contient tous les r�sultats possibles de pr�diction. Les r�sultats sont ordonn�s en ordre descendant de pourcentage de probabilit�.

 -- *valeur retourn�e* **prediction_probabilities** (une liste python) : 
La premi�re valeur retourn�e par la fonction **predictImage** est une liste qui contient les pourcentages de probabilit� correspondantes a toutes les pr�dictions possibles dans **prediction_results**


* **.predictMultipleImages()** , Cette fonction peut �tre utilis�e pour effectuer la tache de pr�diction sur 2 ou plusieurs images en une seule fois. Trouvez ci-dessous un exemple de code, param�tres de fonction et de valeurs renvoy�es�::

 
    results_array = multiple_prediction.predictMultipleImages(all_images_array, result_count_per_image=2)

    for each_result in results_array:
        predictions, percentage_probabilities = each_result["predictions"], each_result["percentage_probabilities"]
        for index in range(len(predictions)):
            print(predictions[index] , " : " , percentage_probabilities[index])
        print("-----------------------")

  -- *param�tre* **sent_images_array** (requis) : Il fait r�f�rence a une liste qui contient le chemin vers vos fichiers image, vos tableau Numpy de vos images ou vos fichiers de flux d�images, d�pendamment du type de valeur d�entr�e sp�cifi�e.   

  -- *param�tre* **result_count_per_image** (optionnel) : Il fait r�f�rence au nombre possible de pr�dictions qui doivent �tre donn�es pour chaque image. Ce param�tre a pour valeur par d�faut 2. 


-- *param�tre* **input_type** (optionnel) :  Il fait r�f�rence au format de vos images ont dans la liste du param�tre **sent_images_array**. Il est de type �file� par d�faut et accepte �stream �et �array �aussi. 


  -- *valeur retourn�e* **output_array** (une liste python) : 
La valeur retourn�e par la fonction **predictMultipleImages** est une liste qui contient des dictionnaires. Chaque dictionnaire correspond � une image contenue dans le tableau envoy�e � **sent_images_array**. 
Chaque dictionnaire a une propriete "prediction_results" qui est une liste de tous les resultats de prediction pour l�image a cet indice aussi bien que la probabilite de prediction "prediction_probabilities" qui est une liste de pourcentage de probabilite correspondant a chaque resultat.

**Exemple de code**

Trouvez ci-dessous un �chantillon de code pour la pr�diction personnalis��::

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
