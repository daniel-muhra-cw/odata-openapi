# Dockerfile for odata-openapi transform.js
# Uses Alpine Linux and only copies required files for running transform.js
FROM node:alpine

# Install Java (required for Xalan)
RUN apk add --no-cache openjdk11-jre

WORKDIR /app

# Copy only necessary files
COPY transform.js ./transform.js
COPY package.json ./package.json
COPY lib ./lib
COPY xalan ./xalan
COPY OData-Version.xsl ./OData-Version.xsl
COPY V2-to-V4-CSDL.xsl ./V2-to-V4-CSDL.xsl
COPY V4-CSDL-to-OpenAPI.xsl ./V4-CSDL-to-OpenAPI.xsl

# Install only production dependencies (none listed, but for future-proofing)
RUN npm install --omit=dev

# Entrypoint for running transform.js
ENTRYPOINT ["node", "transform.js"]
