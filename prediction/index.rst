.. ImageAI documentation master file, created by
   sphinx-quickstart on Tue Jun 12 06:13:09 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Classes de pr�diction
==================
**ImageAI** fournit un ensemble de classes puissantes et faciles � utiliser pour accomplir les t�ches de *reconnaissance sur les images*.
Vous pouvez pourrez accomplir toutes ces taches de pointe de vision assist�e par ordinateur avec du code python allant de 5 � 12 lignes de code. 
Une fois que le python installe, d�autres biblioth�ques et **ImageAI** installes dans votre ordinateur, il n�y a aucune limite aux applications incroyables que vous pouvez cr�er. Trouvez ci-dessous les classes et leur fonction respective rendues disponibles pour votre utilisation.
Ces classes peuvent �tre int�gr�es dans n�importe quelle programme python traditionnel que vous d�veloppez, que cela soit un site internet, une application Windows/Linux/MacOS ou un syst�me qui supporte ou fait partir d�un r�seau local. 


**======= imageai.Prediction.ImagePrediction =======**

La classe **ImagePrediction** vous fournit des fonctions pour utiliser les mod�les de reconnaissance d�images les plus pointus tel **SqueezeNet**, **ResNet**, **InceptionV3** et **DenseNet** qui ont �t� **pr�-entraines** sur la base de donn�es **ImageNet-1000**.  Ceci pour dire que vous pouvez utiliser ces classes pour d�tecter et reconnaitre plus de 1000 diff�rents objets sur n�importe quelle image ou ensemble d�images. Pour initialiser la classe dans votre code, vous allez cr�er une instance dans votre code comme suit�::
    
    from imageai.Prediction import ImagePrediction
    prediction = ImagePrediction()


Nous avons fourni les mod�les pr�-entraines de reconnaissance d�images des algorithmes suivants **SqueezeNet**, **ResNet**, **InceptionV3** et **DenseNet** que vous allez utiliser dans la classe **ImagePrediction** pour faire la reconnaissance sur les images. Trouvez ci-dessous le lien pour t�l�charger les mod�les. Vous pouvez t�l�charger le mod�le que vous voulez utiliser. 

`Telechargez le modele SqueezeNet <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

`T�l�chargez le mod�le ResNet <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

` T�l�chargez le mod�le InceptionV3 <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

` T�l�chargez le mod�le DenseNet <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

Apr�s avoir cr�� une nouvelle instance de la classe **ImagePrediction**, Vous pouvez utiliser les fonctions ci-dessous pour d�finir les valeurs des propri�t�s et commencer la reconnaissance.   

* **.setModelTypeAsSqueezeNet()** , cette fonction �tablit comme mod�le pour votre instance de reconnaissance d�image que vous avez cr��, le mod�le **SqueezeNet**�; ce qui veut dire que vous accomplirez vos taches de pr�diction en utilisant les mod�les pr�-entrain�s de **SqueezeNet** que vous avez t�l�charg� avec le lien ci-dessus. Trouvez le code ci-dessous�::


    prediction.setModelTypeAsSqueezeNet()


* **.setModelTypeAsResNet()** , cette fonction �tablit comme mod�le pour votre instance de reconnaissance d�image que vous avez cr��, le mod�le **ResNet**�; ce qui veut dire que vous accomplirez vos taches de pr�diction en utilisant les mod�les pr�-entrain�s de **ResNet** que vous avez t�l�charg� avec le lien ci-dessus. Trouvez le code ci-dessous�::


    prediction.setModelTypeAsResNet()


* **.setModelTypeAsInceptionV3()** , cette fonction �tablit comme mod�le pour votre instance de reconnaissance d�image que vous avez cr��, le mod�le **InceptionV3**�; ce qui veut dire que vous accomplirez vos taches de pr�diction en utilisant les mod�les pr�-entrain�s de **InceptionV3** que vous avez t�l�charg� avec le lien ci-dessus. Trouvez le code ci-dessous�::



    prediction.setModelTypeAsInceptionV3()


* **.setModelTypeAsDenseNet()** , cette fonction �tablit comme mod�le pour votre instance de reconnaissance d�image que vous avez cr��, le mod�le **DenseNet**�; ce qui veut dire que vous accomplirez vos taches de pr�diction en utilisant les mod�les pr�-entrain�s de **DenseNet** que vous avez t�l�charg� avec le lien ci-dessus. Trouvez le code ci-dessous�::

    prediction.setModelTypeAsDenseNet()


* **.setModelPath()** , cette fonction accepte une chaine de caract�re qui doit �tre le chemin vers le fichier mod�le que vous avez t�l�charg�, il doit correspondre au type de mod�le que vous avez choisi pour votre instance de pr�diction/d�tection sur image. Trouvez un exemple de code, et param�tres de fonction ci-dessous�::
    prediction.setModelPath("resnet50_weights_tf_dim_ordering_tf_kernels.h5")

 -- *param�tre* **model_path** (requis) : Il s�agit du chemin vers votre fichier mod�le t�l�charg�.  

* **.loadModel()** , Cette fonction charge le mod�le � partir du chemin que vous avez sp�cifi� dans l�appel de fonction ci-dessus dans votre instance de pr�diction. Trouvez un exemple de code ci-dessous�::

    prediction.loadModel()

 -- *param�tre* **prediction_speed** (optionnel) : Ce param�tre vous permet de r�duire jusquՈ 80% le temps qu�il faut pour la tache de pr�diction sur une image, ce qui conduit � une l�g�re r�duction de la pr�cision. Ce param�tre accepte les chaines de caract�res. Les valeurs disponibles sont "normal", "fast", "faster" et "fastest". La valeur par d�faut est "normal". 


* **.predictImage()** , C�est la fonction qui effectue la tache de pr�diction a proprement parle sur une image.  Elle peut �tre appel�e plusieurs fois sur plusieurs images une fois que le mod�le a �t� charge dans l�instance de pr�diction. Trouvez un exemple de code, et param�tres de fonction ci-dessous�::
     
    predictions, probabilities = prediction.predictImage("image1.jpg", result_count=10)


 -- *param�tre* **image_input** (requis) : Il fait r�f�rence au chemin vers votre fichier images, tableau Numpy de votre image ou le fichier flux de votre image, d�pendamment du type que vous avez choisi. 


 -- *param�tre* **result_count** (optionnel) : Il fait r�f�rence au nombre possible de pr�dictions qui doivent �tre retourne. Le param�tre a une valeur par d�faut de 5. 


 -- *param�tre* **input_type** (optionnel) : Il fait r�f�rence au type de la valeur d�entr�e dans le param�tre **image_input**. Il est �file� par d�faut et accepte �array� et �stream� aussi. �


 -- *valeur retourn�e* **prediction_results** (une liste python) : La premi�re valeur renvoy�e par la fonction **predictImage** est une liste qui contient tous les r�sultats possibles de pr�diction. Les r�sultats sont arrang�s dans l�ordre descendant de probabilit� de pourcentage. 

 -- *valeur retourn�e* **prediction_probabilities** (une liste python) :
La seconde valeur renvoy�e par la fonction **predictImage** est une liste qui contient les pourcentages de probabilit� correspondant � toutes les pr�dictions possibles dans **prediction_results**


* **.predictMultipleImages()** , Cette fonction pour accomplir la pr�dictions sur 2 ou plusieurs images � la fois. Trouvez un exemple de code, et param�tres de fonction ci-dessous�::
 


    results_array = multiple_prediction.predictMultipleImages(all_images_array, result_count_per_image=5)

    for each_result in results_array:
        predictions, percentage_probabilities = each_result["predictions"], each_result["percentage_probabilities"]
        for index in range(len(predictions)):
            print(predictions[index] , " : " , percentage_probabilities[index])
        print("-----------------------")

  -- *param�tre* **sent_images_array** (requis) : Il fait r�f�rence a une liste qui contient le chemin vers les fichiers images, les tableaux Numpy de vos images ou les fichiers de flux de vos images, d�pendamment de type sp�cifie pour la valeur d�entr�e. 


  -- *param�tre* **result_count_per_image** (optionnel) : Il fait r�f�rence au nombre de possible de pr�dictions renvoy�es pour chaque image. Ce param�tre a pour valeur par d�faut 2. 


  -- *param�tre* **input_type** (optionnel) : Il fait r�f�rence au format dans lequel vos images sont repr�sent�es dans la liste contenu dans le param�tre **sent_images_array**. Il est par d�faut �file� et accepte aussi �array� et �stream�. 


  -- *valeur retourn�e* **output_array** (une liste python) : La valeur retourn�e par la fonction **predictMultipleImages** est une liste qui contient des dictionnaires. Chaque dictionnaire correspond � une image contenue dans le tableau transmis a **sent_images_array**. Chaque dictionnaire a une propri�t� "prediction_results" qui est la liste de tous les r�sultats de pr�dictions sur l�image a cet indice ainsi que la �prediction_probabilities� qui est la liste correspondant au pourcentage de probabilit� de chaque r�sultat. 


**Exemple de code**

Trouver ci-dessous un �chantillon de code pour la pr�diction sur une image�:: 

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

Trouvez ci-dessous un �chantillon de code pour la d�tection/pr�diction sur plusieurs images�::

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

   


