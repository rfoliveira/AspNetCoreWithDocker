## Ref.: https://youtu.be/Po9jQS7WBDQ

## Para testar essa API

# Este comando irá fazer o build do Dockerfile e taggear ele com "aspnetcore-with-docker:v1" para fácil identificação
docker build -t aspnetcore-with-docker:v1 .

# Este comando irá executar a api dentro do container previamente criado
# O parâmetro "--rm" diz que é para remover o container ao finalizar com ctrl+c
# Neste caso está sendo mapeado a porta do container 5000 e a porta do host 5000
docker run -it --rm -p 5000:5000 aspnetcore-with-docker:v1

# Identificar o IP da máquina virtual rodando o docker
docker-machine env

# Com o IP obtido de "DOCKER_HOST", testar no navegador (ou com curl)
curl http://192.168.99.100:5000/weatherforecast

# Após o teste remover a imagem
docker rmi aspnetcore-with-docker:v1