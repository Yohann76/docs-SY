CSV in array ( un service pour mettre un CSV en tableau dans symfony, le service comprend le chemin du fichier, a mettre dans service.yml )
==========


    <?php
    /**
     * User: Yohann Durand
     * Date: 30/07/2021
     * Time: 17:13
     */

    // src/Service/CSVReadRiskMeasure.php
    namespace App\Service;

    use App\Entity\Risk;
    use App\Entity\SecurityMeasure;
    use App\Repository\RiskRepository;
    use App\Repository\SecurityMeasureRepository;
    use App\Service\Csv\CsvConvertToArray;
    use Doctrine\ORM\EntityManagerInterface;
    use Symfony\Component\Security\Core\Security;
    use Symfony\Component\HttpFoundation\Response;
    use Symfony\Component\DependencyInjection\ParameterBag\ContainerBagInterface;
    use Symfony\Component\HttpClient\HttpClient;
    use Symfony\Component\HttpClient\ScopingHttpClient;
    use Symfony\Component\Serializer\Serializer;
    use Symfony\Component\Serializer\Encoder\CsvEncoder;
    use Symfony\Component\Serializer\Encoder\XmlEncoder;
    use Symfony\Component\Serializer\Encoder\YamlEncoder;
    use Symfony\Component\Serializer\Normalizer\ObjectNormalizer;

    class CSVReadRiskMeasure
    {

        private $entityManager;
        private $containerBag;
        private $createAction;
        private $data_csv_directory;
        private $riskRepository;
        private $securityMeasureRepository;

        public function __construct($data_csv_directory,CreateAction $createAction,SecurityMeasureRepository $securityMeasureRepository,RiskRepository $riskRepository,Security $security,EntityManagerInterface $entityManager,ContainerBagInterface $containerBag)
        {
            $this->entityManager = $entityManager;
            $this->security = $security;
            $this->containerBag = $containerBag;
            $this->data_csv_directory = $data_csv_directory;
            $this->riskRepository = $riskRepository;
            $this->securityMeasureRepository = $securityMeasureRepository;
            $this->createAction = $createAction;
        }

        /*  
        * get riskMeasureNotification.csv in /Data
        * serializer : decode CSV in Array
        */
        public function getCSV()
        {
            // data_csv_directory is defined in service.yml
            $file = $this->data_csv_directory . 'riskMeasureNotification.csv';

            $fileExtension = pathinfo($file, PATHINFO_EXTENSION) ; // get extension file

            $normalizers = [new ObjectNormalizer()];  // for tab

            $encoders = [
                new CsvEncoder(),new XmlEncoder(), new YamlEncoder()

            ] ; // for object

            $serializer = new Serializer($normalizers,$encoders);

            /** @var string $fileString */
            $fileString = file_get_contents($file);

            $data = $serializer->decode($fileString, $fileExtension);

            return $data;
            // $data = tab

        }
    }


in service.yml :

    parameters:
        # article
        img_article_directory: '%kernel.project_dir%/public/article/img'
        data_csv_directory: '%kernel.project_dir%/data/'

        App\Service\CSVReadRiskMeasure:
            arguments:
                # article
                $data_csv_directory: '%data_csv_directory%'
