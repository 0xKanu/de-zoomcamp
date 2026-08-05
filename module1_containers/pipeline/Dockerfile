# base image that will run the pipeline
FROM python:3.13.11-slim

COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/


# set working directory inside the container
WORKDIR /code

# add /code to PATH
ENV PATH="/code/.venv.bin:${PATH}"

# copy dependency files to the working directory
COPY pyproject.toml .python-version uv.lock ./

# install dependencies
RUN uv sync --locked

# copy the pipeline script into the container, 1st argument is source, 2nd is destination
COPY ingest_data.py .

# command to run first to run the pipeline
ENTRYPOINT ["python", "ingest_data.py"]
