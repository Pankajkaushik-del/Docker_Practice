#BASE IMAGE
FROM ubuntu AS build

WORKDIR /app

COPY requirements.txt /app
COPY devops /app

ENV PIP_BREAK_SYSTEM_PACKAGES 1

RUN apt-get update && \
    apt-get install -y python3 python3-pip && \
    pip install -r requirements.txt && \
    cd devops

    ############################################
# HERE STARTS THE MAGIC OF MULTI STAGE BUILD
############################################
FROM gcr.io/distroless/python3

# Copy the compiled binary from the build stage
COPY --from=build /app /app

ENTRYPOINT ["/app"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]
