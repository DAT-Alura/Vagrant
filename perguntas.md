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

## Aula 3

1 - Ao usar o comando ```vagrant ssh```, é estabelecido uma conexão SSH com a máquina virtual. O que sabemos sobre essa conexão?

- __É usada uma chave pública e privada para se autenticar__

> Alternativa correta! As chaves são automaticamente geradas e a chave pública é adicionada na máquina virtual.

- __É usado localhost para se conectar com a máquina virtual__

> Alternativa correta! O padrão é usar o ```localhost```.

- É usado a porta 22 no host para se conectar com a máquina virtual

2 - Qual é o comando para listar as configurações SSH?

Obs: Você sempre pode verificar todos os comandos na documentação ou na linha de comando:

```vagrant list-commands```

- agrant ssh --list-config
- vagrant ssh list
- __vagrant ssh-config__

> Alternativa correta! O comando apresenta várias informações úteis como host name, porta, usuário e localização da chave privada.

## Aula 4

1 - O que significa provisionar?

- Significa providenciar a rede, CPU e armazenamento
- __Significa providenciar tudo que for preciso para executar um serviço__

> Alternativa correta! Provisionar significa fornecer a rede, CPU, memória, espaço, mas também o sistema operacional e pacotes, além da implantação em si. Tudo o que for preciso para rodar/executar o serviço. Melhor ainda, fica automatizado e pode ser repetido a qualquer momento.

- Significa usar virtualização
- Significa instalar o sistema operacional em uma máquina virtual

2 - Qual é o mapeamento padrão da pasta compartilhada?

- No host é compartilhado uma pasta shared. No guest essa pasta é chamado de /host.
- __No host é compartilhado a pasta que possui o Vagrantfile. No guest essa pasta é chamada de /vagrant.__

> Alternativa correta! Logada a máquina virtual, podemos acessar o host pela pasta /vagrant. Por padrão, é compartilhado todo diretório onde se encontra o Vagrantfile.

- Por padrão não existe nenhuma pasta compartilhada.

3 - Os provisionadores são chamados sempre:

Obs: Se tiver com dúvida, verifique a [documentação](https://www.vagrantup.com/docs/provisioning).

- ... quando executamos o comando vagrant reload
- ... quando executamos comando vagrant up
- __... quando executamos o comando vagrant provision__

> Alternativa correta! Esse comando pede explicitamente a execução de todos os provisionadores configurados.
