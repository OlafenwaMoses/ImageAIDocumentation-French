.. ImageAI documentation master file, created by
   sphinx-quickstart on Tue Jun 12 06:13:09 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Les Classes de detection
=================
**ImageAI** fournit un ensemble de classes et fonctions puissantes et faciles à utiliser pour la **Détection et Extraction d’objets dans une image**.
**ImageAI** vous permet d’utiliser les algorithmes de pointe en apprentissage profond tel que **RetinaNet**, **YOLOv3** et **TinyYOLOv3**. Avec **ImageAI** vous pouvez accomplir des taches de détection et d’analyse d’images. 
Trouvez ci-dessous les classes et leurs fonctions respectives mise à votre disposition pour votre utilisation. Ces classes peuvent être intégrées dans tout programme Python traditionnel que vous développez ; que ce soit un site internet, une application Windows/Linux/MacOS ou un système qui supporte ou fait partir d’un réseau local.   



**======= imageai.Detection.ObjectDetection =======**


Cette classe **ObjectDetection** vous fournit les fonctions pour accomplir la détection d’objets sur une image ou un ensemble d’images, utilisant les modèles **pré-entraines** sur la base de données **COCO**.  
Les modèles supportés sont **RetinaNet**, **YOLOv3** et **TinyYOLOv3**.
Ceci veut dire que vous pouvez détecter et reconnaitre 80 différents types communs d’objets de tous les jours. Pour commencer, télécharger n’importe quel modèle que vous voulez utiliser via les liens ci-dessous :  


`Télécharger le modèle RetinaNet - resnet50_coco_best_v2.0.1.h5 <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

`Télécharger le modèle YOLOv3 - yolo.h5 <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

`Télécharger le modèle TinyYOLOv3 - yolo-tiny.h5 <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

Une fois que vous avez télécharger le modèle de votre choix, vous devez créer une instance de la classe **ObjectDetection** comme dans l’exemple ci-dessous ::



    from imageai.Detection import ObjectDetection
    
    detector = ObjectDetection()

Une fois que vois vous avez créé une instance de la classe, vous pouvez utiliser les fonctions ci-dessous pour choisir convenablement les propriétés d’instance et de commencer la détection d’objets sur les images. 


* **.setModelTypeAsRetinaNet()** , cette fonction établit comme type de modèle pour l’instance de détection d’objets que vous avez créé le modèle **RetinaNet**, ceci veut dire que vous accomplirez la tache de détection d’objets à l’aide de modèle pré-entrainé de **RetinaNet** que vous avez téléchargé par les liens ci-dessus. Trouvez un exemple de code ci-dessous :: 

    detector.setModelTypeAsRetinaNet()

* **.setModelTypeAsYOLOv3()** , cette fonction établit comme type de modèle pour l’instance de détection d’objets que vous avez créé le modèle **YOLOv3**, ceci veut dire que vous accomplirez la tache de détection d’objets à l’aide de modèle pré-entrainé de **YOLOv3** que vous avez téléchargé par les liens ci-dessus. Trouvez un exemple de code ci-dessous :: 

    detector.setModelTypeAsYOLOv3()

* **.setModelTypeAsTinyYOLOv3()** , cette fonction établit comme type de modèle pour l’instance de détection d’objets que vous avez créé le modèle **TinyYOLOv3**, ceci veut dire que vous accomplirez la tache de détection d’objets à l’aide de modèle pré-entrainé de **TinyYOLOv3** que vous avez téléchargé par les liens ci-dessus. Trouvez un exemple de code ci-dessous :: 

    detector.setModelTypeAsTinyYOLOv3()


* **.setModelPath()** , Cette fonction prend en argument une chaine de caractères qui doit être le chemin vers le fichier modèle que vous avez téléchargé et doit correspondre au type de modèle choisi pour votre instance de détection d’objets. Trouvez un exemple de code et de paramètres de fonction ci-dessous : 

    detector.setModelPath("yolo.h5")

 -- *paramètre* **model_path** (requis) : c’est le chemin vers votre modèle téléchargé. 

* **.loadModel()** ,  Cette fonction charge le modèle à partir du chemin que vous avez spécifié dans l’appel de fonction ci-dessus de votre instance de détection d’objets. Trouver un exemple de code ci-dessous ::

    detector.loadModel()

 -- *paramètre* **detection_speed** (optionnel) : Ce paramètre vous permet de réduire jusqu’à 80% le temps qu’il faut pour détecter les objets sur une image ce qui conduit à une légère réduction de la précision. Ce paramètre accepte des valeurs de type chaines de caractères. Les valeurs disponibles sont **normal**, **fast**, **faster**, **fastest** et **flash**. La valeur par défaut est **normal**


* **.detectObjectsFromImage()** ,C’est la fonction qui accomplit la détection d’objets après que le modèle ait été chargé. Elle peut être appelée plusieurs fois pour détecter les objets dans plusieurs images. Trouvez un exemple de code ci-dessous ::

 
    detections = detector.detectObjectsFromImage(input_image="image.jpg", output_image_path="imagenew.jpg", minimum_percentage_probability=30)

 -- *paramètre* **input_image** (requis) : Il fait référence au chemin vers le fichier image sur lequel vous voulez faire la détection. Ce paramètre peut être le tableau **Numpy** ou le fichier flux de l’image si vous donner la valeur "array" ou "stream" au paramètre **input_type**.


 -- *paramètre* **output_image_path** (requis seulement si **input_type** = "file" ) : Il fait référence au chemin vers le lieu de sauvegarde de l’image détectée ou détection. Il n’est requis que si **input_type** = "file".



 -- *paramètre* **minimum_percentage_probability** (optionnel) : Ce paramètre est utilisé pour déterminer l’intégrité des résultats de détections. Réduire cette valeur permettra de détecter plus d’objets alors que l’augmenter permet d’avoir des objets détectés avec la plus grande précision. La valeur par défaut est 50. 


 -- *paramètre* **output_type** (optionnel) : ce paramètre permet de définir le format dans lequel l’image de détections sera produit. Les valeurs disponibles sont ‘file’(fichier) et ‘array’(tableau). La valeur par défaut est ‘file’.  Si ce paramètre est définit comme ‘array’, la fonction va renvoyer un tableau Numpy pour l’image de détection. Retrouvez un exemple ci-dessous ::  


     returned_image, detections = detector.detectObjectsFromImage(input_image="image.jpg", output_type="array", minimum_percentage_probability=30)

 -- *paramètre* **display_percentage_probability** (optionnel) : Ce paramètre peut être utilisé pour cacher le pourcentage de probabilité de chaque objet détecté dans l’image de détectée si sa valeur est définie à ‘False’. La valeur par défaut est ‘True’. 

 -- *paramètre* **display_object_name** (optionnel) : Ce paramètre peut être utilisé pour cacher le nom de chaque objet détecté dans l’image de détection si sa valeur est définie comme ‘False’. La valeur par défaut est ‘True’.


 -- *paramètre* **extract_detected_objects** (optionnel) : ce paramètre peut être utilisé pour extraire et sauvegarder/ retourner chaque objet détecté dans une image dans une image séparée. Sa valeur par défaut est ‘False’. 

 -- *valeurs renvoyées* : Les valeurs renvoyées vont dépendre des paramètres envoyés dans la fonction **detectObjectsFromImage()**. Retrouvez les commentaires et le code ci-dessous :

                
        """
            
Si tous les paramètres nécessaires sont définis et 'output_image_path' est défini vers le chemin où le fichier de détection sera sauvegardé, la fonction va renvoyer :
1. un tableau de dictionnaires, avec chaque dictionnaire correspondant aux objets détectés dans l’image. Chaque dictionnaire a les propriétés suivantes :
       *Nom (chaine de caractères -- string)
            	 * percentage_probability (float)
	         	 * box_points (tuple de coordonnées x1,y1,x2 et y2)

                   """
        detections = detector.detectObjectsFromImage(input_image="image.jpg", output_image_path="imagenew.jpg", minimum_percentage_probability=30)


        """
Si tous les paramètres requis sont définis et output_type = 'array', la fonction va renvoyer
1. Un tableau Numpy de l’image de détection.
2. Un tableau de dictionnaires, avec chaque dictionnaire correspondant aux objets détectés dans l’image. Chaque dictionnaire contient les propriétés suivantes :
* Nom (string – chaine de caractères)
* percentage_probability (float)
* box_points (tuple de coordonnées x1,y1,x2 et y2)

        """
        returned_image, detections = detector.detectObjectsFromImage(input_image="image.jpg", output_type="array", minimum_percentage_probability=30)


        """
	 
            Si extract_detected_objects = True et 'output_image_path' est défini par le chemin vers le lieu de sauvegarde de l’image de détection, la fonction renvoie :
1. Un tableau de dictionnaires, chaque dictionnaire correspond aux objets détectés dans l’image. Chaque dictionnaire contient les propriétés suivantes :
* Nom (string)
* percentage_probability (float)
* box_points (tuple de coordonnées x1,y1,x2 et y2)
2. Un tableau de chaine de caractères représentant les chemins des images de chaque objet extrait de l’image de départ. 

        """
        detections, extracted_objects = detector.detectObjectsFromImage(input_image="image.jpg", output_image_path="imagenew.jpg", extract_detected_objects=True, minimum_percentage_probability=30)


        """
            Si extract_detected_objects = True et output_type = 'array', la fonction va renvoyer :
1. Un tableau Numpy de l’image de détection.
2. Un tableau de dictionnaires, avec chaque dictionnaire correspondant aux objets détectés dans l’image. Chaque dictionnaire contient les propriétés suivantes :
* nom(string)
* percentage_probability (float)
* box_points (tuple de coordonnées x1,y1,x2 et y2)
	3. Un tableau de tableaux Numpy de chaque objet détecté dans l’image   
        """
        returned_image, detections, extracted_objects = detector.detectObjectsFromImage(input_image="image.jpg", output_type="array", extract_detected_objects=True, minimum_percentage_probability=30)



* **.CustomObjects()** ,C’est la fonction que vous utiliserez lorsque vous ne voulez faire la détection que d’un nombre limité d’objets. Elle renvoie un dictionnaire d’objets et leur valeur ‘True’ ou ‘False’. Pour détecter les objets sélectionnés dans une image, vous devrez utiliser les dictionnaires renvoyés par cette fonction avec la fonction ** detectCustomObjectsFromImage()** . Retrouvez les détails dans les commentaires et le code ci-dessous ::

        
        """
Il y’a 80 possible objets que vous pouvez détecter avec la classe ObjectDetection, vous pouvez les voir ci-dessous. 

            Person(personne),   bicycle(vélo),   car(voiture),   motorcycle(moto),   airplane(avion),
            Bus(bus),   train(train),   truck(camion),   boat(bateau),   traffic light(feu de signalisation),   fire hydrant (bouche d’incendie),   stop_sign (panneau stop),
            parking meter (parc mètre),   bench (banc),   bird (oiseau),   cat (chat),   dog (chien),   horse (cheval),   sheep (brebis),   cow (vache),   elephant (elephant),   bear (ours),   zebra (zebre),
            giraffe (girafe),   backpack (sac à dos),   umbrella (parapluie),   handbag (sac à main),   tie (cravate),   suitcase (valise),   frisbee (frisbee),   skis (skis),   snowboard (snowboard),
            sports ball(balle de sport),   kite (cerf - volant),   baseball bat (batte de baseball),   baseball glove (gang de baseball),   skateboard (skateboard),   surfboard  (planche de surf),   tennis racket (raquette de tennis),
            bottle (bouteille),   wine glass (verre de vin),   cup (gobelet),   fork (fourchette),   knife (couteau),   spoon (cuillère),   bowl (bolle),   banana (banane),   apple (pomme),   sandwich (sandwich),   orange (orange),
            broccoli (brocoli),   carrot (carotte),   hot dog (hot dog),   pizza (pizza),   donut (beignet),   cake(gâteau),   chair (chaise),   couch(canape),   potted plant(plante a pot),   bed(lit),
            dining table(table de diner),   toilet(toilette),   tv(télévision),   laptop(ordinateur),   mouse(souris),   remote(télécommande),   keyboard(clavier),   cell phone(téléphone portable),   microwave(micro-onde),
            oven  (four),   toaster(grille pain),   sink(évier),   refrigerator (réfrigérateur),   book (cahier),   clock (horloge),   vase(vase) ,   scissors(ciseaux),   teddy bear(ours en peluche),   hair dryer(sèche cheveux),
            toothbrush(brosse à dent).

Pour détecter uniquement certains des objets ci-dessus, vous devrez instancier la fonction CustomObjects et définir le ou les noms des objets que vous voulez détecter. Le reste sera défini à ‘False’ par défaut. Dans l’exemple ci-dessous, nous détectons uniquement ‘person’(personne) et ‘dog’(chien). 
     
        """
        custom = detector.CustomObjects(person=True, dog=True)


* **.detectCustomObjectsFromImage()**, Cette fonction a tous les paramètres et renvoie toutes les valeurs de la fonction ** detectObjectsFromImage()**, avec une petite différence. Cette fonction ne fait la détection sur une image que d’objets sélectionnés. Contrairement à la fonction ** detectObjectsFromImage()**, elle a besoin d’un paramètre supplémentaire qui est **custom_objet** qui lui récupère le dictionnaire renvoyé par la fonction ** CustomObjects()**. Dans l’exemple ci-dessous, nous avons défini la fonction de détection pour qu’elle ne reconnaisse que les personnes et les chiens :: 

    
    custom = detector.CustomObjects(person=True, dog=True)

    detections = detector.detectCustomObjectsFromImage( custom_objects=custom, input_image=os.path.join(execution_path , "image3.jpg"), output_image_path=os.path.join(execution_path , "image3new-custom.jpg"), minimum_percentage_probability=30)

        

** Exemple de code pour la détection d’objets sur Image **

Trouvez ci-dessous un exemple de code pour détecter les objets sur une image :: 

    from imageai.Detection import ObjectDetection
    import os

    execution_path = os.getcwd()

    detector = ObjectDetection()
    detector.setModelTypeAsYOLOv3()
    detector.setModelPath( os.path.join(execution_path , "yolo.h5"))
    detector.loadModel()
    detections = detector.detectObjectsFromImage(input_image=os.path.join(execution_path , "image.jpg"), output_image_path=os.path.join(execution_path , "imagenew.jpg"), minimum_percentage_probability=30)

    for eachObject in detections:
        print(eachObject["name"] , " : ", eachObject["percentage_probability"], " : ", eachObject["box_points"] )
        print("--------------------------------")










.. toctree::
   :maxdepth: 2
   :caption: Contents:

   
