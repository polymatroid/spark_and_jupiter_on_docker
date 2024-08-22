FROM jupyter/base-notebook:latest

USER root

# Install Java
RUN apt-get update && apt-get install -y openjdk-11-jdk

# Install PySpark and pandas
RUN pip install pyspark pandas

# Set JAVA_HOME environment variable
ENV JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
ENV PATH="${JAVA_HOME}/bin:${PATH}"

# USER ${NB_UID}