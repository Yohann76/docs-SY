## Quelques script utile avec PHP


Checker une URL avec Curl

    private function checkUrlCurl($link)
    {
        // initialisation de la session
        $ch = curl_init();

        // configuration des options
        curl_setopt($ch, CURLOPT_URL, $link);
        curl_setopt($ch, CURLOPT_HEADER, 0);

        // exécution de la session
        curl_exec($ch);

        $output = curl_exec($ch);
        $code = curl_getinfo($ch,CURLINFO_HTTP_CODE);

        // fermeture des ressources
        curl_close($ch);
        return $code;

    }


Autre script
