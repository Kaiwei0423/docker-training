# All of these is to set the docker image has the same dependencies as the local environment, so that we can run the pipeline in the docker image without any issues.
FROM python:3.13.11-slim
COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/

WORKDIR /code
COPY pyproject.toml .python-version uv.lock ./

RUN uv sync --locked 

# this is to set the vm has the same dependencies
# RUN pip install pandas pyarrow

# WORKDIR /code
COPY pipeline.py .

ENV PATH="/code/.venv/bin:$PATH"

ENTRYPOINT [ "uv", "run", "python", "pipeline.py" ]


