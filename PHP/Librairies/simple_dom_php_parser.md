### Le scraping avec PHP

Nous utilisons la librairie [simple_dom_php_parser](https://simplehtmldom.sourceforge.io/) qui permet d'aller voir des url, pour prendre des éléments en masse. 

Les scripts ressemble a ceci : 

<pre>
  <?php

  require_once 'utils/functions.php';
  require_once 'utils/simple_html_dom.php';
  require_once 'utils/export.php';

  require_once 'Models/Company.php';

  //$url = $_POST['post-form'];

  ini_set("memory_limit", "-1"); //16M
  set_time_limit(500000000); 

  $context = stream_context_create(array(
    'http' => array('ignore_errors' => true),
  ));

  /********PREPARE EXPORT  ********************************************/

  $resultsnum = 0;
  $scrapped = 0;
  $emailArray = [];
  $med = 0;
  $companies = [];

  // page 1 to 32 with https://indexa.fr/entreprises/annuaire/tourisme/agences-de-voyage?page=32
  $urlArray = [];

  for ($i = 15; $i <= 20; $i++) {   // 15 a 20
    array_push($urlArray, "https://indexa.fr/entreprises/annuaire/tourisme/agences-de-voyage?page=$i");
  }


  foreach ($urlArray as $urlNow) {


    try { $html = file_get_html($urlNow, false, $context); } catch (Exception $e) { $html = null; }

    if($html != null) {
      $scrapped = $scrapped + 1;
      $items = $html->find('h3 a');
      foreach ($items as $item) {


        $oneAgency =  'https://indexa.fr'.$item->href;
        $oneAgency = file_get_html($oneAgency, false, $context);

        if($oneAgency->find('.business-summary-details-reputation a', 0)){
          $url = $oneAgency->find('.business-summary-details-reputation a', 0)->href;
        }

        $establishmentName = $oneAgency->find('h1',0)->plaintext;
        $mail = containEmailInWebsite($url);
        if($oneAgency->find('.business-summary-details-address a',1)){
          $adresse = $oneAgency->find('.business-summary-details-address a',1)->plaintext;
        }
        $mentionsLégales = VerifyMentions($url);
        $phone = '';


          $company = new Company;
          if ($establishmentName) {
            $company->establishmentName = utf8_encode($establishmentName);
          }

          if ($phone != null) {
            $company->phone = utf8_encode($phone);
          }

          if ($adresse != null) {
            $company->adresse = utf8_encode($adresse);
          }

          if ($url != null) {
            $company->url = $url;
            $company->mentionsLégales = utf8_encode(VerifyMentions($company->url));
          }

          if ($mail != null) {
            if (is_string($mail) == true) {
              if(in_array($mail, $emailArray) == false){
                $company->mail = utf8_encode($mail);
                array_push($emailArray, $mail);
              }
            } elseif (is_array($mail) == true) {
              if(in_array($mail, $emailArray) == false){
                $company->mail = utf8_encode($mail[0]);
                array_push($emailArray, $mail[0]);
              }
            }
          }

          if ($company->url == 'www.clubmed.fr'){
            $med = $med + 1;
          }

          if ($company->url != null && $company->url != 'www.clubmed.fr' && !empty($company->mail)) {
            $resultsnum = $resultsnum + 1;
            var_dump($company);
            array_push($companies, $company);

            // export to CSV // disable next line for export at the end of searching 

            /*
            if ($resultsnum > 4) {
              var_dump(json_encode($companies));
              return jsonToCsv(json_encode($companies));
            }
            */
            unset($company);
          }
      }
    }
  }

  var_dump('item scrapped : ' . $scrapped);
  var_dump('franchise removed : ' . $med);
  jsonToCsv(json_encode($companies));
  
</pre>


Il faut importer la librairie dans le projet, puis nous utilisons les fonctions ( voir documentation )
