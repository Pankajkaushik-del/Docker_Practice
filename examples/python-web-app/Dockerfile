# First stage: build stage
FROM ubuntu AS build

WORKDIR /app

COPY requirements.txt /app
COPY devops /app

RUN apt-get update && \
    apt-get install -y python3 python3-pip && \
    pip install -r requirements.txt && \
    cd devops

    ############################################
# HERE STARTS THE STAGE2 OF MULTI STAGE BUILD
############################################
FROM gcr.io/distroless/python3

COPY --from=build /app /app

CMD ["manage.py", "runserver", "0.0.0.0:8000"]
