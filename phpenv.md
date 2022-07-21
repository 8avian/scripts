## Install PHP with phpenv on macOS
*source https://blog.daskepon.com/install-php-with-phpenv-on-macos/*

```bash
# install phpenv
git clone https://github.com/madumlao/phpenv.git ~/.phpenv

# install php-build
git clone https://github.com/php-build/php-build.git ~/.phpenv/plugins/php-build

# install libraries
brew install re2c openssl bison libxml2 autoconf automake icu4c libjpeg libpng libmcrypt libzip

# update bash_profile
# phpenv
export PATH="/usr/local/opt/bison/bin:$PATH"
export PHPENV_ROOT="$HOME/.phpenv"
export PATH="$PHPENV_ROOT/bin:$PATH"
eval "$(phpenv init -)"

# load .bash_profile
source ~/.bash_profile
```

### PHP 8.1.8 build
```bash
PHP_BUILD_CONFIGURE_OPTS="--with-bz2=/usr/local/opt/bzip2 --with-iconv=/usr/local/opt/libiconv" phpenv install -v 8.1.8
```

### PHP 7.4.26 build
```bash
OPENSSL_CFLAGS="-I/usr/local/Cellar/openssl@1.1/1.1.1q/include" OPENSSL_LIBS="-L/usr/local/Cellar/openssl@1.1/1.1.1q/lib -lssl -lcrypto" PHP_BUILD_CONFIGURE_OPTS="\
  --with-bz2=$(brew --prefix bzip2) \
  --with-curl=$(brew --prefix curl) \
  --with-gettext=$(brew --prefix gettext) \
  --with-gmp=$(brew --prefix gmp) \
  --with-iconv=$(brew --prefix libiconv) \
  --with-icu-dir=$(brew --prefix icu4c) \
  --with-jpeg-dir=$(brew --prefix jpeg) \
  --with-libedit=$(brew --prefix libedit) \
  --with-libxml-dir=$(brew --prefix libxml2) \
  --with-libzip=$(brew --prefix libzip)
  --with-mcrypt=$(brew --prefix libmcrypt) \
  --with-png-dir=$(brew --prefix libpng) \
  --with-readline=$(brew --prefix readline) \
  --with-tidy=$(brew --prefix tidy-html5) \
  --with-xsl=$(brew --prefix libxslt) \
  --with-zlib=$(brew --prefix zlib) \
  --with-openssl=$(brew --prefix openssl@1.1)" phpenv install -v 7.4.26
  ```
