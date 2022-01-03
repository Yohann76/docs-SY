## Le format JSON


    {
      "squadName": "Super hero squad",
      "homeTown": "Metro City",
      "formed": 2016,
      "secretBase": "Super tower",
      "active": true,
      "members": [
        {
          "name": "Molecule Man",
          "age": 29,
          "secretIdentity": "Dan Jukes",
          "powers": [
            "Radiation resistance",
            "Turning tiny",
            "Radiation blast"
          ]
        },
        {
          "name": "Madame Uppercut",
          "age": 39,
          "secretIdentity": "Jane Wilson",
          "powers": [
            "Million tonne punch",
            "Damage resistance",
            "Superhuman reflexes"
          ]
        },
        {
          "name": "Eternal Flame",
          "age": 1000000,
          "secretIdentity": "Unknown",
          "powers": [
            "Immortality",
            "Heat Immunity",
            "Inferno",
            "Teleportation",
            "Interdimensional travel"
          ]
        }
      ]
    }


en JS :
-----------------------

    superHeroes['members'][1]['powers'][2]


en PHP :
-----------------------

    $json = file_get_contents("cotation_bourse.json");

    var_dump(json_decode($json));

    $parsed_json = json_decode($json);
    $date_jour = $parsed_json->{'response'}->{'features'}->{'date'};
    $heure_cac40 = $parsed_json->{'cotation_bourse'}[0]->{'bourse'}->{'heure'};
    $minute_cac40 = $parsed_json->{'cotation_bourse'}[0]->{'bourse'}->{'minute'};
    $nom_compagnie = $parsed_json->{'cotation_bourse'}[0]->{'total'}->{'compagnie'};
    $cotation_total = $parsed_json->{'cotation_bourse'}[0]->{'total'}->{'cotation'};
    $tendance_total = $parsed_json->{'cotation_bourse'}[0]->{'total'}->{'tendance'};
