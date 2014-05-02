#Presentation
Portia is an awesome open source new web-scraping tool based on scrapy for easy and visual data mining of structured data in web pages.

* Article: [http://blog.scrapinghub.com/2014/04/01/announcing-portia/][1]
* Github project: [https://github.com/scrapinghub/portia][2]

##How to use it
- If you run it directly, it will start the Portia server on port 9001
- You can also run it with bash to take the contents of a scraping located at /opt/portia/slyd/data/projects

### Future improvements
- Add openssh-server to the init script to allow ssh access.

The start-portia.sh is a simple way to directly start the server on 9001

    #!/bin/bash

    cd /opt/portia/slyd
    twist -n slyd

  [1]: http://blog.scrapinghub.com/2014/04/01/announcing-portia/
  [2]: https://github.com/scrapinghub/portia
