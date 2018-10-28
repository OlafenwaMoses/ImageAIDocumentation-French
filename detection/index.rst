.. ImageAI documentation master file, created by
   sphinx-quickstart on Tue Jun 12 06:13:09 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Les Classes de detection
=================
**ImageAI** fournit un ensemble de classes et fonctions puissantes et faciles ˆ utiliser pour la **DŽtection et Extraction dÕobjets dans une image**.
**ImageAI** vous permet dÕutiliser les algorithmes de pointe en apprentissage profond tel que **RetinaNet**, **YOLOv3** et **TinyYOLOv3**. Avec **ImageAI** vous pouvez accomplir des taches de dŽtection et dÕanalyse dÕimages. 
Trouvez ci-dessous les classes et leurs fonctions respectives mise ˆ votre disposition pour votre utilisation. Ces classes peuvent tre intŽgrŽes dans tout programme Python traditionnel que vous dŽveloppez ; que ce soit un site internet, une application Windows/Linux/MacOS ou un systme qui supporte ou fait partir dÕun rŽseau local.   



**======= imageai.Detection.ObjectDetection =======**


Cette classe **ObjectDetection** vous fournit les fonctions pour accomplir la dŽtection dÕobjets sur une image ou un ensemble dÕimages, utilisant les modles **prŽ-entraines** sur la base de donnŽes **COCO**.  
Les modles supportŽs sont **RetinaNet**, **YOLOv3** et **TinyYOLOv3**.
Ceci veut dire que vous pouvez dŽtecter et reconnaitre 80 diffŽrents types communs dÕobjets de tous les jours. Pour commencer, tŽlŽcharger nÕimporte quel modle que vous voulez utiliser via les liens ci-dessousÊ:  


`TŽlŽcharger le modle RetinaNet - resnet50_coco_best_v2.0.1.h5 <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

`TŽlŽcharger le modle YOLOv3 - yolo.h5 <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

`TŽlŽcharger le modle TinyYOLOv3 - yolo-tiny.h5 <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

Une fois que vous avez tŽlŽcharger le modle de votre choix, vous devez crŽer une instance de la classe **ObjectDetection** comme dans lÕexemple ci-dessousÊ::



    from imageai.Detection import ObjectDetection
    
    detector = ObjectDetection()

Une fois que vois vous avez crŽŽ une instance de la classe, vous pouvez utiliser les fonctions ci-dessous pour choisir convenablement les propriŽtŽs dÕinstance et de commencer la dŽtection dÕobjets sur les images. 


* **.setModelTypeAsRetinaNet()** , cette fonction Žtablit comme type de modle pour lÕinstance de dŽtection dÕobjets que vous avez crŽŽ le modle **RetinaNet**, ceci veut dire que vous accomplirez la tache de dŽtection dÕobjets ˆ lÕaide de modle prŽ-entrainŽ de **RetinaNet** que vous avez tŽlŽchargŽ par les liens ci-dessus. Trouvez un exemple de code ci-dessousÊ:: 

    detector.setModelTypeAsRetinaNet()

* **.setModelTypeAsYOLOv3()** , cette fonction Žtablit comme type de modle pour lÕinstance de dŽtection dÕobjets que vous avez crŽŽ le modle **YOLOv3**, ceci veut dire que vous accomplirez la tache de dŽtection dÕobjets ˆ lÕaide de modle prŽ-entrainŽ de **YOLOv3** que vous avez tŽlŽchargŽ par les liens ci-dessus. Trouvez un exemple de code ci-dessousÊ:: 

    detector.setModelTypeAsYOLOv3()

* **.setModelTypeAsTinyYOLOv3()** , cette fonction Žtablit comme type de modle pour lÕinstance de dŽtection dÕobjets que vous avez crŽŽ le modle **TinyYOLOv3**, ceci veut dire que vous accomplirez la tache de dŽtection dÕobjets ˆ lÕaide de modle prŽ-entrainŽ de **TinyYOLOv3** que vous avez tŽlŽchargŽ par les liens ci-dessus. Trouvez un exemple de code ci-dessousÊ:: 

    detector.setModelTypeAsTinyYOLOv3()


* **.setModelPath()** , Cette fonction prend en argument une chaine de caractres qui doit tre le chemin vers le fichier modle que vous avez tŽlŽchargŽ et doit correspondre au type de modle choisi pour votre instance de dŽtection dÕobjets. Trouvez un exemple de code et de paramtres de fonction ci-dessous : 

    detector.setModelPath("yolo.h5")

 -- *paramtre* **model_path** (requis) : cÕest le chemin vers votre modle tŽlŽchargŽ. 

* **.loadModel()** ,  Cette fonction charge le modle ˆ partir du chemin que vous avez spŽcifiŽ dans lÕappel de fonction ci-dessus de votre instance de dŽtection dÕobjets. Trouver un exemple de code ci-dessousÊ::

    detector.loadModel()

 -- *paramtre* **detection_speed** (optionnel) : Ce paramtre vous permet de rŽduire jusquÕˆ 80% le temps quÕil faut pour dŽtecter les objets sur une image ce qui conduit ˆ une lŽgre rŽduction de la prŽcision. Ce paramtre accepte des valeurs de type chaines de caractres. Les valeurs disponibles sont **normal**, **fast**, **faster**, **fastest** et **flash**. La valeur par dŽfaut est **normal**


* **.detectObjectsFromImage()** ,CÕest la fonction qui accomplit la dŽtection dÕobjets aprs que le modle ait ŽtŽ chargŽ. Elle peut tre appelŽe plusieurs fois pour dŽtecter les objets dans plusieurs images. Trouvez un exemple de code ci-dessousÊ::

 
    detections = detector.detectObjectsFromImage(input_image="image.jpg", output_image_path="imagenew.jpg", minimum_percentage_probability=30)

 -- *paramtre* **input_image** (requis) : Il fait rŽfŽrence au chemin vers le fichier image sur lequel vous voulez faire la dŽtection. Ce paramtre peut tre le tableau **Numpy** ou le fichier flux de lÕimage si vous donner la valeur "array" ou "stream" au paramtre **input_type**.


 -- *paramtre* **output_image_path** (requis seulement si **input_type** = "file" ) : Il fait rŽfŽrence au chemin vers le lieu de sauvegarde de lÕimage dŽtectŽe ou dŽtection. Il nÕest requis que si **input_type** = "file".



 -- *paramtre* **minimum_percentage_probability** (optionnel) : Ce paramtre est utilisŽ pour dŽterminer lÕintŽgritŽ des rŽsultats de dŽtections. RŽduire cette valeur permettra de dŽtecter plus dÕobjets alors que lÕaugmenter permet dÕavoir des objets dŽtectŽs avec la plus grande prŽcision. La valeur par dŽfaut est 50. 


 -- *paramtre* **output_type** (optionnel) : ce paramtre permet de dŽfinir le format dans lequel lÕimage de dŽtections sera produit. Les valeurs disponibles sont ÔfileÕ(fichier) et ÔarrayÕ(tableau). La valeur par dŽfaut est ÔfileÕ.  Si ce paramtre est dŽfinit comme ÔarrayÕ, la fonction va renvoyer un tableau Numpy pour lÕimage de dŽtection. Retrouvez un exemple ci-dessousÊ::  


     returned_image, detections = detector.detectObjectsFromImage(input_image="image.jpg", output_type="array", minimum_percentage_probability=30)

 -- *paramtre* **display_percentage_probability** (optionnel) : Ce paramtre peut tre utilisŽ pour cacher le pourcentage de probabilitŽ de chaque objet dŽtectŽ dans lÕimage de dŽtectŽe si sa valeur est dŽfinie ˆ ÔFalseÕ. La valeur par dŽfaut est ÔTrueÕ. 

 -- *paramtre* **display_object_name** (optionnel) : Ce paramtre peut tre utilisŽ pour cacher le nom de chaque objet dŽtectŽ dans lÕimage de dŽtection si sa valeur est dŽfinie comme ÔFalseÕ. La valeur par dŽfaut est ÔTrueÕ.


 -- *paramtre* **extract_detected_objects** (optionnel) : ce paramtre peut tre utilisŽ pour extraire et sauvegarder/ retourner chaque objet dŽtectŽ dans une image dans une image sŽparŽe. Sa valeur par dŽfaut est ÔFalseÕ. 

 -- *valeurs renvoyŽes* : Les valeurs renvoyŽes vont dŽpendre des paramtres envoyŽs dans la fonction **detectObjectsFromImage()**. Retrouvez les commentaires et le code ci-dessousÊ:

                
        """
            
Si tous les paramtres nŽcessaires sont dŽfinis et 'output_image_path' est dŽfini vers le chemin o le fichier de dŽtection sera sauvegardŽ, la fonction va renvoyerÊ:
1. un tableau de dictionnaires, avec chaque dictionnaire correspondant aux objets dŽtectŽs dans lÕimage. Chaque dictionnaire a les propriŽtŽs suivantesÊ:
       *Nom (chaine de caractres -- string)
            	 * percentage_probability (float)
	         	 * box_points (tuple de coordonnŽes x1,y1,x2 et y2)

                   """
        detections = detector.detectObjectsFromImage(input_image="image.jpg", output_image_path="imagenew.jpg", minimum_percentage_probability=30)


        """
Si tous les paramtres requis sont dŽfinis et output_type = 'array', la fonction va renvoyer
1. Un tableau Numpy de lÕimage de dŽtection.
2. Un tableau de dictionnaires, avec chaque dictionnaire correspondant aux objets dŽtectŽs dans lÕimage. Chaque dictionnaire contient les propriŽtŽs suivantesÊ:
* Nom (string Ð chaine de caractres)
* percentage_probability (float)
* box_points (tuple de coordonnŽes x1,y1,x2 et y2)

        """
        returned_image, detections = detector.detectObjectsFromImage(input_image="image.jpg", output_type="array", minimum_percentage_probability=30)


        """
	 
            Si extract_detected_objects = True et 'output_image_path' est dŽfini par le chemin vers le lieu de sauvegarde de lÕimage de dŽtection, la fonction renvoieÊ:
1. Un tableau de dictionnaires, chaque dictionnaire correspond aux objets dŽtectŽs dans lÕimage. Chaque dictionnaire contient les propriŽtŽs suivantesÊ:
* Nom (string)
* percentage_probability (float)
* box_points (tuple de coordonnŽes x1,y1,x2 et y2)
2. Un tableau de chaine de caractres reprŽsentant les chemins des images de chaque objet extrait de lÕimage de dŽpart. 

        """
        detections, extracted_objects = detector.detectObjectsFromImage(input_image="image.jpg", output_image_path="imagenew.jpg", extract_detected_objects=True, minimum_percentage_probability=30)


        """
            Si extract_detected_objects = True et output_type = 'array', la fonction va renvoyerÊ:
1. Un tableau Numpy de lÕimage de dŽtection.
2. Un tableau de dictionnaires, avec chaque dictionnaire correspondant aux objets dŽtectŽs dans lÕimage. Chaque dictionnaire contient les propriŽtŽs suivantesÊ:
* nom(string)
* percentage_probability (float)
* box_points (tuple de coordonnŽes x1,y1,x2 et y2)
	3. Un tableau de tableaux Numpy de chaque objet dŽtectŽ dans lÕimage   
        """
        returned_image, detections, extracted_objects = detector.detectObjectsFromImage(input_image="image.jpg", output_type="array", extract_detected_objects=True, minimum_percentage_probability=30)



* **.CustomObjects()** ,CÕest la fonction que vous utiliserez lorsque vous ne voulez faire la dŽtection que dÕun nombre limitŽ dÕobjets. Elle renvoie un dictionnaire dÕobjets et leur valeur ÔTrueÕ ou ÔFalseÕ. Pour dŽtecter les objets sŽlectionnŽs dans une image, vous devrez utiliser les dictionnaires renvoyŽs par cette fonction avec la fonction ** detectCustomObjectsFromImage()** . Retrouvez les dŽtails dans les commentaires et le code ci-dessousÊ::

        
        """
Il yÕa 80 possible objets que vous pouvez dŽtecter avec la classe ObjectDetection, vous pouvez les voir ci-dessous. 

            Person(personne),   bicycle(vŽlo),   car(voiture),   motorcycle(moto),   airplane(avion),
            Bus(bus),   train(train),   truck(camion),   boat(bateau),   traffic light(feu de signalisation),   fire hydrant (bouche dÕincendie),   stop_sign (panneau stop),
            parking meter (parc mtre),   bench (banc),   bird (oiseau),   cat (chat),   dog (chien),   horse (cheval),   sheep (brebis),   cow (vache),   elephant (elephant),   bear (ours),   zebra (zebre),
            giraffe (girafe),   backpack (sac ˆ dos),   umbrella (parapluie),   handbag (sac ˆ main),   tie (cravate),   suitcase (valise),   frisbee (frisbee),   skis (skis),   snowboard (snowboard),
            sports ball(balle de sport),   kite (cerf - volant),   baseball bat (batte de baseball),   baseball glove (gang de baseball),   skateboard (skateboard),   surfboard  (planche de surf),   tennis racket (raquette de tennis),
            bottle (bouteille),   wine glass (verre de vin),   cup (gobelet),   fork (fourchette),   knife (couteau),   spoon (cuillre),   bowl (bolle),   banana (banane),   apple (pomme),   sandwich (sandwich),   orange (orange),
            broccoli (brocoli),   carrot (carotte),   hot dog (hot dog),   pizza (pizza),   donut (beignet),   cake(g‰teau),   chair (chaise),   couch(canape),   potted plant(plante a pot),   bed(lit),
            dining table(table de diner),   toilet(toilette),   tv(tŽlŽvision),   laptop(ordinateur),   mouse(souris),   remote(tŽlŽcommande),   keyboard(clavier),   cell phone(tŽlŽphone portable),   microwave(micro-onde),
            oven  (four),   toaster(grille pain),   sink(Žvier),   refrigerator (rŽfrigŽrateur),   book (cahier),   clock (horloge),   vase(vase) ,   scissors(ciseaux),   teddy bear(ours en peluche),   hair dryer(sche cheveux),
            toothbrush(brosse ˆ dent).

Pour dŽtecter uniquement certains des objets ci-dessus, vous devrez instancier la fonction CustomObjects et dŽfinir le ou les noms des objets que vous voulez dŽtecter. Le reste sera dŽfini ˆ ÔFalseÕ par dŽfaut. Dans lÕexemple ci-dessous, nous dŽtectons uniquement ÔpersonÕ(personne) et ÔdogÕ(chien). 
     
        """
        custom = detector.CustomObjects(person=True, dog=True)


* **.detectCustomObjectsFromImage()**, Cette fonction a tous les paramtres et renvoie toutes les valeurs de la fonction ** detectObjectsFromImage()**, avec une petite diffŽrence. Cette fonction ne fait la dŽtection sur une image que dÕobjets sŽlectionnŽs. Contrairement ˆ la fonction ** detectObjectsFromImage()**, elle a besoin dÕun paramtre supplŽmentaire qui est **custom_objet** qui lui rŽcupre le dictionnaire renvoyŽ par la fonction ** CustomObjects()**. Dans lÕexemple ci-dessous, nous avons dŽfini la fonction de dŽtection pour quÕelle ne reconnaisse queÊles personnes et les chiensÊ:: 

    
    custom = detector.CustomObjects(person=True, dog=True)

    detections = detector.detectCustomObjectsFromImage( custom_objects=custom, input_image=os.path.join(execution_path , "image3.jpg"), output_image_path=os.path.join(execution_path , "image3new-custom.jpg"), minimum_percentage_probability=30)

        

** Exemple de code pour la dŽtection dÕobjets sur Image **

Trouvez ci-dessous un exemple de code pour dŽtecter les objets sur une imageÊ:: 

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

   
