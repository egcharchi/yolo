FROM egcharchi/yolo-backend:1.0.0

WORKDIR /backend

COPY package.json package.json

RUN npm install

COPY . .

EXPOSE 5000

CMD [ "npm", "start" ]
