FROM cgr.dev/chainguard/python:latest-dev
USER root
RUN apk add imagemagick py3-gunicorn 

USER nonroot
WORKDIR /app


RUN pip install flask

COPY webapp.py webapp.py
COPY templates templates

EXPOSE 5000
RUN mkdir uploads

# RUN useradd -u 999 -G sudo -ms /bin/bash webadmin
# RUN chown webadmin:webadmin /uploads
# USER webadmin:webadmin

ENTRYPOINT ["gunicorn"]
CMD ["--bind", "0.0.0.0:5000", "webapp:app"]

