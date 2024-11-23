name: NorthDots Keycloak

on:
    push:
        branches:
            - main
env:
    GITHUB_REGISTRY: ghcr.io
    DOCKER_IMAGE: ${{ github.repository }}
    POSTGRES_DB: ${{ secrets.POSTGRES_DB }}
    POSTGRES_USER: ${{ secrets.POSTGRES_USER }}
    POSTGRES_PASSWORD: ${{ secrets.POSTGRES_PASSWORD }}
    DB_VENDOR: ${{ secrets.DB_VENDOR }}
    DB_ADDR: ${{ secrets.DB_ADDR }}
    DB_DATABASE: ${{ secrets.DB_DATABASE }}
    DB_USER: ${{ secrets.DB_USER }}
    DB_PASSWORD: ${{ secrets.DB_PASSWORD }}
    KEYCLOAK_ADMIN: ${{ secrets.KEYCLOAK_ADMIN }}
    KEYCLOAK_ADMIN_PASSWORD: ${{ secrets.KEYCLOAK_ADMIN_PASSWORD }}
    KEYCLOAK_USER: ${{ secrets.KEYCLOAK_USER }}
    KC_DB_USERNAME: ${{ secrets.KC_DB_USERNAME }}
    KC_DB_PASSWORD: ${{ secrets.KC_DB_PASSWORD }}
    KC_DB: ${{ secrets.KC_DB }}
    KC_DB_URL: ${{ secrets.KC_DB_URL }}
    DOCKER_BUILDKIT: 1
    DOCKER_CLI_AGGREGATE: 1

jobs:
    build-and-deploy:
        runs-on: ubuntu-latest
        steps:
            - run: echo "🎉 The job was automatically triggered by a ${{ github.event_name }} event."
            - run: echo "🐧 This job is now running on a ${{ runner.os }} server hosted by GitHub!"
            - run: echo "🔎 The name of your branch is ${{ github.ref }} and your repository is ${{ github.repository }}."

    build-push-docker-image:
        runs-on: ubuntu-latest
        steps:
            - name: Build and push the image
              uses: actions/checkout@v4
            - run: |
                echo ${{ secrets.GH_DOCKER_PAT }} | docker login ghcr.io -u ${{ github.repository_owner }} --password-stdin
                docker build . -t ghcr.io/damindda/${{ github.repository }}:latest
                docker push ghcr.io/damindda/${{ github.repository }}:latest