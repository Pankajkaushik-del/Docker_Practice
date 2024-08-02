FROM ubuntu

WORKDIR /app

COPY requirements.txt /app
COPY devops /app

#ENV PIP_BREAK_SYSTEM_PACKAGES 1

# Old command provided by Abhishek
#RUN apt-get update && \
    #apt-get install -y python3 python3-pip && \
    #pip install -r requirements.txt && \
    #cd devops
    
# new command found from the comment
RUN apt-get update && \
    apt-get install -y python3 python3-venv && \
    python3 -m venv /venv && \
    /venv/bin/pip install -r requirements.txt
    cd devops

#Old provided by Abhishek
#ENTRYPOINT ["python3"]

# Provided by video comment
ENTRYPOINT ["/venv/bin/python3"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]
