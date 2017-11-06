# cmd

### jQuery keypress enter
$(document).keypress(function(event){

	var keycode = (event.keyCode ? event.keyCode : event.which);
	if(keycode == '13'){
    $( ".hack" ).toggle();

	}

});

### Récupérer les données d'un fichier JSON - Démonstration sur fichier html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Todolist</title>
  </head>
  <body>
<div id="result" style="color:red"></div>

  </body>
  <script src="./js/jquery.min.js"></script>
  <script>
  var getJSON = function(url) {
  return new Promise(function(resolve, reject) {
    var xhr = new XMLHttpRequest();
    xhr.open('get', url, true);
    xhr.responseType = 'json';
    xhr.onload = function() {
      var status = xhr.status;
      if (status == 200) {
        resolve(xhr.response);
      } else {
        reject(status);
      }
    };
    xhr.send();
  });
};

getJSON('./json/fr.json').then(function(data) {
    alert('Your Json result is:  ' + data.prenom); //you can comment this, i used it to debug

    result.innerText = data.prenom; //display the result in an HTML element
}, function(status) { //error detection....
  alert('Something went wrong.');
});

  </script>
</html>
