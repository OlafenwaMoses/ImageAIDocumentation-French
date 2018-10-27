.. ImageAI documentation master file, created by
   sphinx-quickstart on Tue Jun 12 06:13:09 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Les Classes de detection
=================
**ImageAI** fournit un ensemble de classes et fonctions puissantes et faciles � utiliser pour la **D�tection et Extraction d�objets dans une image**.
**ImageAI** vous permet d�utiliser les algorithmes de pointe en apprentissage profond tel que **RetinaNet**, **YOLOv3** et **TinyYOLOv3**. Avec **ImageAI** vous pouvez accomplir des taches de d�tection et d�analyse d�images. 
Trouvez ci-dessous les classes et leurs fonctions respectives mise � votre disposition pour votre utilisation. Ces classes peuvent �tre int�gr�es dans tout programme Python traditionnel que vous d�veloppez ; que ce soit un site internet, une application Windows/Linux/MacOS ou un syst�me qui supporte ou fait partir d�un r�seau local.   



**======= imageai.Detection.ObjectDetection =======**


Cette classe **ObjectDetection** vous fournit les fonctions pour accomplir la d�tection d�objets sur une image ou un ensemble d�images, utilisant les mod�les **pr�-entraines** sur la base de donn�es **COCO**.  
Les mod�les support�s sont **RetinaNet**, **YOLOv3** et **TinyYOLOv3**.
Ceci veut dire que vous pouvez d�tecter et reconnaitre 80 diff�rents types communs d�objets de tous les jours. Pour commencer, t�l�charger n�importe quel mod�le que vous voulez utiliser via les liens ci-dessous�:  


`T�l�charger le mod�le RetinaNet - resnet50_coco_best_v2.0.1.h5 <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

`T�l�charger le mod�le YOLOv3 - yolo.h5 <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

`T�l�charger le mod�le TinyYOLOv3 - yolo-tiny.h5 <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

Une fois que vous avez t�l�charger le mod�le de votre choix, vous devez cr�er une instance de la classe **ObjectDetection** comme dans l�exemple ci-dessous�::



    from imageai.Detection import ObjectDetection
    
    detector = ObjectDetection()

Une fois que vois vous avez cr�� une instance de la classe, vous pouvez utiliser les fonctions ci-dessous pour choisir convenablement les propri�t�s d�instance et de commencer la d�tection d�objets sur les images. 


* **.setModelTypeAsRetinaNet()** , cette fonction �tablit comme type de mod�le pour l�instance de d�tection d�objets que vous avez cr�� le mod�le **RetinaNet**, ceci veut dire que vous accomplirez la tache de d�tection d�objets � l�aide de mod�le pr�-entrain� de **RetinaNet** que vous avez t�l�charg� par les liens ci-dessus. Trouvez un exemple de code ci-dessous�:: 

    detector.setModelTypeAsRetinaNet()

* **.setModelTypeAsYOLOv3()** , cette fonction �tablit comme type de mod�le pour l�instance de d�tection d�objets que vous avez cr�� le mod�le **YOLOv3**, ceci veut dire que vous accomplirez la tache de d�tection d�objets � l�aide de mod�le pr�-entrain� de **YOLOv3** que vous avez t�l�charg� par les liens ci-dessus. Trouvez un exemple de code ci-dessous�:: 

    detector.setModelTypeAsYOLOv3()

* **.setModelTypeAsTinyYOLOv3()** , cette fonction �tablit comme type de mod�le pour l�instance de d�tection d�objets que vous avez cr�� le mod�le **TinyYOLOv3**, ceci veut dire que vous accomplirez la tache de d�tection d�objets � l�aide de mod�le pr�-entrain� de **TinyYOLOv3** que vous avez t�l�charg� par les liens ci-dessus. Trouvez un exemple de code ci-dessous�:: 

    detector.setModelTypeAsTinyYOLOv3()


* **.setModelPath()** , Cette fonction prend en argument une chaine de caract�res qui doit �tre le chemin vers le fichier mod�le que vous avez t�l�charg� et doit correspondre au type de mod�le choisi pour votre instance de d�tection d�objets. Trouvez un exemple de code et de param�tres de fonction ci-dessous : 

    detector.setModelPath("yolo.h5")

 -- *param�tre* **model_path** (requis) : c�est le chemin vers votre mod�le t�l�charg�. 

* **.loadModel()** ,  Cette fonction charge le mod�le � partir du chemin que vous avez sp�cifi� dans l�appel de fonction ci-dessus de votre instance de d�tection d�objets. Trouver un exemple de code ci-dessous�::

    detector.loadModel()

 -- *param�tre* **detection_speed** (optionnel) : Ce param�tre vous permet de r�duire jusquՈ 80% le temps qu�il faut pour d�tecter les objets sur une image ce qui conduit � une l�g�re r�duction de la pr�cision. Ce param�tre accepte des valeurs de type chaines de caract�res. Les valeurs disponibles sont **normal**, **fast**, **faster**, **fastest** et **flash**. La valeur par d�faut est **normal**


* **.detectObjectsFromImage()** ,C�est la fonction qui accomplit la d�tection d�objets apr�s que le mod�le ait �t� charg�. Elle peut �tre appel�e plusieurs fois pour d�tecter les objets dans plusieurs images. Trouvez un exemple de code ci-dessous�::

 
    detections = detector.detectObjectsFromImage(input_image="image.jpg", output_image_path="imagenew.jpg", minimum_percentage_probability=30)

 -- *param�tre* **input_image** (requis) : Il fait r�f�rence au chemin vers le fichier image sur lequel vous voulez faire la d�tection. Ce param�tre peut �tre le tableau **Numpy** ou le fichier flux de l�image si vous donner la valeur "array" ou "stream" au param�tre **input_type**.


 -- *param�tre* **output_image_path** (requis seulement si **input_type** = "file" ) : Il fait r�f�rence au chemin vers le lieu de sauvegarde de l�image d�tect�e ou d�tection. Il n�est requis que si **input_type** = "file".



 -- *param�tre* **minimum_percentage_probability** (optionnel) : Ce param�tre est utilis� pour d�terminer l�int�grit� des r�sultats de d�tections. R�duire cette valeur permettra de d�tecter plus d�objets alors que l�augmenter permet d�avoir des objets d�tect�s avec la plus grande pr�cision. La valeur par d�faut est 50. 


 -- *param�tre* **output_type** (optionnel) : ce param�tre permet de d�finir le format dans lequel l�image de d�tections sera produit. Les valeurs disponibles sont �file�(fichier) et �array�(tableau). La valeur par d�faut est �file�.  Si ce param�tre est d�finit comme �array�, la fonction va renvoyer un tableau Numpy pour l�image de d�tection. Retrouvez un exemple ci-dessous�::  


     returned_image, detections = detector.detectObjectsFromImage(input_image="image.jpg", output_type="array", minimum_percentage_probability=30)

 -- *param�tre* **display_percentage_probability** (optionnel) : Ce param�tre peut �tre utilis� pour cacher le pourcentage de probabilit� de chaque objet d�tect� dans l�image de d�tect�e si sa valeur est d�finie � �False�. La valeur par d�faut est �True�. 

 -- *param�tre* **display_object_name** (optionnel) : Ce param�tre peut �tre utilis� pour cacher le nom de chaque objet d�tect� dans l�image de d�tection si sa valeur est d�finie comme �False�. La valeur par d�faut est �True�.


 -- *param�tre* **extract_detected_objects** (optionnel) : ce param�tre peut �tre utilis� pour extraire et sauvegarder/ retourner chaque objet d�tect� dans une image dans une image s�par�e. Sa valeur par d�faut est �False�. 

 -- *valeurs renvoy�es* : Les valeurs renvoy�es vont d�pendre des param�tres envoy�s dans la fonction **detectObjectsFromImage()**. Retrouvez les commentaires et le code ci-dessous�:

                
        """
            
Si tous les param�tres n�cessaires sont d�finis et 'output_image_path' est d�fini vers le chemin o� le fichier de d�tection sera sauvegard�, la fonction va renvoyer�:
1. un tableau de dictionnaires, avec chaque dictionnaire correspondant aux objets d�tect�s dans l�image. Chaque dictionnaire a les propri�t�s suivantes�:
       *Nom (chaine de caract�res -- string)
            	 * percentage_probability (float)
	         	 * box_points (tuple de coordonn�es x1,y1,x2 et y2)

                   """
        detections = detector.detectObjectsFromImage(input_image="image.jpg", output_image_path="imagenew.jpg", minimum_percentage_probability=30)


        """
Si tous les param�tres requis sont d�finis et output_type = 'array', la fonction va renvoyer
1. Un tableau Numpy de l�image de d�tection.
2. Un tableau de dictionnaires, avec chaque dictionnaire correspondant aux objets d�tect�s dans l�image. Chaque dictionnaire contient les propri�t�s suivantes�:
* Nom (string � chaine de caract�res)
* percentage_probability (float)
* box_points (tuple de coordonn�es x1,y1,x2 et y2)

        """
        returned_image, detections = detector.detectObjectsFromImage(input_image="image.jpg", output_type="array", minimum_percentage_probability=30)


        """
	 
            Si extract_detected_objects = True et 'output_image_path' est d�fini par le chemin vers le lieu de sauvegarde de l�image de d�tection, la fonction renvoie�:
1. Un tableau de dictionnaires, chaque dictionnaire correspond aux objets d�tect�s dans l�image. Chaque dictionnaire contient les propri�t�s suivantes�:
* Nom (string)
* percentage_probability (float)
* box_points (tuple de coordonn�es x1,y1,x2 et y2)
2. Un tableau de chaine de caract�res repr�sentant les chemins des images de chaque objet extrait de l�image de d�part. 

        """
        detections, extracted_objects = detector.detectObjectsFromImage(input_image="image.jpg", output_image_path="imagenew.jpg", extract_detected_objects=True, minimum_percentage_probability=30)


        """
            Si extract_detected_objects = True et output_type = 'array', la fonction va renvoyer�:
1. Un tableau Numpy de l�image de d�tection.
2. Un tableau de dictionnaires, avec chaque dictionnaire correspondant aux objets d�tect�s dans l�image. Chaque dictionnaire contient les propri�t�s suivantes�:
* nom(string)
* percentage_probability (float)
* box_points (tuple de coordonn�es x1,y1,x2 et y2)
	3. Un tableau de tableaux Numpy de chaque objet d�tect� dans l�image   
        """
        returned_image, detections, extracted_objects = detector.detectObjectsFromImage(input_image="image.jpg", output_type="array", extract_detected_objects=True, minimum_percentage_probability=30)



* **.CustomObjects()** ,C�est la fonction que vous utiliserez lorsque vous ne voulez faire la d�tection que d�un nombre limit� d�objets. Elle renvoie un dictionnaire d�objets et leur valeur �True� ou �False�. Pour d�tecter les objets s�lectionn�s dans une image, vous devrez utiliser les dictionnaires renvoy�s par cette fonction avec la fonction ** detectCustomObjectsFromImage()** . Retrouvez les d�tails dans les commentaires et le code ci-dessous�::

        
        """
Il y�a 80 possible objets que vous pouvez d�tecter avec la classe ObjectDetection, vous pouvez les voir ci-dessous. 

            Person(personne),   bicycle(v�lo),   car(voiture),   motorcycle(moto),   airplane(avion),
            Bus(bus),   train(train),   truck(camion),   boat(bateau),   traffic light(feu de signalisation),   fire hydrant (bouche d�incendie),   stop_sign (panneau stop),
            parking meter (parc m�tre),   bench (banc),   bird (oiseau),   cat (chat),   dog (chien),   horse (cheval),   sheep (brebis),   cow (vache),   elephant (elephant),   bear (ours),   zebra (zebre),
            giraffe (girafe),   backpack (sac � dos),   umbrella (parapluie),   handbag (sac � main),   tie (cravate),   suitcase (valise),   frisbee (frisbee),   skis (skis),   snowboard (snowboard),
            sports ball(balle de sport),   kite (cerf - volant),   baseball bat (batte de baseball),   baseball glove (gang de baseball),   skateboard (skateboard),   surfboard  (planche de surf),   tennis racket (raquette de tennis),
            bottle (bouteille),   wine glass (verre de vin),   cup (gobelet),   fork (fourchette),   knife (couteau),   spoon (cuill�re),   bowl (bolle),   banana (banane),   apple (pomme),   sandwich (sandwich),   orange (orange),
            broccoli (brocoli),   carrot (carotte),   hot dog (hot dog),   pizza (pizza),   donut (beignet),   cake(g�teau),   chair (chaise),   couch(canape),   potted plant(plante a pot),   bed(lit),
            dining table(table de diner),   toilet(toilette),   tv(t�l�vision),   laptop(ordinateur),   mouse(souris),   remote(t�l�commande),   keyboard(clavier),   cell phone(t�l�phone portable),   microwave(micro-onde),
            oven  (four),   toaster(grille pain),   sink(�vier),   refrigerator (r�frig�rateur),   book (cahier),   clock (horloge),   vase(vase) ,   scissors(ciseaux),   teddy bear(ours en peluche),   hair dryer(s�che cheveux),
            toothbrush(brosse � dent).

Pour d�tecter uniquement certains des objets ci-dessus, vous devrez instancier la fonction CustomObjects et d�finir le ou les noms des objets que vous voulez d�tecter. Le reste sera d�fini � �False� par d�faut. Dans l�exemple ci-dessous, nous d�tectons uniquement �person�(personne) et �dog�(chien). 
     
        """
        custom = detector.CustomObjects(person=True, dog=True)


* **.detectCustomObjectsFromImage()**, Cette fonction a tous les param�tres et renvoie toutes les valeurs de la fonction ** detectObjectsFromImage()**, avec une petite diff�rence. Cette fonction ne fait la d�tection sur une image que d�objets s�lectionn�s. Contrairement � la fonction ** detectObjectsFromImage()**, elle a besoin d�un param�tre suppl�mentaire qui est **custom_objet** qui lui r�cup�re le dictionnaire renvoy� par la fonction ** CustomObjects()**. Dans l�exemple ci-dessous, nous avons d�fini la fonction de d�tection pour qu�elle ne reconnaisse que�les personnes et les chiens�:: 

    
    custom = detector.CustomObjects(person=True, dog=True)

    detections = detector.detectCustomObjectsFromImage( custom_objects=custom, input_image=os.path.join(execution_path , "image3.jpg"), output_image_path=os.path.join(execution_path , "image3new-custom.jpg"), minimum_percentage_probability=30)

        

** Exemple de code pour la d�tection d�objets sur Image **

Trouvez ci-dessous un exemple de code pour d�tecter les objets sur une image�:: 

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

   
