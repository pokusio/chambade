# Chambade Studios



```bash
hugo server -b http://127.0.0.1:3131 -p 3131 -w
```



```bash 
npm i -D surge

export DEPLOYMENT_DOMAIN=chambade.surge.sh
export DEPLOYMENT_BASE_URL=https://${DEPLOYMENT_DOMAIN}

if [ -d ./docs ]; then
  rm -fr ./docs
fi;

if [ -d ./public ]; then
  rm -fr ./public
fi;

mkdir -p  ./docs
mkdir -p  ./public

hugoBuildNdeploy () {
  export PATH=$PATH:/usr/local/go/bin
  hugo -b ${DEPLOYMENT_BASE_URL}

  cp -fr ./public/* ./docs/
  alias surge='node ./node_modules/surge/lib/cli.js'
  surge ./public "${DEPLOYMENT_DOMAIN}"
}


hugoBuildNdeploy

```