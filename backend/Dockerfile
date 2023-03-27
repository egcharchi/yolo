FROM egcharchi/yolo-backend:1.0.0

WORKDIR /backend

COPY package.json .

RUN npm install && \
    npm audit fix --force && \
    npm cache clean --force

COPY . .

EXPOSE 5000

CMD ["npm", "start"]
