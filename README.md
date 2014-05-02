#Presentation
Portia is an awesome open source new web-scraping tool based on scrapy for easy and visual data mining of structured data in web pages.

* Article: [http://blog.scrapinghub.com/2014/04/01/announcing-portia/][1]
* Github project: [https://github.com/scrapinghub/portia][2]

##How to use it
- If you run it directly, it will start the Portia server on port 9001
- You can also run it with bash to take the contents of a scraping located at /opt/portia/slyd/data/projects

### Future improvements
- Add openssh-server to the init script to allow ssh access.

##Dockerfile

This docker contains all the packages neccesary to run portia on it's default settings

	# Select Fedora as base image
	FROM fedora

	MAINTAINER Mario Castro mariocaster@gmail.com

	# Install required dependencies and GIT to clone portia project
	RUN yum install -y --nogpgcheck gcc 
	RUN yum install -y --nogpgcheck python
	RUN yum install -y --nogpgcheck git
	RUN yum install -y --nogpgcheck python-pip 
	RUN yum install -y --nogpgcheck python-devel 
	RUN yum install -y --nogpgcheck twisted python-twisted-runner 
	RUN yum install -y --nogpgcheck python-lxml

	# Install required Portia package
	RUN pip install virtualenv
	RUN pip install loginform
	RUN pip install jsonschema
	RUN pip install scrapy
	RUN pip install -e git://github.com/scrapy/scrapely.git\#egg=scrapely

	# Clone portia project from github
	RUN git clone https://github.com/scrapinghub/portia.git /opt/portia

	# "Compile"? slybot
	RUN pip install -e /opt/portia/slybot

	# Expose the port used by portia
	EXPOSE 9001 22

	# Add the startup script
	ADD start-portia.sh /opt/portia/start-portia.sh

	# Start the web server
	CMD ["/opt/portia/start-portia.sh"]

The start-portia.sh is a simple way to directly start the server on 9001

    #!/bin/bash

    cd /opt/portia/slyd
    twist -n slyd

  [1]: http://blog.scrapinghub.com/2014/04/01/announcing-portia/
  [2]: https://github.com/scrapinghub/portia
