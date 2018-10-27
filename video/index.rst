a.. ImageAI documentation master file, created by
   sphinx-quickstart on Tue Jun 12 06:13:09 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Analyse et détection sur Vidéo et flux vidéo temp réel Vidéo 
==========================================
**ImageAI** fournit un ensemble de classes et de fonctions puissantes et facile à utiliser pour faire de la **Détection et du tracking d’objets dans une Vidéo** et L’**analyse vidéo**. **ImageAI** vous permet d’utiliser ou d’employer tous les algorithmes de pointes d’apprentissage profond tel que **RetinaNet**, **YOLOv3** et **TinyYOLOv3**.
Avec **ImageAI** vous pouvez effectuer des taches de détection et analyser des vidéos et des flux vidéo temps réel à partir des cameras IP et de celle de vos appareils. 
Trouvez ci-dessous les différentes classes et les fonctions respectives mise à votre disposition pour votre utilisation. 
Ces classes peuvent être intégré à tout programme python traditionnel que vous développez, que cela soit un site internet, une application Windows/Linux/MacOS ou un système qui supporte ou fait partie d’un réseau local. 


**======= imageai.Detection.VideoObjectDetection =======**


La classe **VideoObjectDetection** vous fournit des fonctions pour détecter les objets dans une vidéo ou un flux vidéo provenant d’une caméra ou d’une caméra IP en utilisant les modèles **pré-entrainé** à partir de la base de données **COCO**. Les modèles supportes sont **RetinaNet**, **YOLOv3** et **TinyYOLOv3**. Ceci veut dire que vous pouvez détecter et reconnaitre 80 différents types d’objets de la vie de tous les jours dans les vidéos. 
Pour commencer, télécharger un des modèles pré-entrainé que vous voulez utiliser via les liens ci-dessous. 

`Télécharger le modèle RetinaNet - resnet50_coco_best_v2.0.1.h5 <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

` Télécharger le modèle YOLOv3 - yolo.h5 <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

` Télécharger le modèle TinyYOLOv3 -  yolo-tiny.h5 <https://github.com/OlafenwaMoses/ImageAI/releases/tag/1.0 />`_

Une fois que vous avez téléchargé le modèle que vous choisissez d’utiliser, créez une instance de **VideoObjectDetection** comme vous pouvez le voir ci-dessous ::

    
    from imageai.Detection import VideoObjectDetection
    
    detector = VideoObjectDetection()
Une fois que vous avez créé une instance de la classe, vous pouvez appeler les fonctions ci-dessous pour paramétrer ses propriétés et détecter les objets dans une vidéo. 

* **.setModelTypeAsRetinaNet()** , cette fonction établit comme type de modèle pour l’instance de détection d’objets que vous avez créé le modèle
**RetinaNet**, ce qui veut dire que vous accomplirez votre tâche de détection d’objets en utilisant le modèle pré-entrainé **RetinaNet** que vous avez précédemment téléchargé par le lien ci-dessus. Trouvez ci-dessous un exemple de code ::  


    detector.setModelTypeAsRetinaNet()

* **.setModelTypeAsYOLOv3()** , cette fonction établit comme type de modèle pour l’instance de détection d’objets que vous avez créé le modèle
**YOLOv3**, ce qui veut dire que vous accomplirez votre tâche de détection d’objets en utilisant le modèle pré-entrainé **YOLOv3** que vous avez précédemment téléchargé par le lien ci-dessus. Trouvez ci-dessous un exemple de code ::  


    detector.setModelTypeAsYOLOv3()

* **.setModelTypeAsTinyYOLOv3()** , cette fonction établit comme type de modèle pour l’instance de détection d’objets que vous avez créé le modèle
**TinyYOLOv3**, ce qui veut dire que vous accomplirez votre tâche de détection d’objets en utilisant le modèle pré-entrainé **TinyYOLOv3** que vous avez précédemment téléchargé par le lien ci-dessus. Trouvez ci-dessous un exemple de code ::  

    detector.setModelTypeAsTinyYOLOv3()


* **.setModelPath()** , cette fonction accepte une chaine de caractère qui doit être le chemin vers le fichier modèle que vous avez téléchargé et doit correspondre au type de modèle choisi pour votre instance de détection d’objets. Trouver un exemple de code et de paramètres de la fonction ci-dessous ::  

    detector.setModelPath("yolo.h5")

 -- *paramètre* **model_path** (requis) : C’est le chemin vers le fichier modèle téléchargé.  

* **.loadModel()** , Cette fonction charge le modèle à partir du chemin que vous avez spécifié dans l’appel ci-dessus de fonction de votre instance de détection d’objets. Trouver un exemple de code ci-dessous ::

    detector.loadModel()

 -- *paramètre* **detection_speed** (optionnel) : Ce paramètre vous permet de réduire de 80% le temps qu’il faut pour détecter les objets sur une vidéo, ce qui conduira à une légère baisse de la précision. Ce paramètre accepte des valeurs de type chaine de caractères. Les valeurs disponibles sont "normal", "fast", "faster", "fastest" et "flash". La valeur par défaut est ‘normal’. 


* **.detectObjectsFromVideo()** , Il s’agit de la fonction qui accomplit la détection d’objets sur un fichier vidéo ou un flux vidéo direct après que le modèle ait été chargé dans l’instance que vous avez créé. Retrouvez ci-après un exemple de code complet ::


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



 -- *parametre* **input_file_path** (requis si vous ne tenez pas compte de **camera_input**) : Il fait référence au chemin vers le fichier vidéo sur lequel vous voulez faire la détection.

 -- *paramètre* **output_file_path** (requis si **save_detected_video** n’a pas la valeur False) : Il fait référence vers l’emplacement de l’enregistrement du fichier vidéo détecté. Par défaut, cette fonction enregistre les vidéos dans le format  **.avi**. 


 -- *paramètre* **frames_per_second** (optionnel, mais recommandé) : 
Ce paramètre vous permet de définir le nombre de frames par seconde pour la vidéo détectée qui sera enregistrée. Sa valeur par défaut est 20 mais nous recommandons que vous définissiez la valeur qui sied pour votre vidéo ou vidéo-direct.  


 -- *paramètre* **log_progress** (optionnel) : Définir ce paramètre a ‘True’ affiche le progrès de la vidéo ou flux direct pendant qu’il est détecter dans la console. Il fera un rapport sur chaque frame détecté pendant qu’il progresse. La valeur par défaut est ‘False’

 -- *paramètre* **return_detected_frame** (optionnel) : 
Ce paramètre vous permet de retourner le frame détecté comme tableau Numpy pour chaque frame, seconde et minute de la vidéo détectée. Le tableau Numpy retourné sera envoyé respectivement a **per_frame_function**, **per_second_function** et **per_minute_function** (détails ci-dessous)
 

 -- *paramètre* **camera_input** (optionnel) : Ce paramètre peut être assigne en remplacement de **input_file_path** si vous voulez détecter des objets dans le flux vidéo de la caméra. Vous devez instancier la fonction **VideoCapture()** d’ OpenCV et de charger l’objet dans ce paramètre. 

 

    Ci-dessous un exemple complet de code :: 

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



 -- *paramètre* **minimum_percentage_probability** (optionnel) : Ce paramètre est utilisé pour déterminer l’intégrité des résultats de détection. Diminuer la valeur permet d’afficher plus d’objets alors que l’accroitre permet de s’assurer que les objets détectés ont la précision la plus élevée. La valeur par défaut est 50.    


 -- *paramètre* **display_percentage_probability** (optionnel) :  Ce paramètre peut être utilisé pour cacher le pourcentage de probabilité pour chaque objet détecté dans la vidéo détecté si sa valeur est ‘False’. La valeur par défaut est ‘True’. 


 -- *paramètre* **display_object_name** (optionnel) :  Ce paramètre peut être utilise pour cacher le nom de chaque objet détecte dans la vidéo s’il est défini à False. La valeur par défaut est True. 


 -- *paramètre* **save_detected_video** (optionnel) : Ce paramètre peut être utilisé pour sauvegarder ou non la vidéo de détection. Sa valeur par défaut est True.  

 -- *paramètre* **per_frame_function** (optionnel) : Ce paramètre pour permet de transmettre le nom d’une fonction que vous définissez. Puis, pour chaque frame de la vidéo qui est détectée, la fonction sera définie dans le paramètre qui sera exécuté et la donnée analytique de la vidéo sera transmise à la fonction. Les données renvoyées peuvent être visualisées ou enregistrées dans une base de données NoSQL pour une utilisation et visualisation ultérieure.  

    Ci-dessous un exemple complet de code :: 


        """

Ce paramètre vous permet de définir dans une fonction ou vous voulez faire une exécution chaque fois qu’une image de vidéo est détectée. Si ce paramètre est défini par une fonction, après qu’une image de la vidéo soit détectée, la fonction sera exécutée avec les valeurs suivantes en entrée :
* Numéro de position de la frame de la vidéo.
* Un tableau de dictionnaires, avec chaque dictionnaire correspondant à chaque objet détecté. Chaque dictionnaire contient : 'name', 'percentage_probability' et 'box_points'
* Un dictionnaire avec pour clefs le nom de chaque unique objet et le nombre d’instance de chaque objet présent.
* Si return_detected_frame est défini a ‘True’, le tableau Numpy de la frame détectée sera transmis comme quatrième valeur dans la fonction. 

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


Dans l’exemple ci-dessus, chaque image ou frame de la vidéo est traitée et détectée, la fonction va recevoir et renvoyer les données analytiques pour chaque objet détecté dans la frame de la vidéo comme vous pouvez le voir ci-dessous :: 


        Output for each object : [{'box_points': (362, 295, 443, 355), 'name': 'boat', 'percentage_probability': 26.666194200515747}, {'box_points': (319, 245, 386, 296), 'name': 'boat', 'percentage_probability': 30.052968859672546}, {'box_points': (219, 308, 341, 358), 'name': 'boat', 'percentage_probability': 47.46982455253601}, {'box_points': (589, 198, 621, 241), 'name': 'bus', 'percentage_probability': 24.62330162525177}, {'box_points': (519, 181, 583, 263), 'name': 'bus', 'percentage_probability': 27.446213364601135}, {'box_points': (493, 197, 561, 272), 'name': 'bus', 'percentage_probability': 59.81815457344055}, {'box_points': (432, 187, 491, 240), 'name': 'bus', 'percentage_probability': 64.42965269088745}, {'box_points': (157, 225, 220, 255), 'name': 'car', 'percentage_probability': 21.150341629981995}, {'box_points': (324, 249, 377, 293), 'name': 'car', 'percentage_probability': 24.089913070201874}, {'box_points': (152, 275, 260, 327), 'name': 'car', 'percentage_probability': 30.341443419456482}, {'box_points': (433, 198, 485, 244), 'name': 'car', 'percentage_probability': 37.205660343170166}, {'box_points': (184, 226, 233, 260), 'name': 'car', 'percentage_probability': 38.52525353431702}, {'box_points': (3, 296, 134, 359), 'name': 'car', 'percentage_probability': 47.80363142490387}, {'box_points': (357, 302, 439, 359), 'name': 'car', 'percentage_probability': 47.94844686985016}, {'box_points': (481, 266, 546, 314), 'name': 'car', 'percentage_probability': 65.8585786819458}, {'box_points': (597, 269, 624, 318), 'name': 'person', 'percentage_probability': 27.125394344329834}]
 
        Output count for unique objects : {'bus': 4, 'boat': 3, 'person': 1, 'car': 8}

        ------------END OF A FRAME --------------
Ci-dessous est le code complet qui a une fonction qui récupère les données analytiques et les visualise ; ainsi que la frame détectée en temps réel pendant que la vidéo est traitée et analysée ::


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


 -- *paramètre* **per_second_function** (optionnel) : Ce paramètre vous permet de transmettre le nom d’une fonction que vous définissez. Puis, pour chaque seconde de la vidéo qui est détectée, la fonction sera transmise dans le paramètre sera exécutée et les données analytiques de la vidéo seront envoyées dans la fonction. Les données renvoyées peuvent être visualisées ou sauvegardées dans une base de données NoSQL pour une utilisation et visualisation future.  

    Ci-dessous un exemple complet de code :: 

        """
	  Ce paramètre vous permet de transmettre dans une fonction où vous voulez faire une exécuter après que chaque seconde de la vidéo soit détectée.  Si le paramètre est défini comme une fonction, seconde après que le vidéo soit détecté, la fonction sera exécutée avec les valeurs suivantes en argument :

        -- numéro de position du second 
        -- un tableau de dictionnaire dont les clefs sont les numéros de position de chaque frame présente à la dernière seconde, et la valeur de chaque clef est le tableau de chaque frame qui contient les dictionnaires de chaque objet détecté dans la frame.



        -- Un tableau de dictionnaires, avec chaque dictionnaire à chaque frame de la seconde précédente, et les clés pour chaque dictionnaire sont les noms de numéros d’objets uniques détectés dans chaque frame, et les clés sont le nombre d’instances des objets trouvés dans le frame. 

 
        -- Un dictionnaire avec pour clé le nom de chaque unique objet détecté dans toutes les secondes passées, at les valeurs clés sont les moyennes d’instance d’objets trouvés dans toutes les frames contenus dans les secondes passées. 


        -- Si return_detected_frame est défini aa ‘True’, le tableau Numpy du frame de détection sera envoyé comme cinquième paramètre dans la fonction. 

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



Dans l’exemple ci-dessus, chaque seconde dans la vidéo est traitée et détectée, la fonction va recevoir et renvoyer les données analytiques des objets détectés dans la vidéo comme vous pouvez le voir ci-dessous :: 


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

Ci-dessous est le code complet qui a une fonction qui analyse les données analytiques et les visualise, et le frame détecté à la fin de la seconde en temps réel pendant que la vidéo est traitée et analysée : 

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





 -- *paramètre* **per_minute_function** (optionnel) :  Ce paramètre peut être transmis en argument du nom de la fonction que vous définissez. Puis, pour chaque frame de la vidéo qui est détectée, le paramètre qui a été transmis dans la fonction sera interprété et les données analytiques de la vidéo seront transmis à la fonction. Les données retournées sont de même nature que **per_second_function** ; la différence est qu’elle ne tient compte que de tous les frames de la dernière minute de la vidéo. 

    
	Retrouvez une exemple de fonction pour ces paramètres ci-dessous :: 

        def forMinute(minute_number, output_arrays, count_arrays, average_output_count):
            print("MINUTE : ", minute_number)
            print("Array for the outputs of each frame ", output_arrays)
            print("Array for output count for unique objects in each frame : ", count_arrays)
            print("Output average count for unique objects in the last minute: ", average_output_count)
            print("------------END OF A MINUTE --------------")
 


 -- *paramètre* **video_complete_function** (optionnel) :  Ce paramètre peut être transmis en argument d’une fonction que vous définissez. Une fois que tous les frames de la vidéo sont totalement détectés, le paramètre transmis sera interprété et les données analytiques de la vidéo seront transmis à la fonction. Les données retournées ont la même nature que **per_second_function** et **per_minute_function** ; les différences sont qu’aucun index n’est renvoyé et ici tous les frames de la vidéo sont couvertes.  

 
	Retrouvez une exemple de fonction pour ces paramètres ci-dessous :: 
   

        def forFull(output_arrays, count_arrays, average_output_count):
            print("Array for the outputs of each frame ", output_arrays)
            print("Array for output count for unique objects in each frame : ", count_arrays)
            print("Output average count for unique objects in the entire video: ", average_output_count)
            print("------------END OF THE VIDEO --------------")











.. toctree::
   :maxdepth: 2
   :caption: Contents:

   



