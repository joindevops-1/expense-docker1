# FROM mysql:8.0
# ENV MYSQL_ROOT_PASSWORD=ExpenseApp@1 
# ADD scripts/*.sql /docker-entrypoint-initdb.d
    # MYSQL_DATABASE=transactions \
    # MYSQL_USER=expense \
    # MYSQL_PASSWORD=ExpenseApp@1

# Start with the official MySQL 8.0 image
FROM mysql:8.0

# Create a new user and group for running the application (not root)
RUN groupadd -g 1001 expense && \
    useradd -u 1001 -r -g expense -s /sbin/nologin expense

# Set environment variables for MySQL configuration
ENV MYSQL_ROOT_PASSWORD=ExpenseApp@1 \
    MYSQL_USER=expense \
    MYSQL_PASSWORD=ExpenseApp@1 \
    MYSQL_DATABASE=transactions

# Change ownership of MySQL directories to the new user
RUN chown -R expense:expense /var/lib/mysql /var/run/mysqld /docker-entrypoint-initdb.d

# Copy initialization scripts into the container
COPY scripts/*.sql /docker-entrypoint-initdb.d/

# Switch to the non-root user for running the container
USER expense

# Set the default command for the MySQL image
CMD ["mysqld"]
