# Secrets Management

## DotEnv File

This approach is inspired by how developers usually manage secrets in their source code.

In this approach, you can store all your secrets in a `.env` file at the root of your collection folder.

Bruno will automatically load the secrets from this file and make them available to your collection via `process.env.<secret-name>`.

![dot env vars](../public/images/dot-env-vars.png)

Your `.env` file might look like:
```shell
JWT_TOKEN=exampletokenhere
```

Your environment file at `environments/Local.bru` would look like:
```groovy
vars {
  host: http://localhost:5005
  jwtToken: {{process.env.JWT_TOKEN}}
}
```

| :warning: WARNING                                    |
|:-----------------------------------------------------|
| Don't forget to add `.env` to your `.gitignore` file.|

And now you can safely check in your collection to source control without worrying about exposing your secrets.


You can store a `.env.sample` file in your collection folder to help other developers get started with the collection.
