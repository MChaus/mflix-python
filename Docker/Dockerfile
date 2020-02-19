FROM mongo

RUN apt-get update; \
    apt-get install -y python3; \
    apt-get install -y python3-pip; \
    mkdir /course_m220p && chown -R mongodb:mongodb /course_m220p; \ 
    python3 -m pip install virtualenv;

WORKDIR /course_m220p

ENV VIRTUAL_ENV=/course_m220p/.venv

COPY requirements.txt .

RUN virtualenv .venv --python=python3 && chown -R mongodb:mongodb .venv; 

ENV PATH="$VIRTUAL_ENV/bin:$PATH"

RUN pip install -r requirements.txt;

RUN mkdir /home/mongodb && chown -R mongodb:mongodb /home/mongodb;

EXPOSE 5000 8080

USER mongodb

VOLUME /course_m220p/mflix_python/
