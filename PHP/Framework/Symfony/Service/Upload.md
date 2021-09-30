## Service upload

Avec $targetImgArticle défini dans le service.yml ( pour avoir le chemin de l'upload )

    <?php
    // src/Service/Upload.php
    namespace App\Service;

    use Symfony\Component\HttpFoundation\File\Exception\FileException;
    use Symfony\Component\HttpFoundation\File\UploadedFile;

    class Upload
    {

        private $targetImgArticle;

        public function __construct($targetImgArticle)
        {
            $this->targetImgArticle = $targetImgArticle;
        }


        // for article picture
        public function uploadImgArticle(UploadedFile $file)
        {
            $originalFilename = pathinfo($file->getClientOriginalName(), PATHINFO_FILENAME);
            $safeFilename = transliterator_transliterate('Any-Latin; Latin-ASCII; [^A-Za-z0-9_] remove; Lower()', $originalFilename);
            $fileName = $safeFilename.'-'.uniqid().'.'.$file->guessExtension();

            try {
                $file->move($this->getTargetImgArticle(), $fileName);
            } catch (FileException $e) {
                // ... handle exception if something happens during file upload
            }

            return $fileName;
        }

        public function getTargetImgArticle()
        {
            // defined in config/services.yaml
            return $this->targetImgArticle;
        }
    }
