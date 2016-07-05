# Sylius Order Association Bundle

This bundle adds a command to generate product associations from existing orders to Sylius e-commerce platform. Those
associations can be used to show a **"Customers Who Bought This Item Also Bought"** section.

---

## Installation

  1. require the bundle with Composer:

  ```bash
  $ composer require webburza/sylius-order-association-bundle
  ```

  2. enable the bundle in `app/AppKernel.php`:

  ```php
  public function registerBundles()
  {
    $bundles = array(
      // ...
      new \Webburza\Sylius\OrderAssociationBundle\WebburzaSyliusOrderAssociationBundle(),
      // ...
    );
  }
  ```

  3. Configure a limit for associations per product. This way you can associate only the most often bought together
  products to each product. To configure the limit add this to your `app/config/config.yml`:

  ```yaml
  webburza_sylius_order_association:
      association_limit: 5
  ```

  4. This bundle adds a console command that either generates or updates associations for all products. You should run
  it initially to generate associations and after that periodically to update them. It will create a new association
  type and use it for all generated associations.

  ```bash
  $ app/console webburza:sylius-order-association:generate
  ```

  If the command is behaving unusually or if you want more information on what it's doing, add a verbosity flag (-v)

  You can also specify the association limit via an option when you run the command.

    ```bash
    $ app/console webburza:sylius-order-association:generate --limit=5
    ```

## License

This bundle is available under the [MIT license](LICENSE).

## To-do

- Tests
