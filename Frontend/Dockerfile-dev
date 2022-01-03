FROM node:16-buster

ENV PYTHONUNBUFFERED=1
RUN apt-get update
RUN apt-get install -y git python3 python3-dev build-essential libc6 libffi-dev python3-pip python3-venv
RUN ln -sf python3 /usr/bin/python

RUN pip3 install --no-cache --upgrade pip setuptools

RUN git clone https://github.com/kartevonmorgen/kartevonmorgen-v1 /frontend
WORKDIR /frontend

RUN yarn install
RUN yarn run build:dev

# Install Frontend
WORKDIR /frontend/scripts/python
RUN python3 -m venv venv
RUN . ./venv/bin/activate
RUN pip3 install -r requirements.txt

RUN python3 tag-frequency-cron.py --dev --fetch-all-on-start --sync-once --log-level debug

WORKDIR /frontend

CMD ["yarn", "run", "start:dev"]
#CMD ["pm2-runtime", "start", "'yarn run start:production'", "--name", "kartevonmorgen"]