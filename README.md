<!DOCTYPE html>
<html>
    <head>
        <title>Campus Cameras</title>
    </head>
    <body>
        <h1>BYU Campus Cameras</h1>
        <?php
        
            //Creating a class in order to make the program more efficient
            
            class camera {
                public $id;
                public $name;
                public $description;
                public $refresh;
                public $location;
                
                //constructor function
                
                public function __construct($id,$name,$description,$refresh,$location){
                    $this->id = $id;
                    $this->name = $name;
                    $this->description = $description;
                    $this->refresh = $refresh;
                    $this->location = $location;
                }
                
                //this function is used to add the data from the website in an array to easily print it out in a list
                
                public function addToArray(){
                    array_push($id_array, $this->id);
                    array_push($name_array, $this->name);
                    array_push($description_array, $this->description);
                    array_push($refresh_array, $this->refresh);
                    array_push($location_array, $this->location);
                }
            }
            
            //this code is used to grab the data from the source URL
            
            $content = file_get_contents('https://soaregistry.byu.edu/services/campusInformation/webcam/v1/streams/');
            $i=0;
            $id_array = array();
            $name_array = array();
            $description_array = array();
            $refresh_array = array();
            $location_array = array();
            
            //creating new instances of the camera class
            
            $cam1 = new camera("testing", "Testing Center", "Testing Center Line Conditions", 15, "https://ws.byu.edu/services/cameras/rest/v1/streams/testing");
            $cam2 = new camera("timp-esc", "Mt. Timpanogos (from ESC)", "", 5, "https://ws.byu.edu/services/cameras/rest/v1/streams/timp-esc");
            $cam3 = new camera("daily-universe", "Daily Universe Camera", "", 60, "https://ws.byu.edu/services/cameras/rest/v1/streams/daily-universe");
            $cam4 = new camera("broadcasting-sw", "Broadcasting Building (SW)", "", 5, "https://ws.byu.edu/services/cameras/rest/v1/streams/broadcasting-sw");
            $cam5 = new camera("student-fitness", "Student Fitness Center", "See how busy the fitness center is", 5, "https://ws.byu.edu/services/cameras/rest/v1/streams/student-fitness");
            
            //adding the data from the instances into arrays
            
            $cam1 -> addToArray();
            $cam2 -> addToArray();
            $cam3 -> addToArray();
            $cam4 -> addToArray();
            $cam5 -> addToArray();
            
            //this while loop will print out the data from the URL into a list
            
            while ($i < 5) {
                echo $id_array[$i] . " " . $name_array[$i] . " " . $description_array[$i] . " " . $refresh_array[$i] . " " . $location_array[$i] "<br>";
                $i++;
            }
            
        ?>
    </body>


</html>
