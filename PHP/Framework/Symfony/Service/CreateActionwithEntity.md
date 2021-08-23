## Create action ( un service pour implémenter directement des infos en bdd)



    <?php
    // src/Service/Upload.php
    namespace App\Service;

    use Symfony\Component\HttpFoundation\File\Exception\FileException;
    use Symfony\Component\HttpFoundation\File\UploadedFile;
    use App\Entity\Notification;
    use App\Entity\User;
    use App\Repository\NotificationRepository;
    use App\Repository\OrganizationRepository;
    use App\Repository\UserRepository;
    use DateTime;
    use Doctrine\ORM\EntityManagerInterface;
    use Symfony\Component\Security\Core\Security;

    class CreateAction
    {
        private $entityManager;
        private $notificationRepository;

        public function __construct(Security $security,EntityManagerInterface $entityManager,NotificationRepository $notificationRepository)
        {
            $this->entityManager = $entityManager;
            $this->security = $security;
            $this->notificationRepository = $notificationRepository;
        }

        // addAction (content,$forUser,emergency)
        public function addAction($content,$forUser,$emergency)
        {

            $action = new Notification();

            // get current user logged with security component
            $user = $this->security->getUser();

            $action->setFromUser($user);

            // argument function
            $action->setContent($content);
            $action->setUser($forUser);

            $action->setAxisCompliance("test");

            $action->setEmergency($emergency);

            $action->setStatus("A faire");
            $action->setCreatedAt(new DateTime() );

            $this->entityManager->persist($action);
            $this->entityManager->flush();

        }
    }
