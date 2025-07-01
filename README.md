# Packer - Provadevops

Este repósitório contém todos os arquivos necessarios para se realizar o provisionamento das maquinas utilizadas para este projeto.
Para realizar o provisionamento das maquinas é necessário:

- # 1 Clonar este repositório
É preciso que clone este repositório para utilizar-se de seus arquivos.

- # 2 Baixe os binários do Packer e do Vagrant
Para executar os comando você utilizará eles, os binários estão disponiveis nos links a seguir:

[Packer](https://developer.hashicorp.com/packer/install)

[Vagrant](https://developer.hashicorp.com/vagrant/install)

Os binarios devem estar na mesma pasa que o arquivo packer.pkr.hcl.

Além disso será necessario que seu computador tenha tanto Python, quanto Ansible instalados em seu coputador.

- # 3 Executar os seguintes comandos, nesta ordem.
~~~
packer init .

packer plugin install github.com/hashicorp/virtualbox

packer plugin install github.com/hashicorp/vagrant

packer build debian.json

vagrant box add debian12 debian12.box

vagrant up

# No terminal da maquina hospedeira |

ssh-keygen # Não precisa preencher nenhuma opção

ssh-copy-id -i <caminho da chave gerada> vagrant@<ip da maquina virtual gerada>

# --------------------------------- |

ansible-playbook -i hosts install_nginx.yml

~~~