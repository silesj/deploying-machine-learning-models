FROM python:3.11

# Create the user that will run the app
RUN adduser --disabled-password --gecos '' ml-api-user

ARG PIP_EXTRA_INDEX_URL

# Install requirements, including from Gemfury
#RUN apt-get update
RUN apt-get install -y git

#ADD ./house-prices-api /opt/house-prices-api/
RUN git clone https://github.com/silesj/ML_Deploy_MSCD.git /opt/deploying-machine-learning-models

WORKDIR /opt/ML_Deploy_MSCD/section-08-deploying-with-containers
#RUN cd /opt/deploying-machine-learning-models/section-08-deploying-with-containers/house-prices-api
#RUN git pull
RUN git checkout mscd_janeth

WORKDIR /opt/ML_Deploy_MSCD/section-08-deploying-with-containers/house-prices-api
RUN pip install --upgrade pip
RUN pip install -r /opt/ML_Deploy_MSCD/section-08-deploying-with-containers/house-prices-api/requirements.txt

RUN chmod +x /opt/ML_Deploy_MSCD/section-08-deploying-with-containers/house-prices-api/run.sh
RUN chown -R ml-api-user:ml-api-user ./

USER ml-api-user

EXPOSE 8001

CMD ["bash", "./run.sh"]
