Command
===================
`Console Commands`_


Crée une commande
--------------------------------
::

    // src/Command/CreateUserCommand.php
    namespace App\Command;

    use Symfony\Component\Console\Command\Command;
    use Symfony\Component\Console\Input\InputInterface;
    use Symfony\Component\Console\Output\OutputInterface;

    class CreateUserCommand extends Command
    {
        // the name of the command (the part after "bin/console")
        protected static $defaultName = 'app:create-user';

        protected function configure()
        {
            // ...
        }

        protected function execute(InputInterface $input, OutputInterface $output)
        {
            // ...

            return 0;
        }
    }




.. _`Console Commands`: https://symfony.com/doc/current/console.html#the-console-app-env-app-debug
