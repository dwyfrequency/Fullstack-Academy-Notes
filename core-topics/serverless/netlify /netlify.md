> netlify init
> in the setup, build command will be gatsby build

once the functions are setup run `netlify dev`

https://www.youtube.com/watch?v=vrSoLMmQ46k&feature=youtu.be

To fix the blank site issue on deploy, be sure to add

```
# example netlify.toml
[build]
command = "gatsby build"
functions = "functions"
publish = "public"ç
```

To get functions running `netlify dev` to build project with your functions
To get the templates for serverless functions, `netlify functions:create`
