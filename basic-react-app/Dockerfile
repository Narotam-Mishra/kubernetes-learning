FROM node:22-slim

WORKDIR /myapp

COPY . .

RUN npm install

EXPOSE 5173

ENV HOST=0.0.0.0

CMD ["npm", "run", "dev", "--", "--host"]