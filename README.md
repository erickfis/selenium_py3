# A python-selenium enabled environment

This image offer an environment ready for running your selenium web scrapper python applications.

It is based on geckodriver, Mozila Firefox and Python 3.9.


## Usage

On your python code:

    from selenium import webdriver
    from selenium.webdriver.firefox.options import Options

    fx_bin = '/usr/bin/firefox-esr'
    driver = webdriver.Firefox(options=options, firefox_binary=fx_bin)

    driver.get('http://www.google.com')

## The Dockerfile

      # base image
      FROM python:3.9-slim-buster

      ## Installing firefox and geckodriver
      RUN apt-get update && apt-get install -yq firefox-esr wget

      # GeckoDriver v0.29.1
      RUN wget -q "https://github.com/mozilla/geckodriver/releases/download/v0.29.1/geckodriver-v0.29.1-linux64.tar.gz" \
          -O /tmp/geckodriver.tgz \
          && tar zxf /tmp/geckodriver.tgz -C /usr/bin/ \
          && rm /tmp/geckodriver.tgz

      # create symlinks to geckodriver (to the PATH)
      RUN ln -s /usr/bin/geckodriver && chmod 777 /usr/bin/geckodriver



# About

- Erick Medeiros Anastacio
- Data Scientist
- erickfis@gmail.com
- [portfolio](https://erickfis.github.io/portfolio/)
- [linkedin](https://www.linkedin.com/in/erick-medeiros-anast%C3%A1cio-15241717/)
