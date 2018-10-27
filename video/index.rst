a.. ImageAI documentation master file, created by
   sphinx-quickstart on Tue Jun 12 06:13:09 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Analyse et d�tection sur Vid�o et flux vid�o temp r�el Vid�o 
==========================================
**ImageAI** fournit un ensemble de classes et de fonctions puissantes et facile � utiliser pour faire de la **D�tection et du tracking d�objets dans une Vid�o** et L�**analyse vid�o**. **ImageAI** vous permet d�utiliser ou d�employer tous les algorithmes de pointes d�apprentissage profond tel que **RetinaNet**, **YOLOv3** et **TinyYOLOv3**.
Avec **ImageAI** vous pouvez effectuer des taches de d�tection et analyser des vid�os et des flux vid�o temps r�el � partir des cameras IP et de celle de vos appareils. 
Trouvez ci-dessous les diff�rentes classes et les fonctions respectives mise � votre disposition pour votre utilisation. 
Ces classes peuvent �tre int�gr� � tout programme python traditionnel que vous d�veloppez, que cela soit un site internet, une application Windows/Linux/MacOS ou un syst�me qui supporte ou fait partie d�un r�seau local. 


**======= imageai.Detection.VideoObjectDetection =======**


La classe **VideoObjectDetection** vous fournit des fonctions pour d�tecter les objets dans une vid�o ou un flux vid�o provenant d�une cam�ra ou d�une cam�ra IP en utilisant les mod�les **pr�-entrain�** � partir de la base de donn�es **COCO**. Les mod�les supportes sont **RetinaNet**, **YOLOv3** et **TinyYOLOv3**. Ceci veut dire que vous pouvez d�tecter et reconnaitre 80 diff�rents types d�objets de la vie de tous les jours dans les vid�os. 
Pour commencer, t�l�charger un des mod�les pr�-entrain� que vous voulez utiliser via les liens ci-dessous. 

`T�l�charger le mod�le RetinaNet - resnet50_coco_best_v2.0.1.h5 <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

` T�l�charger le mod�le YOLOv3 - yolo.h5 <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

` T�l�charger le mod�le TinyYOLOv3 -  yolo-tiny.h5 <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

Une fois que vous avez t�l�charg� le mod�le que vous choisissez d�utiliser, cr�ez une instance de **VideoObjectDetection** comme vous pouvez le voir ci-dessous�::

    
    from imageai.Detection import VideoObjectDetection
    
    detector = VideoObjectDetection()
Une fois que vous avez cr�� une instance de la classe, vous pouvez appeler les fonctions ci-dessous pour param�trer ses propri�t�s et d�tecter les objets dans une vid�o. 

* **.setModelTypeAsRetinaNet()** , cette fonction �tablit comme type de mod�le pour l�instance de d�tection d�objets que vous avez cr�� le mod�le
**RetinaNet**, ce qui veut dire que vous accomplirez votre t�che de d�tection d�objets en utilisant le mod�le pr�-entrain� **RetinaNet** que vous avez pr�c�demment t�l�charg� par le lien ci-dessus. Trouvez ci-dessous un exemple de code�::  


    detector.setModelTypeAsRetinaNet()

* **.setModelTypeAsYOLOv3()** , cette fonction �tablit comme type de mod�le pour l�instance de d�tection d�objets que vous avez cr�� le mod�le
**YOLOv3**, ce qui veut dire que vous accomplirez votre t�che de d�tection d�objets en utilisant le mod�le pr�-entrain� **YOLOv3** que vous avez pr�c�demment t�l�charg� par le lien ci-dessus. Trouvez ci-dessous un exemple de code�::  


    detector.setModelTypeAsYOLOv3()

* **.setModelTypeAsTinyYOLOv3()** , cette fonction �tablit comme type de mod�le pour l�instance de d�tection d�objets que vous avez cr�� le mod�le
**TinyYOLOv3**, ce qui veut dire que vous accomplirez votre t�che de d�tection d�objets en utilisant le mod�le pr�-entrain� **TinyYOLOv3** que vous avez pr�c�demment t�l�charg� par le lien ci-dessus. Trouvez ci-dessous un exemple de code�::  

    detector.setModelTypeAsTinyYOLOv3()


* **.setModelPath()** , cette fonction accepte une chaine de caract�re qui doit �tre le chemin vers le fichier mod�le que vous avez t�l�charg� et doit correspondre au type de mod�le choisi pour votre instance de d�tection d�objets. Trouver un exemple de code et de param�tres de la fonction ci-dessous�::  

    detector.setModelPath("yolo.h5")

 -- *param�tre* **model_path** (requis) : C�est le chemin vers le fichier mod�le t�l�charg�.  

* **.loadModel()** , Cette fonction charge le mod�le � partir du chemin que vous avez sp�cifi� dans l�appel ci-dessus de fonction de votre instance de d�tection d�objets. Trouver un exemple de code ci-dessous�::

    detector.loadModel()

 -- *param�tre* **detection_speed** (optionnel) : Ce param�tre vous permet de r�duire de 80% le temps qu�il faut pour d�tecter les objets sur une vid�o, ce qui conduira � une l�g�re baisse de la pr�cision. Ce param�tre accepte des valeurs de type chaine de caract�res. Les valeurs disponibles sont "normal", "fast", "faster", "fastest" et "flash". La valeur par d�faut est��normal�. 


* **.detectObjectsFromVideo()** , Il s�agit de la fonction qui accomplit la d�tection d�objets sur un fichier vid�o ou un flux vid�o direct apr�s que le mod�le ait �t� charg� dans l�instance que vous avez cr��. Retrouvez ci-apr�s un exemple de code complet�::


    from imageai.Detection import VideoObjectDetection
    import os

    execution_path = os.getcwd()

    detector = VideoObjectDetection()
    detector.setModelTypeAsYOLOv3()
    detector.setModelPath( os.path.join(execution_path , "yolo.h5"))
    detector.loadModel()

    video_path = detector.detectObjectsFromVideo(input_file_path=os.path.join(execution_path, "traffic.mp4"),
                                output_file_path=os.path.join(execution_path, "traffic_detected")
                                , frames_per_second=20, log_progress=True)
    print(video_path)



 -- *parametre* **input_file_path** (requis si vous ne tenez pas compte de **camera_input**) : Il fait r�f�rence au chemin vers le fichier vid�o sur lequel vous voulez faire la d�tection.

 -- *param�tre* **output_file_path** (requis si **save_detected_video** n�a pas la valeur False) : Il fait r�f�rence vers l�emplacement de l�enregistrement du fichier vid�o d�tect�. Par d�faut, cette fonction enregistre les vid�os dans le format  **.avi**. 


 -- *param�tre* **frames_per_second** (optionnel, mais recommand�) : 
Ce param�tre vous permet de d�finir le nombre de frames par seconde pour la vid�o d�tect�e qui sera enregistr�e. Sa valeur par d�faut est 20 mais nous recommandons que vous d�finissiez la valeur qui sied pour votre vid�o ou vid�o-direct.  


 -- *param�tre* **log_progress** (optionnel) : D�finir ce param�tre a �True� affiche le progr�s de la vid�o ou flux direct pendant qu�il est d�tecter dans la console. Il fera un rapport sur chaque frame d�tect� pendant qu�il progresse. La valeur par d�faut est �False�

 -- *param�tre* **return_detected_frame** (optionnel) : 
Ce param�tre vous permet de retourner le frame d�tect� comme tableau Numpy pour chaque frame, seconde et minute de la vid�o d�tect�e. Le tableau Numpy retourn� sera envoy� respectivement a **per_frame_function**, **per_second_function** et **per_minute_function** (d�tails ci-dessous)
 

 -- *param�tre* **camera_input** (optionnel) : Ce param�tre peut �tre assigne en remplacement de **input_file_path** si vous voulez d�tecter des objets dans le flux vid�o de la cam�ra. Vous devez instancier la fonction **VideoCapture()** d� OpenCV et de charger l�objet dans ce param�tre. 

 

    Ci-dessous un exemple complet de code�:: 

        from imageai.Detection import VideoObjectDetection
        import os
        import cv2

        execution_path = os.getcwd()

        camera = cv2.VideoCapture(0)

        detector = VideoObjectDetection()
        detector.setModelTypeAsYOLOv3()
        detector.setModelPath(os.path.join(execution_path , "yolo.h5"))
        detector.loadModel()

        video_path = detector.detectObjectsFromVideo(camera_input=camera,
            output_file_path=os.path.join(execution_path, "camera_detected_video") 
            , frames_per_second=20, log_progress=True, minimum_percentage_probability=30)

        print(video_path)



 -- *param�tre* **minimum_percentage_probability** (optionnel) : Ce param�tre est utilis� pour d�terminer l�int�grit� des r�sultats de d�tection. Diminuer la valeur permet d�afficher plus d�objets alors que l�accroitre permet de s�assurer que les objets d�tect�s ont la pr�cision la plus �lev�e. La valeur par d�faut est 50.    


 -- *param�tre* **display_percentage_probability** (optionnel) :  Ce param�tre peut �tre utilis� pour cacher le pourcentage de probabilit� pour chaque objet d�tect� dans la vid�o d�tect� si sa valeur est �False�. La valeur par d�faut est �True�. 


 -- *param�tre* **display_object_name** (optionnel) :  Ce param�tre peut �tre utilise pour cacher le nom de chaque objet d�tecte dans la vid�o s�il est d�fini � False. La valeur par d�faut est True. 


 -- *param�tre* **save_detected_video** (optionnel) : Ce param�tre peut �tre utilis� pour sauvegarder ou non la vid�o de d�tection. Sa valeur par d�faut est True.  

 -- *param�tre* **per_frame_function** (optionnel) : Ce param�tre pour permet de transmettre le nom d�une fonction que vous d�finissez. Puis, pour chaque frame de la vid�o qui est d�tect�e, la fonction sera d�finie dans le param�tre qui sera ex�cut� et la donn�e analytique de la vid�o sera transmise � la fonction. Les donn�es renvoy�es peuvent �tre visualis�es ou enregistr�es dans une base de donn�es NoSQL pour une utilisation et visualisation ult�rieure.  

    Ci-dessous un exemple complet de code�:: 


        """

Ce param�tre vous permet de d�finir dans une fonction ou vous voulez faire une ex�cution chaque fois qu�une image de vid�o est d�tect�e. Si ce param�tre est d�fini par une fonction, apr�s qu�une image de la vid�o soit d�tect�e, la fonction sera ex�cut�e avec les valeurs suivantes en entr�e�:
* Num�ro de position de la frame de la vid�o.
* Un tableau de dictionnaires, avec chaque dictionnaire correspondant � chaque objet d�tect�. Chaque dictionnaire contient�: 'name', 'percentage_probability' et 'box_points'
* Un dictionnaire avec pour clefs le nom de chaque unique objet et le nombre d�instance de chaque objet pr�sent.
* Si return_detected_frame est d�fini a �True�, le tableau Numpy de la frame d�tect�e sera transmis comme quatri�me valeur dans la fonction. 

                """

        from imageai.Detection import VideoObjectDetection
        import os


        def forFrame(frame_number, output_array, output_count):
        print("FOR FRAME " , frame_number)
        print("Output for each object : ", output_array)
        print("Output count for unique objects : ", output_count)
        print("------------END OF A FRAME --------------")


        video_detector = VideoObjectDetection()
        video_detector.setModelTypeAsYOLOv3()
        video_detector.setModelPath(os.path.join(execution_path, "yolo.h5"))
        video_detector.loadModel()


        video_detector.detectObjectsFromVideo(input_file_path=os.path.join(execution_path, "traffic.mp4"), output_file_path=os.path.join(execution_path, "video_frame_analysis") ,  frames_per_second=20, per_frame_function=forFrame,  minimum_percentage_probability=30)


Dans l�exemple ci-dessus, chaque image ou frame de la vid�o est trait�e et d�tect�e, la fonction va recevoir et renvoyer les donn�es analytiques pour chaque objet d�tect� dans la frame de la vid�o comme vous pouvez le voir ci-dessous�:: 


        Output for each object : [{'box_points': (362, 295, 443, 355), 'name': 'boat', 'percentage_probability': 26.666194200515747}, {'box_points': (319, 245, 386, 296), 'name': 'boat', 'percentage_probability': 30.052968859672546}, {'box_points': (219, 308, 341, 358), 'name': 'boat', 'percentage_probability': 47.46982455253601}, {'box_points': (589, 198, 621, 241), 'name': 'bus', 'percentage_probability': 24.62330162525177}, {'box_points': (519, 181, 583, 263), 'name': 'bus', 'percentage_probability': 27.446213364601135}, {'box_points': (493, 197, 561, 272), 'name': 'bus', 'percentage_probability': 59.81815457344055}, {'box_points': (432, 187, 491, 240), 'name': 'bus', 'percentage_probability': 64.42965269088745}, {'box_points': (157, 225, 220, 255), 'name': 'car', 'percentage_probability': 21.150341629981995}, {'box_points': (324, 249, 377, 293), 'name': 'car', 'percentage_probability': 24.089913070201874}, {'box_points': (152, 275, 260, 327), 'name': 'car', 'percentage_probability': 30.341443419456482}, {'box_points': (433, 198, 485, 244), 'name': 'car', 'percentage_probability': 37.205660343170166}, {'box_points': (184, 226, 233, 260), 'name': 'car', 'percentage_probability': 38.52525353431702}, {'box_points': (3, 296, 134, 359), 'name': 'car', 'percentage_probability': 47.80363142490387}, {'box_points': (357, 302, 439, 359), 'name': 'car', 'percentage_probability': 47.94844686985016}, {'box_points': (481, 266, 546, 314), 'name': 'car', 'percentage_probability': 65.8585786819458}, {'box_points': (597, 269, 624, 318), 'name': 'person', 'percentage_probability': 27.125394344329834}]
 
        Output count for unique objects : {'bus': 4, 'boat': 3, 'person': 1, 'car': 8}

        ------------END OF A FRAME --------------
Ci-dessous est le code complet qui a une fonction qui r�cup�re les donn�es analytiques et les visualise�; ainsi que la frame d�tect�e en temps r�el pendant que la vid�o est trait�e et analys�e�::


        from imageai.Detection import VideoObjectDetection
        import os
        from matplotlib import pyplot as plt


        execution_path = os.getcwd()

        color_index = {'bus': 'red', 'handbag': 'steelblue', 'giraffe': 'orange', 'spoon': 'gray', 'cup': 'yellow', 'chair': 'green', 'elephant': 'pink', 'truck': 'indigo', 'motorcycle': 'azure', 'refrigerator': 'gold', 'keyboard': 'violet', 'cow': 'magenta', 'mouse': 'crimson', 'sports ball': 'raspberry', 'horse': 'maroon', 'cat': 'orchid', 'boat': 'slateblue', 'hot dog': 'navy', 'apple': 'cobalt', 'parking meter': 'aliceblue', 'sandwich': 'skyblue', 'skis': 'deepskyblue', 'microwave': 'peacock', 'knife': 'cadetblue', 'baseball bat': 'cyan', 'oven': 'lightcyan', 'carrot': 'coldgrey', 'scissors': 'seagreen', 'sheep': 'deepgreen', 'toothbrush': 'cobaltgreen', 'fire hydrant': 'limegreen', 'remote': 'forestgreen', 'bicycle': 'olivedrab', 'toilet': 'ivory', 'tv': 'khaki', 'skateboard': 'palegoldenrod', 'train': 'cornsilk', 'zebra': 'wheat', 'tie': 'burlywood', 'orange': 'melon', 'bird': 'bisque', 'dining table': 'chocolate', 'hair drier': 'sandybrown', 'cell phone': 'sienna', 'sink': 'coral', 'bench': 'salmon', 'bottle': 'brown', 'car': 'silver', 'bowl': 'maroon', 'tennis racket': 'palevilotered', 'airplane': 'lavenderblush', 'pizza': 'hotpink', 'umbrella': 'deeppink', 'bear': 'plum', 'fork': 'purple', 'laptop': 'indigo', 'vase': 'mediumpurple', 'baseball glove': 'slateblue', 'traffic light': 'mediumblue', 'bed': 'navy', 'broccoli': 'royalblue', 'backpack': 'slategray', 'snowboard': 'skyblue', 'kite': 'cadetblue', 'teddy bear': 'peacock', 'clock': 'lightcyan', 'wine glass': 'teal', 'frisbee': 'aquamarine', 'donut': 'mincream', 'suitcase': 'seagreen', 'dog': 'springgreen', 'banana': 'emeraldgreen', 'person': 'honeydew', 'surfboard': 'palegreen', 'cake': 'sapgreen', 'book': 'lawngreen', 'potted plant': 'greenyellow', 'toaster': 'ivory', 'stop sign': 'beige', 'couch': 'khaki'}


        resized = False

        def forFrame(frame_number, output_array, output_count, returned_frame):

            plt.clf()

            this_colors = []
            labels = []
            sizes = []

            counter = 0

            for eachItem in output_count:
                counter += 1
                labels.append(eachItem + " = " + str(output_count[eachItem]))
                sizes.append(output_count[eachItem])
                this_colors.append(color_index[eachItem])

            global resized

            if (resized == False):
                manager = plt.get_current_fig_manager()
                manager.resize(width=1000, height=500)
                resized = True

            plt.subplot(1, 2, 1)
            plt.title("Frame : " + str(frame_number))
            plt.axis("off")
            plt.imshow(returned_frame, interpolation="none")

            plt.subplot(1, 2, 2)
            plt.title("Analysis: " + str(frame_number))
            plt.pie(sizes, labels=labels, colors=this_colors, shadow=True, startangle=140, autopct="%1.1f%%")

            plt.pause(0.01)



        video_detector = VideoObjectDetection()
        video_detector.setModelTypeAsYOLOv3()
        video_detector.setModelPath(os.path.join(execution_path, "yolo.h5"))
        video_detector.loadModel()

        plt.show()

        video_detector.detectObjectsFromVideo(input_file_path=os.path.join(execution_path, "traffic.mp4"), output_file_path=os.path.join(execution_path, "video_frame_analysis") ,  frames_per_second=20, per_frame_function=forFrame,  minimum_percentage_probability=30, return_detected_frame=True)


 -- *param�tre* **per_second_function** (optionnel) : Ce param�tre vous permet de transmettre le nom d�une fonction que vous d�finissez. Puis, pour chaque seconde de la vid�o qui est d�tect�e, la fonction sera transmise dans le param�tre sera ex�cut�e et les donn�es analytiques de la vid�o seront envoy�es dans la fonction. Les donn�es renvoy�es peuvent �tre visualis�es ou sauvegard�es dans une base de donn�es NoSQL pour une utilisation et visualisation future.  

    Ci-dessous un exemple complet de code�:: 

        """
	  Ce param�tre vous permet de transmettre dans une fonction o� vous voulez faire une ex�cuter apr�s que chaque seconde de la vid�o soit d�tect�e.  Si le param�tre est d�fini comme une fonction, seconde apr�s que le vid�o soit d�tect�, la fonction sera ex�cut�e avec les valeurs suivantes en argument�:

        -- num�ro de position du second 
        -- un tableau de dictionnaire dont les clefs sont les num�ros de position de chaque frame pr�sente � la derni�re seconde, et la valeur de chaque clef est le tableau de chaque frame qui contient les dictionnaires de chaque objet d�tect� dans la frame.



        -- Un tableau de dictionnaires, avec chaque dictionnaire � chaque frame de la seconde pr�c�dente, et les cl�s pour chaque dictionnaire sont les noms de num�ros d�objets uniques d�tect�s dans chaque frame, et les cl�s sont le nombre d�instances des objets trouv�s dans le frame. 

 
        -- Un dictionnaire avec pour cl� le nom de chaque unique objet d�tect� dans toutes les secondes pass�es, at les valeurs cl�s sont les moyennes d�instance d�objets trouv�s dans toutes les frames contenus dans les secondes pass�es. 


        -- Si return_detected_frame est d�fini aa �True�, le tableau Numpy du frame de d�tection sera envoy� comme cinqui�me param�tre dans la fonction. 

        """

        from imageai.Detection import VideoObjectDetection
        import os


        def forSeconds(second_number, output_arrays, count_arrays, average_output_count):
            print("SECOND : ", second_number)
            print("Array for the outputs of each frame ", output_arrays)
            print("Array for output count for unique objects in each frame : ", count_arrays)
            print("Output average count for unique objects in the last second: ", average_output_count)
            print("------------END OF A SECOND --------------")


        video_detector = VideoObjectDetection()
        video_detector.setModelTypeAsYOLOv3()
        video_detector.setModelPath(os.path.join(execution_path, "yolo.h5"))
        video_detector.loadModel()


        video_detector.detectObjectsFromVideo(input_file_path=os.path.join(execution_path, "traffic.mp4"), output_file_path=os.path.join(execution_path, "video_second_analysis") ,  frames_per_second=20, per_second_function=forSecond,  minimum_percentage_probability=30)



Dans l�exemple ci-dessus, chaque seconde dans la vid�o est trait�e et d�tect�e, la fonction va recevoir et renvoyer les donn�es analytiques des objets d�tect�s dans la vid�o comme vous pouvez le voir ci-dessous�:: 


        Array for the outputs of each frame [[{'box_points': (362, 295, 443, 355), 'name': 'boat', 'percentage_probability': 26.666194200515747}, {'box_points': (319, 245, 386, 296), 'name': 'boat', 'percentage_probability': 30.052968859672546}, {'box_points': (219, 308, 341, 358), 'name': 'boat', 'percentage_probability': 47.46982455253601}, {'box_points': (589, 198, 621, 241), 'name': 'bus', 'percentage_probability': 24.62330162525177}, {'box_points': (519, 181, 583, 263), 'name': 'bus', 'percentage_probability': 27.446213364601135}, {'box_points': (493, 197, 561, 272), 'name': 'bus', 'percentage_probability': 59.81815457344055}, {'box_points': (432, 187, 491, 240), 'name': 'bus', 'percentage_probability': 64.42965269088745}, {'box_points': (157, 225, 220, 255), 'name': 'car', 'percentage_probability': 21.150341629981995}, {'box_points': (324, 249, 377, 293), 'name': 'car', 'percentage_probability': 24.089913070201874}, {'box_points': (152, 275, 260, 327), 'name': 'car', 'percentage_probability': 30.341443419456482}, {'box_points': (433, 198, 485, 244), 'name': 'car', 'percentage_probability': 37.205660343170166}, {'box_points': (184, 226, 233, 260), 'name': 'car', 'percentage_probability': 38.52525353431702}, {'box_points': (3, 296, 134, 359), 'name': 'car', 'percentage_probability': 47.80363142490387}, {'box_points': (357, 302, 439, 359), 'name': 'car', 'percentage_probability': 47.94844686985016}, {'box_points': (481, 266, 546, 314), 'name': 'car', 'percentage_probability': 65.8585786819458}, {'box_points': (597, 269, 624, 318), 'name': 'person', 'percentage_probability': 27.125394344329834}],
            [{'box_points': (316, 240, 384, 302), 'name': 'boat', 'percentage_probability': 29.594269394874573}, {'box_points': (361, 295, 441, 354), 'name': 'boat', 'percentage_probability': 36.11513376235962}, {'box_points': (216, 305, 340, 357), 'name': 'boat', 'percentage_probability': 44.89373862743378}, {'box_points': (432, 198, 488, 244), 'name': 'truck', 'percentage_probability': 22.914741933345795}, {'box_points': (589, 199, 623, 240), 'name': 'bus', 'percentage_probability': 20.545457303524017}, {'box_points': (519, 182, 583, 263), 'name': 'bus', 'percentage_probability': 24.467085301876068}, {'box_points': (492, 197, 563, 271), 'name': 'bus', 'percentage_probability': 61.112016439437866}, {'box_points': (433, 188, 490, 241), 'name': 'bus', 'percentage_probability': 65.08989334106445}, {'box_points': (352, 303, 442, 357), 'name': 'car', 'percentage_probability': 20.025095343589783}, {'box_points': (136, 172, 188, 195), 'name': 'car', 'percentage_probability': 21.571354568004608}, {'box_points': (152, 276, 261, 326), 'name': 'car', 'percentage_probability': 33.07966589927673}, {'box_points': (181, 225, 230, 256), 'name': 'car', 'percentage_probability': 35.111838579177856}, {'box_points': (432, 198, 488, 244), 'name': 'car', 'percentage_probability': 36.25282347202301}, {'box_points': (3, 292, 130, 360), 'name': 'car', 'percentage_probability': 67.55480170249939}, {'box_points': (479, 265, 546, 314), 'name': 'car', 'percentage_probability': 71.47912979125977}, {'box_points': (597, 269, 625, 318), 'name': 'person', 'percentage_probability': 25.903674960136414}],................, 
            [{'box_points': (133, 250, 187, 278), 'name': 'umbrella', 'percentage_probability': 21.518094837665558}, {'box_points': (154, 233, 218, 259), 'name': 'umbrella', 'percentage_probability': 23.687003552913666}, {'box_points': (348, 311, 425, 360), 'name': 'boat', 'percentage_probability': 21.015766263008118}, {'box_points': (11, 164, 137, 225), 'name': 'bus', 'percentage_probability': 32.20453858375549}, {'box_points': (424, 187, 485, 243), 'name': 'bus', 'percentage_probability': 38.043853640556335}, {'box_points': (496, 186, 570, 264), 'name': 'bus', 'percentage_probability': 63.83994221687317}, {'box_points': (588, 197, 622, 240), 'name': 'car', 'percentage_probability': 23.51653128862381}, {'box_points': (58, 268, 111, 303), 'name': 'car', 'percentage_probability': 24.538707733154297}, {'box_points': (2, 246, 72, 301), 'name': 'car', 'percentage_probability': 28.433072566986084}, {'box_points': (472, 273, 539, 323), 'name': 'car', 'percentage_probability': 87.17672824859619}, {'box_points': (597, 270, 626, 317), 'name': 'person', 'percentage_probability': 27.459821105003357}]
            ]
 
        Array for output count for unique objects in each frame : [{'bus': 4, 'boat': 3, 'person': 1, 'car': 8},
            {'truck': 1, 'bus': 4, 'boat': 3, 'person': 1, 'car': 7},
            {'bus': 5, 'boat': 2, 'person': 1, 'car': 5},
            {'bus': 5, 'boat': 1, 'person': 1, 'car': 9},
            {'truck': 1, 'bus': 2, 'car': 6, 'person': 1},
            {'truck': 2, 'bus': 4, 'boat': 2, 'person': 1, 'car': 7},
            {'truck': 1, 'bus': 3, 'car': 7, 'person': 1, 'umbrella': 1},
            {'bus': 4, 'car': 7, 'person': 1, 'umbrella': 2},
            {'bus': 3, 'car': 6, 'boat': 1, 'person': 1, 'umbrella': 3},
            {'bus': 3, 'car': 4, 'boat': 1, 'person': 1, 'umbrella': 2}]
 
        Output average count for unique objects in the last second: {'truck': 0.5, 'bus': 3.7, 'umbrella': 0.8, 'boat': 1.3, 'person': 1.0, 'car': 6.6}

        ------------END OF A SECOND --------------

Ci-dessous est le code complet qui a une fonction qui analyse les donn�es analytiques et les visualise, et le frame d�tect� �la fin de la seconde en temps r�el pendant que la vid�o est trait�e et analys�e : 

        from imageai.Detection import VideoObjectDetection
        import os
        from matplotlib import pyplot as plt


        execution_path = os.getcwd()

        color_index = {'bus': 'red', 'handbag': 'steelblue', 'giraffe': 'orange', 'spoon': 'gray', 'cup': 'yellow', 'chair': 'green', 'elephant': 'pink', 'truck': 'indigo', 'motorcycle': 'azure', 'refrigerator': 'gold', 'keyboard': 'violet', 'cow': 'magenta', 'mouse': 'crimson', 'sports ball': 'raspberry', 'horse': 'maroon', 'cat': 'orchid', 'boat': 'slateblue', 'hot dog': 'navy', 'apple': 'cobalt', 'parking meter': 'aliceblue', 'sandwich': 'skyblue', 'skis': 'deepskyblue', 'microwave': 'peacock', 'knife': 'cadetblue', 'baseball bat': 'cyan', 'oven': 'lightcyan', 'carrot': 'coldgrey', 'scissors': 'seagreen', 'sheep': 'deepgreen', 'toothbrush': 'cobaltgreen', 'fire hydrant': 'limegreen', 'remote': 'forestgreen', 'bicycle': 'olivedrab', 'toilet': 'ivory', 'tv': 'khaki', 'skateboard': 'palegoldenrod', 'train': 'cornsilk', 'zebra': 'wheat', 'tie': 'burlywood', 'orange': 'melon', 'bird': 'bisque', 'dining table': 'chocolate', 'hair drier': 'sandybrown', 'cell phone': 'sienna', 'sink': 'coral', 'bench': 'salmon', 'bottle': 'brown', 'car': 'silver', 'bowl': 'maroon', 'tennis racket': 'palevilotered', 'airplane': 'lavenderblush', 'pizza': 'hotpink', 'umbrella': 'deeppink', 'bear': 'plum', 'fork': 'purple', 'laptop': 'indigo', 'vase': 'mediumpurple', 'baseball glove': 'slateblue', 'traffic light': 'mediumblue', 'bed': 'navy', 'broccoli': 'royalblue', 'backpack': 'slategray', 'snowboard': 'skyblue', 'kite': 'cadetblue', 'teddy bear': 'peacock', 'clock': 'lightcyan', 'wine glass': 'teal', 'frisbee': 'aquamarine', 'donut': 'mincream', 'suitcase': 'seagreen', 'dog': 'springgreen', 'banana': 'emeraldgreen', 'person': 'honeydew', 'surfboard': 'palegreen', 'cake': 'sapgreen', 'book': 'lawngreen', 'potted plant': 'greenyellow', 'toaster': 'ivory', 'stop sign': 'beige', 'couch': 'khaki'}


        resized = False

        def forSecond(frame2_number, output_arrays, count_arrays, average_count, returned_frame):

            plt.clf()

            this_colors = []
            labels = []
            sizes = []

            counter = 0

            for eachItem in average_count:
                counter += 1
                labels.append(eachItem + " = " + str(average_count[eachItem]))
                sizes.append(average_count[eachItem])
                this_colors.append(color_index[eachItem])

            global resized

            if (resized == False):
                manager = plt.get_current_fig_manager()
                manager.resize(width=1000, height=500)
                resized = True

            plt.subplot(1, 2, 1)
            plt.title("Second : " + str(frame_number))
            plt.axis("off")
            plt.imshow(returned_frame, interpolation="none")

            plt.subplot(1, 2, 2)
            plt.title("Analysis: " + str(frame_number))
            plt.pie(sizes, labels=labels, colors=this_colors, shadow=True, startangle=140, autopct="%1.1f%%")

            plt.pause(0.01)



        video_detector = VideoObjectDetection()
        video_detector.setModelTypeAsYOLOv3()
        video_detector.setModelPath(os.path.join(execution_path, "yolo.h5"))
        video_detector.loadModel()

        plt.show()

        video_detector.detectObjectsFromVideo(input_file_path=os.path.join(execution_path, "traffic.mp4"), output_file_path=os.path.join(execution_path, "video_second_analysis") ,  frames_per_second=20, per_second_function=forSecond,  minimum_percentage_probability=30, return_detected_frame=True, log_progress=True)





 -- *param�tre* **per_minute_function** (optionnel) :  Ce param�tre peut �tre transmis en argument du nom de la fonction que vous d�finissez. Puis, pour chaque frame de la vid�o qui est d�tect�e, le param�tre qui a �t� transmis dans la fonction sera interpr�t� et les donn�es analytiques de la vid�o seront transmis � la fonction. Les donn�es retourn�es sont de m�me nature que **per_second_function**�; la diff�rence est qu�elle ne tient compte que de tous les frames de la derni�re minute de la vid�o. 

    
	Retrouvez une exemple de fonction pour ces param�tres ci-dessous�:: 

        def forMinute(minute_number, output_arrays, count_arrays, average_output_count):
            print("MINUTE : ", minute_number)
            print("Array for the outputs of each frame ", output_arrays)
            print("Array for output count for unique objects in each frame : ", count_arrays)
            print("Output average count for unique objects in the last minute: ", average_output_count)
            print("------------END OF A MINUTE --------------")
 


 -- *param�tre* **video_complete_function** (optionnel) :  Ce param�tre peut �tre transmis en argument d�une fonction que vous d�finissez. Une fois que tous les frames de la vid�o sont totalement d�tect�s, le param�tre transmis sera interpr�t� et les donn�es analytiques de la vid�o seront transmis � la fonction. Les donn�es retourn�es ont la m�me nature que **per_second_function** et **per_minute_function**�; les diff�rences sont qu�aucun index n�est renvoy� et ici tous les frames de la vid�o sont couvertes.  

 
	Retrouvez une exemple de fonction pour ces param�tres ci-dessous�:: 
   

        def forFull(output_arrays, count_arrays, average_output_count):
            print("Array for the outputs of each frame ", output_arrays)
            print("Array for output count for unique objects in each frame : ", count_arrays)
            print("Output average count for unique objects in the entire video: ", average_output_count)
            print("------------END OF THE VIDEO --------------")











.. toctree::
   :maxdepth: 2
   :caption: Contents:

   



