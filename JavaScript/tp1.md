# TP 1 

Dans le formulaire suivant, nous souhaitons passer la connexion en AJAX pour faire des vérifications sur les données de l'utilisateur. 


* Le `ajax_login.php` doit être appelé depuis un script AJAX.
* Les deux champs ne doivent pas être vides.
* Le champ de login est un mail, vous devrez vérifier _via_ une regexp que le mail est valide
* Si un des champs est vide, il doit y avoir un message du type `Le champs login est vide` ; si les deux champs sont vides, il doit y avoir deux messages (dans `span.error`). 
* En cas de champ vide, il doit avoir une bordure rouge pour montrer rapidement à l'utilisateur où est l'erreur. 
* Si tout est correct, l'utilisateur sera redirigé sur https://www.google.fr


```html 

<style type="text/css">
	span.error {
		color : red;
	}
</style>

<span class="error"></span>
<form method="POST">
	<input type="text" name="login">
	<input type="text" name="password">
	<button type="submit">Connecter</button>
</form>
```


```php
<?php

// ajax_login.php

session_start(); 
header('Content-Type: application/json');
if(!empty($_POST['login']) && $_POST['login'] == 'root@toor.us' && !empty($_POST['password']) && $_POST['password'] == 'toor'){
	$_SESSION['connected'] = true; 
	echo json_encode(['connected' => 'true']);
} else {
	echo json_encode(['connected' => 'false']);
}

```

Vous pouvez lancer un serveur php en ligne de commande via la commande `php -S localhost` en étant dans votre dossier contenant le fichier php ([doc](http://php.net/manual/fr/features.commandline.webserver.php)). 
