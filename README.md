#### Задание 5. ПИС.

Контроллеры:
```js
app.get("/", (_, res: Response) => {
  res.end(JSON.stringify(counter));
});

app.get("/stat", (_, res: Response) => {
  res.end(JSON.stringify(counter++));
});

app.get("/about", (_, res: Response) => {
  const name = "Ilya Salahov";
  const html = `<h3>Hello, ${name}!</h3>`;

  res.writeHead(200, {'Content-Type': 'text/html'});
  res.end(html);
});
```

```dockerfile
FROM node:latest
WORKDIR /app
COPY ["index.ts",  "package.json", "tsconfig.json", ".env", "./"]
RUN npm install
RUN npm run build
CMD npm run start
EXPOSE 8080
```

Использование образа:
```text
docker build -t salahov/task-7:latest .
docker push salahov/task-7:latest
docker pull salahov/task-7:latest
docker run salahov/task-7:latest
```