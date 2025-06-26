# Packer - Provadevops

Este repósitório contém todos os arquivos necessarios para se realizar o provisionamento das maquinas utilizadas para este projeto.
Para realizar o provisionamento das maquinas é necessário:

- # 1 Clonar este repositório
É preciso que clone este repositório para utilizar-se de seus arquivos.

- # 2 Baixe os binários do Packer e do Vagrant
Para executar os comando você utilizará eles, os binários estão disponiveis nos links a seguir:
[https://developer.hashicorp.com/packer/install](Packer)
[https://developer.hashicorp.com/vagrant/install](Vagrant)
Os binarios devem estar na mesma pasa que o arquivo packer.pkr.hcl.

- # 3 Executar os seguintes comandos, nesta ordem.
~~~
packer init .

packer plugin install github.com/hashicorp/virtualbox

packer plugin install github.com/hashicorp/vagrant

packer build debian.json
~~~