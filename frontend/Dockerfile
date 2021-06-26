FROM node:alpine as builder
WORKDIR /app
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
#엔진엑스의 listen을 3000으로 설정
EXPOSE 3000 
#작성한것을 컨테이너 안의 config 파일로 덮어주는것
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
#빌드파일을 nginx로 넣어준다
COPY --from=builder /app/build  /usr/share/nginx/html
