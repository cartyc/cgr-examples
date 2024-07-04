# Build Env
FROM cgr.dev/chainguard/python:latest-dev as build

ENV PATH="/app/venv/bin:$PATH"
WORKDIR /app

RUN python -m venv /app/venv
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Runtime Stage
FROM cgr.dev/chainguard/python:latest
ENV PATH="/venv/bin:$PATH"
ENV FLASK_APP=app.py
WORKDIR /app

# Copy Virtual Env Dependencies to Runtime image
COPY --from=build /app/venv /venv

# Copy Python Code
COPY app.py wsgi.py .

EXPOSE 5000

ENTRYPOINT ["python", "app.py"]