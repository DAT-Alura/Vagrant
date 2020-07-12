# Perguntas

## Aula 1

1 - Quais das ferramentas abaixo são consideradas um Hypervisor?

- __VMware__

> Alternativa correta! VMware é um Hypervisor! No entanto, nesse curso, usaremos o VirtualBox.

- __VirtualBox__

> Alternativa correta! Inclusive, a VirtualBox será o Hypervisor que usaremos durante o curso.

- Docker
- Vagrant

2 - Quais são as vantagens de usar uma máquina virtual?

- Mais agilidade na correção de bugs
- __Menos gastos com infraestrutura__

> Alternativa correta! O mesmo computador (mesmo hardware) pode rodar vários sistemas e ambientes ao mesmo tempo.

- Menos problemas na escalabilidade
- __Mais agilidade na criação de ambiente__

> Alternativa correta! Como ainda veremos, será fácil e rápido criar e rodar um ambiente inteiro de desenvolvimento.

3 - Qual é o papel do Vagrantfile?

- Define qual provider (Hyperviser) será usado
- Possui as configurações do hardware físico utilizado
- __Conter todos as configurações da máquina virtual__

> Alternativa correta! É um belo exemplo de Infraestrutura como código. No Vagrantfile, vamos definir o sistema operacional, a rede, memória, entre outras configurações.

4 - Você já viu o comando ```vagrant up``` durante a aula. O que ele faz?

- Resume a execução da máquina virtual
- __Cria a máquina virtual__

> Alternativa correta! Correto, se a máquina virtual não foi criada ainda, o comando vai criar. Criar significa baixar e importar a box.

- Conecta com a máquina virtual
- Inicializa o Vagrantfile
- __Configura a máquina virtual__

> Alternativa correta! Além de criar, também aplica as configurações na máquina virtual.

## Aula 2

1 - Na configuração ```forwarded_port```, usamos configurações ```guest``` e ```host```, como no exemplo abaixo:

```config.vm.network "forwarded_port", guest: 80, host: 8088```

O que é ```guest``` e ```host```?

- O host define uma porta na faixa 0 a 1024, enquanto o guest define uma porta na faixa 1024 a 49151
- __O guest é a máquina virtual, host é o sistema que roda o provider/hypervisor__

> Alternativa correta! O host é o hospedeiro (o sistema que permite o guest (convidado) a rodar). O guest é a máquina virtual.

- O guest define a porta da máquina virtual chamada guest, e host a porta da máquina virtual host
- O guest é o sistema que roda o provider/hypervisor, host é a máquina virtual

2 - Veja a configuração abaixo:

```config.vm.network "public_network", ip: "192.168.1.17"```

Usando o VirtualBox como provedor, qual será o Network-Adapter usado?

- __Bridge__

> Alternativa correta! Bridge permite que a máquina virtual participe na rede "pública" (empresarial).

- NAT
- Host-only
