# # Nginx를 사용하지 않고, 로컬에서 실행시켰던 방식으로 npm run dev를 사용하는 방법
# FROM node::24-alpine

# WORKDIR /app

# # package.json 복사해서 실행 => node_modules 만들어짐
# COPY . .
# RUN npm install

# EXPOSE 5173

# # 접근허용
# CMD [ "npm", "run", "dev"]


## 1단계 : 빌드
#FROM node:24-alpine AS build
#WORKDIR /app
#
## package.json 통해 읜존성(패키지) 설치
#COPY package.json ./
#
## 의존성 설치
#RUN npm install
#
## 소스 코드 복사
#COPY . .

# npm run build

# 2단계 : 실행 환경
FROM nginx:stable-alpine

# React에 빌드 결과물은 Nginx 정적 폴더로 복사
# React의 build 도구 현재 Vite 사용 중 (dist 폴더)
#COPY --from=build /app/dist /usr/share/nginx/html
COPY dist /usr/share/nginx/html

EXPOSE 80
# nginx 실행하면 백그라운드 실행, nginx를 컨테이너가 종료돼도 실행될 수 있도록
CMD [ "nginx", "-g", "daemon off;" ]