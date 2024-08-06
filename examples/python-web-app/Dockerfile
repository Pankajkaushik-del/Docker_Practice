#UPDATED WITH CHATGPT AS COMPARED TO ABHISHEKS FILE
# First stage: build stage
FROM ubuntu AS build

WORKDIR /app

COPY requirements.txt /app
COPY devops /app/devops

ENV PIP_BREAK_SYSTEM_PACKAGES=1

RUN apt-get update && \
    apt-get install -y python3 python3-pip && \
    pip install -r requirements.txt

############################################
# HERE STARTS THE MAGIC OF MULTI STAGE BUILD
############################################
FROM gcr.io/distroless/python3

# Copy the app from the build stage
COPY --from=build /app /app

WORKDIR /app/devops

ENTRYPOINT ["python3", "manage.py"]
CMD ["runserver", "0.0.0.0:8000"]
