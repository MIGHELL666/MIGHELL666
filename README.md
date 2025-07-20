<!--  BANNER INICIAL -->
<img src="https://media1.tenor.com/m/lzHCfSah59oAAAAC/zero-no-tsukaima-saito-hiraga.gif" alt="Banner" width="420"> <img src="https://media1.tenor.com/m/eHsowtlJhaYAAAAd/highschooldxd-issei.gif" alt="Banner" width="420">

<!-- PRESENTACION -->
<h1 align="center">Hola 👋  soy JOSE MIGUEL 💎</h1> 
<!-- REDES SOCIALES -->
<p align="center">
  <a href="https://www.instagram.com/miguelf546/" target="blank"><img align="center" src="https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white" alt=""  /></a>
  </p>


<!-- SOBRE MI -->
<h1 align="center">💻Sobre Mi💻</h1> 
<p align="left">
🎓 Estudiante de INGENIERIA EN TECNOLOGIAS DE LA INFORMACION.

💻 Soy un apasionado por la tecnología, el desarrollo web y la programación. Actualmente, estoy aprendiendo y mejorando mis habilidades.

Aunque aún estoy en formación y tengo poca experiencia profesional, he trabajado en proyectos personales y académicos donde he desarrollado **sistemas funcionales, interfaces atractivas y mecánicas de juego innovadoras**. Siempre busco mejorar mis habilidades, 
aprender nuevas tecnologías y enfrentar desafíos que me ayuden a crecer como desarrollador.
### 🎯 Mis Objetivos  
- 📚 Seguir aprendiendo y fortaleciendo mis conocimientos en desarrollo web y de videojuegos.  
- 💡 Construir proyectos cada vez más complejos y pulidos.  
- 🤝 Colaborar con otros desarrolladores y ampliar mi experiencia en equipo.  

Estoy en constante aprendizaje y con muchas ganas de seguir creciendo en este mundo tecnológico. 🚀  
</p>
<br>


<!-- TECNOLOGIAS CONOCIDAS-->
<h2 >Tecnologías conocidas👨🏻‍💻</h2>
<p align="left">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=discord,vscode,py,pycharm,git,github,js,npm,html,css,cs,mysql,nodejs,figma,blender,linkedin,notion,gmail,visualstudio,unreal,kotlin,androidstudio,linux,mint,apple,windows,powershell&perline=16" /></a>
</p>
<br>




<?php

	function get_num_visitas(){
		//conectar
		$link = mysql_connect('localhost', 'root', '');
		if (!$link) {
			die('Não foi possível conectar: ' . mysql_error());
		}
		
		mysql_select_db("contador");
		$query = "SELECT total " .
				 "FROM `visitas` " .
				 "ORDER BY total ASC LIMIT 1";
		$result = mysql_query($query);
		if (!$result) {
			$message  = 'Invalid query: ' . mysql_error() . "\n";
			$message .= 'Whole query: ' . $query;
			die($message);
		}
		if (mysql_num_rows($result) == 0) {
			echo "No rows found, nothing to print so am exiting";
			exit;
		}
		$row = mysql_fetch_array($result);
		mysql_close($link);
		return $row["total"];
		//fazer consulta
		//retornar total
	}

	function imprime_visitas($contador){
		return "<h1>" . $contador . "</h1>";
	}
	
	function contar_visita(){
		//conectar
		$link = mysql_connect('localhost', 'root', '');
		if (!$link) {
			die('Não foi possível conectar: ' . mysql_error());
		}
		
		mysql_select_db("contador");
		$query = "UPDATE `visitas` " .
				 "SET total = total + 1";
		$result = mysql_query($query);
		if (!$result) {
			$message  = 'Invalid query: ' . mysql_error() . "\n";
			$message .= 'Whole query: ' . $query;
			die($message);
		}
		mysql_close($link);
	}

	contar_visita();
	$contador = get_num_visitas();
	echo imprime_visitas($contador);

?>
