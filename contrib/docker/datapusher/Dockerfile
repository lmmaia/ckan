FROM python:3-onbuild
ENV LANG C.UTF-8
ENV LC_ALL C
RUN apt-get update && apt-get install -y postgresql libpq-dev sudo
RUN service postgresql start && \
    sudo -u postgres psql -c "CREATE ROLE datapusher_jobs NOSUPERUSER NOCREATEDB NOCREATEROLE LOGIN PASSWORD 'ckan';" && \
    sudo -u postgres psql -c "CREATE DATABASE datapusher_jobs OWNER datapusher_jobs ENCODING 'utf-8' TEMPLATE template0;" && \
    sudo -u postgres psql -c "GRANT ALL PRIVILEGES ON DATABASE datapusher_jobs TO datapusher_jobs;"
CMD service postgresql start && python "datapusher/main.py", "deployment/datapusher_settings.py"