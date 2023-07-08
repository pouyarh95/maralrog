aleo smart contract
------------------------------------------------------------------
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

source $HOME/.cargo/env

rustup install stable

rustup update stable

rustup default stable

git clone https://github.com/AleoHQ/leo
cd leo

apt install clang gcc libssl-dev pkg-config

cargo install --path .

git clone https://github.com/AleoHQ/snarkOS.git --depth 1
cd snarkOS

./build_ubuntu.sh

cargo install --path .
------------------------------------------------------------------
@AleoFaucet send 10 credits to aleo1y9s2yr50paljp0rd8wtqzy6ue9cshyyukwfslx2vhpj588vnguzqnndumr

https://chrome.google.com/webstore/detail/json-beautifier-editor/lpopeocbeepakdnipejhlpcmifheolpl
------------------------------------------------------------------
cd $HOME

mkdir demo_deploy_Leo_app && cd demo_deploy_Leo_app

WALLETADDRESS="aleo16tczu3pcr5h78z69yzyq56x3nlurumsyj469mu947anhzyr68uxsm32fuv"

APPNAME=helloworld_"${WALLETADDRESS:4:6}"

leo new "${APPNAME}"

PATHTOAPP=$(realpath -q $APPNAME)

cd $PATHTOAPP && cd ..

PRIVATEKEY="APrivateKey1zkpDB23cwgPtPuyLBLgBrLdmARC1QdnbkAb4a5zkr8tW5S1"

RECORD="{
  owner: aleo16tczu3pcr5h78z69yzyq56x3nlurumsyj469mu947anhzyr68uxsm32fuv.private,
  microcredits: 50000000u64.private,
  _nonce: 2120230241095403491600241531012123554533180656289241288836698536806171214406group.public
}"

snarkos developer deploy "${APPNAME}.aleo" --private-key "${PRIVATEKEY}" --query "https://vm.aleo.org/api" --path "./${APPNAME}/build/" --broadcast "https://vm.aleo.org/api/testnet3/transaction/broadcast" --fee 600000 --record "${RECORD}"


# maralrog
ALEO
