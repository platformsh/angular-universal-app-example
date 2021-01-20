#  Server-side rendering (SSR) with Angular Universal  on Platform.sh

A trivial example for running Angular SSR on platform.sh.

Basicaly boils down to adding the following to your Angular SSR app (see https://angular.io/guide/universal) repo:

`.platform.app.yaml`:
```yaml
name: app
type: nodejs:14
hooks:
    build: npm run build:ssr
web:
    commands:
        start: NODE_ENV=production npm run serve:ssr
```
`.platform/routes.yaml`:
```yaml
"https://{default}/":
    type: upstream
    upstream: "app:http"
```
and an empty `.platform/services.yaml`
