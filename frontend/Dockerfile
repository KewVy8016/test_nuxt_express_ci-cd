FROM node:20-alpine
WORKDIR /app
COPY package.json package-lock.json* ./
RUN npm ci || npm install
COPY . .
# When the frontend is served to the host/browser, the API should be reachable
# at http://localhost:7000. Using the internal Docker hostname `api` here causes
# the client (browser) to try to resolve http://api:7000 which fails (ERR_NAME_NOT_RESOLVED).
# Set the public API base to localhost so the browser can reach the backend port
# published on the host.
# ENV NUXT_PUBLIC_API_BASE=http://api:7000
EXPOSE 3000
CMD ["npm","run","dev"]
