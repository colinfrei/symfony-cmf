# Symfony Content Management Framework

## Mission Statement

The Symfony CMF project makes it easier for **developers** to add **CMS functionality** to applications built with the **Symfony2 PHP** framework. Key development principles for the provided **set of bundles** are **scalability**, **usability**, **documentation** and **testing**.


## Links

- GitHub: <https://github.com/symfony-cmf/symfony-cmf>
- Sandbox: <https://github.com/symfony-cmf/cmf-sandbox>
- Web, documentation: <http://cmf.symfony.com/>
- Wiki: <http://github.com/symfony-cmf/symfony-cmf/wiki>
- Issue Tracker: <http://cmf.symfony-project.org/redmine/>
- IRC: irc://freenode/#symfony-cmf
- Users mailing list: <http://groups.google.com/group/symfony-cmf-users>
- Devs mailing list: <http://groups.google.com/group/symfony-cmf-devs>


## Installation

This is the main repository containing all bundles you need for the CMF.

### Prerequisites

You need to install [Doctrine PHPCR ODM](http://github.com/doctrine/phpcr-odm) according to the install instructions.

### Setup

* Add this repository to your vendors
* Make sure to run ```git submodule update --recursive --init``` inside the symfony-cmf folder after each vendor update (we added this to the vendors script)

*app/autoload.php:* Add autoloader entries

    'Symfony\\Cmf'                          => __DIR__.'/../vendor/symfony-cmf/src',
    'Doctrine\\Bundle\\DoctrinePHPCRBundle' => __DIR__.'/../vendor/bundles',
    'Doctrine\\ODM\\PHPCR'                  => __DIR__.'/../vendor/symfony-cmf/vendor/doctrine-phpcr-odm/lib',
    'Jackalope'                             => __DIR__.'/../vendor/symfony-cmf/vendor/doctrine-phpcr-odm/lib/vendor/jackalope/src',
    'PHPCR'                                 => array(
                                                 __DIR__.'/../vendor/symfony-cmf/vendor/doctrine-phpcr-odm/lib/vendor/jackalope/lib/phpcr/src',
                                                 __DIR__.'/../vendor/symfony-cmf/vendor/doctrine-phpcr-odm/lib/vendor/jackalope/lib/phpcr-utils/src',
                                               ),


*app/autoload.php:* Add autoloader entries for the ODM annotations right after the last AnnotationRegistry::registerFile line

    AnnotationRegistry::registerFile(__DIR__.'/../vendor/symfony-cmf/vendor/doctrine-phpcr-odm/lib/Doctrine/ODM/PHPCR/Mapping/Annotations/DoctrineAnnotations.php');

*app/AppKernel.php:* Initialize bundles in the Kernel registerBundle method

    new Doctrine\Bundle\DoctrinePHPCRBundle\DoctrinePHPCRBundle(),
    new Symfony\Cmf\Bundle\CoreBundle\SymfonyCmfCoreBundle(),
    new Symfony\Cmf\Bundle\MultilangContentBundle\SymfonyCmfMultilangContentBundle(),
    new Symfony\Cmf\Bundle\NavigationBundle\SymfonyCmfNavigationBundle(),
    new Symfony\Cmf\Bundle\ContentBundle\SymfonyCmfContentBundle(),
    new Symfony\Cmf\Bundle\ContentBundle\SymfonyCmfMenuBundle(),


#### Menus

The MenuBundle makes use of the KnpMenu library and KnpMenuBundle (see http://github.com/knplabs/KnpMenuBundle for installation and configuration). If you want to use menus you need to add KnpMenu and KnpMenuBundle to your vendors.

Don't forget to add the bundle in app/AppKernel.php:

*app/AppKernel.php:* Initialize bundles in the Kernel registerBundle method

    new Symfony\Cmf\Bundle\MenuBundle\SymfonyCmfMenuBundle(),


