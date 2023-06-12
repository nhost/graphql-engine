To build a customized image:

```
git remote add upstream git@github.com:hasura/graphql-engine.git
```

Then:

```
export VERSION=v2.26.0 # or whichever version you want to rebuild
export COMMIT=87be1a6b097f1b93ee44bd6f699991bb7922f7cf # check the correct commit
make prepare-version
```


At this point verify the result of the rebase is correct.

You can test locally by running:

```
make build-images-local VERSION=$VERSION-ce
```

And build and push with:

```
make build-images VERSION=$VERSION-ce
```
