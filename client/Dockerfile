FROM egcharchi/yolo-client:1.0.0

WORKDIR /client

COPY package.json package.json

RUN npm install

COPY . .

EXPOSE 3000

CMD [ "npm", "start" ]

