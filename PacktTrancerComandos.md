
# Comando para Switches e Roteadores da Cisco.

### Internetwork Operating System IOS

>**IOS** é um sistema operacional presente em Switches e Roteadores da Cisco.

## Comandos

### **Verificando o nível de acesso**

**Switch>**  (User Mode-Modo de usuário)-Sem muito privilégio de acesso e configuração

**Switch#** (Privileged Mode-Modo privilegiado)

**Switch(config)#** (Global Mode)

**OBS:** Nos três modos você pode usar ?(interrogação) para visualizar os possíveis comando de cada nível de acesso.

### **Negando um comando feito**

Basta adicionar o **NO** na frente do comando.

**Switch(config)#** hostname TESTE

**Switch(config)#** no hostname

### **Comando para linhas**

**Ctrl + a** (Volta para o começo da linha)

**Ctrl + e** (Volta para o fim da linha)

**Ctrl + w** (apagar a última palavra)

### **Configurando hora/data e exibindo informações**

**Switch>** enable (subindo um nível de acesso)

**Switch#** clock set 22:30:00 25 Dec 2014

**Switch#** show running config (exibe as configurações,informações que estão na memória volátil)

**Switch(config)#** exit (Volta uma camada na linha de comando, saindo da tela atual)

**Switch#** copy running-config startup-config (salvando as configurações na startup,configuração de inicialização)

### **Protocolo para acessar configurações do Switch/Roteador sem cabo de console. Podendo acessar por rede remota. Instalar um Cliente de TELNET na sua plataforma. O Switch vem por padrão com um servidor de TELNET rodando, mas não tem um endereço IP rodando.**

TELNET - protocolo de tunelamento(protocolo da camada de aplicação)

**Criando senha para acesso por TELNET. Portas vty 1-15**

**Switch(config)#** line vty 0 1 (colocando o acesso nas portas 0-1, apenas dois acessos simultâneos).

**Switch(config-line)#** password (digite a senha)

**Switch(config-line)#** end

**Switch(config-line)#** service password-encryption (colocando criptografia na senha)

**Switch(config-line)#** end

### **SSH - protocolo de segurança**

#### Configurando o SSH

**Switch(config)#** line vty 0 1

**Switch(config-line)#** login local

**Switch(config-line)#** exit

**Switch(config)#** username (digite o nome) password (digite a senha)

**Switch(config)#** ip domain-name (ex: testando.com)

**Switch(config)#** crypto key generate rsa modulus 1024 (tamanho do módulo) 

**Switch(config)#** ip ssh time-out 60 (tempo de duração para sessão no ssh)

**Switch(config)#** ip ssh authentication-retries 4 (número de tentativas de autenticação)

**Switch(config)#** ip ssh version 2 (número da versão do ssh)

**Switch(config)#** line vty 0 1

**Switch(config)#** transport input ssh telnet (aceitando os dois tipos de sessão)

### **Criando uma Interface Virtual para dar endereço IP ao Switch, podendo acessá-lo remotamente**

**Switch>** enable

**Switch#** configure terminal

**Switch(config)#** interface vlan1 (acessando interface vlan para configurar)

**Switch(config-if)#** ip address 192.168.1.120 255.255.255.0 (definindo IP e Máscara de endereço)

**Switch(config-if)#** end (encerrando)

**Switch#** show interface vlan1 (mostra as configurações feitas na interface)

**Switch(config)#** interface vlan1 (acessando interface)

**Switch(config-if)#** no shutdown (para levantar as configurações)

**Switch(config-if)#** shutdown (derrubar as configurações)

**Switch(config-if)#** ip default-gateway 192.168.1.1 (configurando IP para gateway padrão)

**Switch(config-if)#** end(encerrar)

**Switch#** show running-config (olha todas as configurações feitas até o momento)

### **Configurando senhas no Switch**

**Switch>** enable

**Switch#** configure terminal

**Switch(config)#** enable password (digite a senha) Sem criptografia

**Switch(config)#** exit

### **Senha com criptografia**

**Switch(config)#** enable secret (digite a senha) Com criptografia **MD5**

### **Colocando senha para acessar o switch pelo console**

**Switch>** enable

**Switch#** configure terminal

**Switch(config)#** line console 0

**Switch(config-if)#** password (digite a senha)

**Switch#** copy running-config startup-config (salvando as configurações)

### **Adicionando os Banners**

**Switch(config)#** banner# (Menssage of the Day/MOTD)
(Entre com o texto e termine com o símbolo especificado anteriormente >> #)

### **Adicionando os Banners exec**

**Switch(config)#** banner exec # (Mensagem para o administrador)

### **Monstrando as interfaces**

**Switch#** show ip interface brief (mostra todas as interfaces, portas, ip, protocolos...)

**Switch#** terminal monitor (vai mostrar tudo o que for conectado no switch-fisicamente)

**Switch#** show mac address-table (mostra as tabelas dos endereços MAC)

### **Configurando Port Security**

>Comando que limita o número de MAC Address que podem trafegar em uma determinada porta

**Switch>** enable

**Switch#** configure terminal

**Switch(config)#** interface FastEthernet 0/8 (especificando a porta 0/8)

**Switch(config-if)#** switchport mode ?

**Access**- um dispositivo que tenha endereço MAC

**Dynamic**- o sistema vai determinar

**Trunk**- pode ser um switch em outro switch

**Switch(config-if)#** switchport mode access

**Switch(config-if)#** switchport port-security

**Switch(config-if)#** switchport port-security maximum (quantidade de endereço MAC)

**Switch(config-if)#** switchport port-security violation ? (Protect/Restrict/Shutdown)

**Protect**- vai descartar o tráfego.

**Restrict**- vai descartar o tráfego, mas enviará LOG e Mensagens de SMNP.

**Shutdown**- faz tudo e derruba a interface.

**Switch(config-if)#** switchport port-security mac-address (Sticky/H.H.H)

>H.H.H 48 bit mac address - Definir o MAC Address manualmente.

>Sticky - pega todos os MAC e define o MAC que tem acesso.

**Switch(config-if)#** switchport port-securty mac-address sticky

**Switch(config-if)#** do show running-config interface FastEthernet 0/8 (mostrando as configurações)

**Switch(config-if)#** do show port-security interface FastEthernet 0/8 (mostrando as configurações)

### **Port Mirroring/Espelhamento de porta**

**Switch(config)#** monitor session 1 (source Interface FastEthernet 0/2 both) - a porta escolhida 

**Switch(config)#** monitor session 1 (destination Interface FastEthernet 0/6) - aporta de destino

**Switch(config)#** do show monitor

### **Velocidade e Duplex**

>Velocidade: 10 Mbs/100 Mbs; Duplex: Full/Half

**Duplex Mismatch Error**- problema com transmissão de pacote entre os hosts.

**Switch(config)#** interface FastEthernet 0/6 (entrada com problema)

**Switch(config-if)#** duplex ? (Opções: Full/Half)

**Switch(config-if)#** duplex half

**Switch(config-if)#** opções: 10 Mbs/100 Mbs/Auto

### **Optimização da navegação no Cisco IOS**

**Switch(config-if)#** logging sysnchronous

**Switch(config-if)#** do show running

**Switch(config)#** no ip domain-lookup (tirando a busca do sistema por resposta)

### **TimeOut e Erase NVRAM**

>Coloca tempo para navegar no console, encerrando a sessão

**Switch(config)#** line con 0

**Switch(config-line)#** exec-timeout ? (Opções em segundos)

**Switch#** erase ?

**Switch#** erase nvram

**Switch#** reaload

### **Configurando Vlans**

**Switch>** enable

**Switch#** configure terminal

**Switch(config)#** vlan 10

**Switch(config-vlan)#** name (digite um nome)

**Switch(config-vlan)#** exit

**Switch(config)#** vlan 20

**Switch(config-vlan)#** name (digite um nome)

**Switch(config-vlan)#** exit

**Switch(config)#** interface range FastEnthernet 0/2-12 (determinando quais portas fazem parte)

**Switch(config-if-range)#** switchport mode ? (Opções: access/Dynamic/Trunk)

**Switch(config-if-range)#** switchport mode access (dispositivos que tenham endereço MAC vão acessar essas portas)

**Switch(config-if-range)#** switchport mode access vlan 10

**Switch(config-if-range)#** no shut down

### **Definindo a outra Vlan**

**Switch(config)#** interface range FastEthernet 0/13-24

**Switch(config-if-range)#** switchport mode access

**Switch(config-if-range)#** switchport mode access vlan 20

**Switch#** copy running-config startup-config (salvando as configurações feitas)

### **Definindo endereço ip da vlan**

**Switch(config)#** interface vlan1

**Switch(config-if)#** ip address 192.168.0.100 255.255.255.0

**Switch(config-if)#** no shutdown

### **Roteador**

**Roteador>** enable (entrar no modo privilegiado)

**Roteador#** Configure terminal (modo de configuração de terminal)

**Roteador(config)#** no ip domain lookup (desliga a busca de palavras digitadas)

**Roteador(config)#** banner motd @ (Para abrir o texto, coloque o caracter especial antes do ENTER-Definindo o banner)

@ (Para fechar o banner)

**Roteador(config)#** exit (volta uma seção)

**Roteador(config)#** end (volta para início)

**Roteador(config)#** enable secret (digite a senha) (Senha para acessar o Enable)

### **Protocolos**

RIP- ClassFull
OSPF- Class Less
IGRP- Class Less/comportamento ClassFull

(config)# router rip (entrar na interface RIP)

(config-route)# network 172.16.10.0

### **Sobre Métricas**

[120/1] Após a barra, curso(saltos), caminho percorrido.

[120/1] Antes da barra, distância administrativa(AD), a distância administrativa é uma métrica utilizada pelos roteadores para decidir qual rota deve ser inserida na tabela de roteamento. Quando é conhecida mais de uma rota até o mesmo destino que foram aprendidas através de diferentes origens ou protocolos de roteamento.
A preferência é sempre pela rota com menor distância administrativa, cujos valores podem ser observados na tabela abaixo.

|Máscara coringa|WildCard Mask|
|---|---|
|255.0.0.0|0.255.255.255|
|255.255.0.0|0.0.255.255|
|255.255.255.0|0.0.0.255|
|255.2555.255.252|0.0.0.3|
|255.255.255.128/25|0.0.0.127|

**Roteador>** Enable

**Roteador(config)** router ospf 64 (número de variações de ações/protocolos)

**(config-router)** network 172.16.10.0 0.0.0.255 area 0 (wild card + área)

EIGRP é classfull (para remover o classfull > confif-router > no auto-summary, passa a ser classless)

**(config)** router eigrp 90 (número que identifica a rede, número de processo e no eigrp tem que ser para todos os roteadores, padrão)


### **Redistribuirção de Rotas**

EIGRP - possui 5 métricas k1,k2,k3,k4 e k5

**(config)#** router eigrp 65000

**(config-router)#** network 10.1.0.0 0.0.0.3

**(config)#** router ospf 64

**(config-router)#** network 10.2.0.0 0.0.0.3 area 0

**(config)#** router eigrp 65000

**(config-router)#** redistribute ospf 64 metric ?

**(config-router)#** redistribute ospf 64 metric 100 33 255 1 1500 (métricas para eigrp)

**(config)#** router ospf 64

**(config-router)#** redistribute eigrp 65000 ?

**(config-router)#** redistribute eigrp 65000 subnets (ospf não tem rotas summary/rota summary do EIGRP não passe para OSPF)


