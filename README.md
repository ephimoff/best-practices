# Best practices

A set of best practises for different tools and languages

Everything listed below is based on personal experience and articles that I read. And, of course, everything is the subject for a change.

## Docker

### Dockerfile

- Use Alpine as a base image unless you can't due to technical reasons
- Pin versions to at least the minor version, example: `2.5-alpine` not `2-alpine`
- Add a maintainer `LABEL` to keep tabs on who initially made the image
- Only include `ARG` and `ENV` instructions if you really need them
- Use `/app` to store your app's code and set it as the `WORKDIR` (if it makes sense)
- When installing packages, take advantage of Docker's layer caching techniques
- If your app is a web service, `EXPOSE 8000` unless you have a strong reason not to
- Include a `wget` driven `HEALTHCHECK` (if it makes sense)
- Stick to the `[]` syntax when supplying your CMD instructions

### docker-compose.yml

- List your services in the order you expect them to start
- Alphabetize each service's properties
- Double quote all strings and use `{}` for empty hashes / dictionaries
- Pin versions to at least the minor version, example: `10.4-alpine` not `10 alpine`
- Use `.` instead of `$PWD` for when you need the current directory's path
- Prefer `build: "."` unless you need to use `args` or some other sub-property
- If your service is a web service, publish port `8000` unless it doesn't make sense to

### .dockerignore

- Don't forget to create this file
- Don't forget to add the `.git` folder
- Don't forget to add any sensitive files such as `.env.production`