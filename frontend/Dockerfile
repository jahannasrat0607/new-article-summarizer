# Use an official Python image
FROM python:3.9

# Create a non-root user for security
RUN useradd -m -u 1000 user
USER user
ENV PATH="/home/user/.local/bin:$PATH"

# Set working directory
WORKDIR /app

# Copy and install dependencies
COPY --chown=user requirements.txt requirements.txt
RUN pip install --no-cache-dir --upgrade -r requirements.txt

# Copy application files
COPY --chown=user . /app

# Expose the Streamlit port
EXPOSE 7861

# Start Streamlit app
CMD streamlit run frontend/app.py --server.port 7861 --server.address 0.0.0.0 --browser.serverAddress="0.0.0.0"
