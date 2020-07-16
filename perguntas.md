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

## Aula 5

1 - Veja o Vagrantfile abaixo:

``` Vagrantfile
Vagrant.configure("2") do |config|

  config.vm.define "phpweb" do |php_config|
    php_config.vm.box = "apache"
  end

  config.vm.define "mysqldb" do |mysql_config|
    mysql_config.vm.box = "ubuntu/bionic64"
  end
end
```

Quais comandos abaixo sobem, de uma vez só, as duas máquinas configuradas acima?

- __vagrant up__

> Alternativa correta! Ao usar vagrant up, subimos todas as máquinas, na ordem da declaração no Vagrantfile

- vagrant provision
- vagrant up --all
- __vagrant up phpweb mysqldb__

> Alternativa correta! No entanto, o comando sobe primeiro a máquina phpweb e depois o mysqldb (mesmo se forem declaradas em uma outra ordem no Vagrantfile)

2 - Você está ajudando uma outra equipe de desenvolvimento, que também usa Vagrant. Ao executar o comando vagrant status, você recebe a seguinte saída:

``` Bash
$vagrant status
Current machine states:
testing                  poweroff (virtualbox)
homologacao              not created (virtualbox)
production               running (virtualbox)
```

Sabendo disso, quais afirmações abaixo são verdadeiras?

- Temos três máquinas rodando
- __Duas máquinas já foram importadas__

> Alternativa correta! As máquinas testing e production já foram importadas e rodaram pelo menos uma vez. A máquina homologacao ainda não foi importada e criada.

- __Para parar a máquina production, podemos usar o comando ```vagrant halt production```__

> Alternativa correta! O comando vagrant halt desliga a máquina virtual e ela assume o status poweroff.

- Existem três Vagrantfile diferentes, um arquivo para cada ambiente

3 - O foco do curso é o Vagrant, mas vimos também alguns detalhes sobre o Puppet. O que podemos dizer sobre o Puppet?

- __É uma ferramenta relacionada ao IaC (Infrastructure as Code)__

> Alternativa correta! Através do Puppet, definimos a configuração da máquina em um script, como se tudo fosse um código.

- O Puppet também cria a máquina virtual e instala o sistema operacional
- O Vagrant não oferece suporte ao Puppet
- __Puppet precisa de um agent instalado, como na máquina guest__

> Alternativa correta! Para aplicar o script de configuração (*.pp), é precisa ter instalado um puppet client na máquina guest.

## Aula 6

1 - Quais foram as principais diferenças entre Puppet e Ansible mencionadas no vídeo?

- O Ansible não pode ser integrado com o Vagrant, já o Puppet, sim.
- O Ansible não faz parte das ferramentas IaC (Infrastructure as Code), já o Puppet, sim
- __O Ansible não precisa de um cliente na máquina guest, o Puppet sim.__

> Alternativa correta! O Ansible não possui nenhum cliente na máquina a configurar, no entanto precisa de Python pré-instalado.

- __O Ansible empurra as configurações do host para o guest, o Puppet "puxa" as configurações do host para o guest.__

> Alternativa correta! Por isso o Ansible não precisa do cliente instalado, pois empurra os comandos para o guest, através do SSH.

2 - Quais são os pré-requisitos para rodar o Ansible?

- __O host precisa ser um sistema *NIX (algum sistema Unix)__

> Alternativa correta! Infelizmente o Ansible não funciona no Windows. Por isso criamos uma máquina virtual com Ubuntu, só para instalar e rodar o Ansible.

- O host deve ter Python instalado
- __O SSH deve funcionar entre o host e o guest__

> Alternativa correta! O Ansible envia comandos SSH do host para o guest.

3 - Vimos durante a aula dois arquivos específicos do Ansible (existem mais), o arquivo __playbook.yml__ e __hosts__.

Qual é o papel do arquivo __hosts__?

- Possui todos os detalhes do provisionamento, como a instalação dos pacotes e inicialização do serviço a rodar.
- __É o inventário que define quais máquinas queremos provisionar__

> Alternativa correta! O arquivo hosts possui os endereços das máquinas onde queremos aplicar o provisionamento. Podemos definir grupos de máquinas e definir detalhes da conexão SSH, como a chave ou usuário.

- Possui todas a configurações referente à CPU, memória, armazenamento e sistema operacional

4 - Novamente, você foi chamado para ajudar uma equipe que usa o Vagrant, mas agora também tem o Ansible envolvido. Você encontrou o Vagrantfile abaixo:

``` Vagrantfile
Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/bionic64"

  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.provision "ansible" do |ansible|
    ansible.inventory_path = "./hosts"
    ansible.playbook = "./playbook.yml"
  end
end
```

O que você sabe sobre a máquina host?

- Os arquivos hosts e playbook.yml devem estar na mesma pasta do Vagrantfile
- O Ansible vai configurar e alterar a máquina host local
- __O Ansible deve estar instalado na mesma máquina do Vagrant, pois usamos o provisioner do Vagrant para chamar o Ansible__

> Alternativa correta! O Vagrant vai tentar chamar o Ansible na própria máquina host.

## Aula 7

1 - Com qual comando você pode ver todas as máquinas configuradas no host, garantindo que entradas inválidas não apareçam?

- vagrant global-status
- vagrant box prune
- __vagrant global-status --prune__

> Alternativa correta! O comando global-status mostra todas as máquinas configuradas no host, e a flag --prune garante que entradas desatualizadas serão removidas.

- vagrant status --global

2 - Vimos os comandos do Vagrant para controlar uma máquina virtual, como ```vagrant up``` ou ```vagrant provision```.

Em configurações Multi-Machine, é possível ser mais específico e usar o nome da configuração/máquina, por exemplo ```vagrant up phpweb```.

Nesses comandos, em lugar do nome, podemos usar também:

- O ID da box
- __O ID da máquina__

> Alternativa correta! Você pode passar o nome ou o ID. O importante é que podemos executar o comando a partir de qualquer pasta, usando o ID da máquina.
> Funciona a partir de qualquer diretório, por exemplo:
> ```vagrant destroy -f <ID>```

- O nome do provedor
- O nome da box
