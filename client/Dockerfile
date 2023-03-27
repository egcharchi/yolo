FROM egcharchi/yolo-client:1.0.0

WORKDIR /client

COPY package.json .

RUN npm install && \
    npm audit fix --force && \
    npm cache clean --force

COPY . .

EXPOSE 3000

CMD ["npm", "start"]

