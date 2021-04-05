# globalbitcoin.cash

This is the repository for [globalbitcoin.cash](https://globalbitcoin.cash).

Build & Run the Docker Image
----------------------------

In order to build and run the site you need ruby and docker. Then run:

1. `gem install bundler`
2. `bundle install`
3. `rake docker:build`
4. `docker run -d -p 8888:80 globalbitcoincash`

Contributions
-------------

If you want to submit updates to the website make sure you are editing `index.html.erb`. This is the template used to generate all translated html files via `rake translations:build`.

Adding Translations
-------------------

To add translations to the project, use `translations/en.yml` as a template and create a new file for your locale. Then translate all the content inside of the yaml file and send us a pull request.

About Bitcoin Cash
------------------

Bitcoin Cash brings sound money to the world.  Merchants and users are empowered with low fees and reliable confirmations. The future shines brightly with unrestricted growth, global adoption, permissionless innovation, and decentralized development.

All Bitcoin holders as of block 478558 are now owners of Bitcoin Cash. All Bitcoiners are welcome to join the Bitcoin Cash community as we move forward in creating sound money accessible to the whole world.

License
-------

globalbitcoin.cash is released under the terms of the MIT license. See [COPYING](COPYING) for more
information or see https://opensource.org/licenses/MIT.
