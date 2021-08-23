## Repository Exemple



    // find orga from user
    public function findOrgaofUser($OrgaOfUser)
    {
        $qb = $this->createQueryBuilder('p')
            ->where('p.organization = :user ')
            ->setParameter('user', $OrgaOfUser )
        ;
        $query = $qb->getQuery();
        return $query->execute();
    }
