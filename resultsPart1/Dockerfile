# Use official PostGIS image (includes PostgreSQL 16 + PostGIS 3.4)
FROM postgis/postgis:16-3.4

# Set environment variables
ENV POSTGRES_USER=postgres
ENV POSTGRES_PASSWORD=postgres
ENV POSTGRES_DB=garruchosdb

# Install dependencies for h3-pg
RUN apt-get update && apt-get install -y \
    git \
    build-essential \
    cmake \
    postgresql-server-dev-16 \
    && rm -rf /var/lib/apt/lists/*

# Install H3 library
WORKDIR /tmp
RUN git clone https://github.com/uber/h3.git && \
    cd h3 && \
    mkdir build && \
    cd build && \
    cmake -DCMAKE_BUILD_TYPE=Release .. && \
    make && \
    make install && \
    ldconfig

# Install h3-pg extension
RUN git clone https://github.com/zachasme/h3-pg.git && \
    cd h3-pg && \
    make && \
    make install

# Cleanup
RUN rm -rf /tmp/h3 /tmp/h3-pg

# Expose PostgreSQL port
EXPOSE 5432
