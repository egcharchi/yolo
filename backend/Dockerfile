FROM egcharchi/yolo-backend:1.0.1

WORKDIR /backend

COPY package.json .

RUN npm install

COPY . .

EXPOSE 5000

CMD ["npm", "start"]
