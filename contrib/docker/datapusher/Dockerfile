FROM python:3-onbuild
RUN apt-get update && apt-get install -y postgresql libpq-dev sudo
RUN service postgresql start && sudo -u postgres createuser -S -D -R -w datapusher_jobs && sudo -u postgres createdb -O datapusher_jobs datapusher_jobs -E utf-8 -T template0
CMD [ "python", "datapusher/main.py", "deployment/datapusher_settings.py"]