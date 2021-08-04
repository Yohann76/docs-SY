## ASP.net_MVC

##### Platform par Microsoft, ASP est le framework, MVC pour model view controller

[Cours OC](https://openclassrooms.com/fr/courses/1730206-apprenez-asp-net-mvc/1809316-hello-world-mvc)

Introduction
-------------------

Il existe deux logique ASP.NET ( MVC et Webform ) ici nous allons utilisé MVC
Créer un nouveau projet ASP.NET MVC. Rendez-vous dans le menu Fichier et choisissez Nouveau Projet,
puis dans les modèles, choisissez un projet Visual C#/Web de type Application Web ASP.NET
Pour ouvrir un fichier déja existant, ouvrir le projet avec le .sln pour pouvoir executer le code.
Sous visual studio, le code peut etre exécuter avec F5 ( avec debug ) ou ctrl + F5 ( sans débug ).

Les fichiers
-------------------

Le répertoire App_Data est un répertoire où nous pourrons stocker des données, fichiers binaires ou bases de données.
Le répertoire App_Start contient en général la logique de configuration
Le répertoire Controller contiendra en toute logique les contrôleurs qui servent à gérer les actions.
Le répertoire Models, où nous mettrons tout ce qui a rapport avec notre modèle, c’est-à-dire les classes qui interagissent avec les données
Le répertoire Views contiendra toutes les vues de notre application, grosso modo ce qui permettra le rendu de nos pages à base de HTML
Un fichier Global.asax, qui est exécuté au tout début du lancement de l’application et qui nous permettra entre autre de configurer l’application.
Un fichier packages.config que nous pouvons ignorer ,il sert à la configuration des packages nuget
Un autre fichier Web.config (différent de celui présent dans le répertoire Views), bien connu des développeurs ASP.NET WebForms, qui contient des éléments de configuration de l’application.

Les routes
-------------------

Dans le fichier RouteConfig.classes


    routes.MapRoute(
        name: "Default",
        url: "{controller}/{action}/{id}",
        defaults: new { controller = "Home", action = "Index", id = UrlParameter.Optional }
    );

    // Controller = Home pour homecontroller et action = Index, la méthode : public ActionResult Index() { return View(); }
    // par default return la view associé au nom.


Exemple
-------------------


    routes.MapRoute(
        name: "Default",
        url: "{action}/{valeur1}/{valeur2}",
        defaults: new { controller = "Calculateur", action = "Ajouter", valeur1 = 0, valeur2 = 0 }
    );

    public class CalculateurController : Controller
    {
        public string Ajouter(int valeur1, int valeur2)
        {
            int resultat = valeur1 + valeur2;
            return resultat.ToString();
        }
    }


Le Controller
-------------------  


Le Modele
-------------------   
Exemple d'un modéle Category :


    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Web;

    namespace PhotoGalery.Models
    {

        // One
        public class Category
        {
            public string Name { get; set; }
            public int Years { get; set; }
        }

        // Many
        public class Categories
        {
            public List<Category> GetListCategories()
            {
                return new List<Category>
                {
                new Category {  Years = 30, Name = "Nicolas" },
                new Category {  Years = 30, Name = "Delphine" },
                new Category {  Years = 30, Name = "Jérémie" },
                new Category {  Years = 30, Name = "Timéo" }
                };
            }
        }
    }



La View
-------------------


Une vue est sous format .cshtml

Pour écrire du C# dans la view :

            <tr>
                <td>@category.Name</td>
                <td>@category.Years</td>

            </tr>

Info de view ( début de page , titre... ) :

    @{
        Layout = "~/Views/Shared/_Layout.cshtml";
    }

Récupéré des infos :

    La Category @ViewData["Name"] a bien été trouvé et a @ViewData["Years"] ans.
