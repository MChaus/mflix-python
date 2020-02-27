FROM mongo:4.2.3

RUN mkdir /course_m220p && chown -R mongodb:mongodb /course_m220p; \
    mkdir /home/mongodb && chown -R mongodb:mongodb /home/mongodb;

WORKDIR /course_m220p

RUN apt-get update; \
    apt-get install -y python3.6 \
                       python3-pip; \
    \ 
    python3.6 -m pip install --no-cache-dir virtualenv==20.0.7; \
    apt-get clean;

COPY requirements.txt .

RUN virtualenv .venv --python=python3.6 && chown -R mongodb:mongodb .venv; 

ENV VIRTUAL_ENV=/course_m220p/.venv
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

RUN pip3 install --no-cache-dir -r requirements.txt;

EXPOSE 5000 8080

USER mongodb
