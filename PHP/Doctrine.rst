Doctrine sous symfony
===================

Annotations des entités  : 
---------------------------

::
	/**
	* @ORM\OneToMany(targetEntity="App\Entity\Comment", mappedBy="article")
	* @ORM\OrderBy({"createdAt" = "DESC"})
	*/


	/**
	* @ORM\ManyToOne(targetEntity="App\Entity\Article", inversedBy="comments")
	* @ORM\JoinColumn(nullable=false)
	*/

	/*Modéliser la relation des deux coté*/
	/**
	* @ORM\ManyToMany(targetEntity="App\Entity\Tag", inversedBy="articles")
	*/


	* @ORM\OrderBy({"createdAt" = "DESC"})
	* @ORM\OneToMany(targetEntity="App\Entity\Comment", mappedBy="article")
