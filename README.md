```bash
fpm -s dir -t rpm -v 1.0.0 -n test .
```

```bash
fpm --input-type dir \
--output-type rpm \
--version 1.0.0 \
--name test \
--chdir BUILD/ \
--license 'The Apache License, Version 2.0' \
--vendor 'Jeremy Custenborder' \
--architecture all \
--maintainer jcustenborder@gmail.com \
--config-files /etc

fpm --input-type tar \
--output-type rpm \
--version 1.0.0 \
--name test \
--license 'The Apache License, Version 2.0' \
--vendor 'Jeremy Custenborder' \
--architecture all \
--maintainer jcustenborder@gmail.com \
--config-files /etc \
SOURCES/kafka-connect-simulator-0.1.55.tar.gz 


fpm -s dir -t rpm -v 1.0.0 -n test .
```

kafka-connect-simulator-0.1.59.tar.gz
kafka-connect-simulator-0.1.59.tar.gz