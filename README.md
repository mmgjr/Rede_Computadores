# Redes de Computadores
## Conceitos

### Modelo OSI(Open System Interconnection)

Modelo de redes de computador,referência da ISO, dividido em camadas de funções.

|Camadas|
|:---:|
|Aplicação|
|Apresentação|
|Sessão|
|Transporte|
|Rede|
|Enlace|
|Física|

### Modelo TCP/IP(Transmission Control Protocol/Internet Protocol)

Modelo atual de redes de computadores.

|Camadas|
|:---:|
|Aplicação|
|Transporte|
|Internet|
|Enlace| 

Enlace-> Equivale as camadas 1 e 2 do moledo OSI;

Internet-> Equivale a camada 3 do modelo OSI;

Transporte-> Equivale a camada 4 do modelo OSI;e

Aplicação->Equivale a camada 5,6 e 7 do modelo OSI.

### Protocolo de Internet versão 4(IPv4)

Padrão de enderecamento de rede. Possui 32 bits divididos em quatro octetos,4 grupos de 8 bits.

**Endereço 127.0.0.1** reservado para loopback(comunicação entre processos da mesma máquina)

|**Classes**|**Faixa de endereço IP**|**IPs por rede**|
|:---:|:---:|:---:|
|**A**|0.0.0.0 até 127.255.255.255|16.777.216|
|**B**|128.0.0.0 até 191.255.255.255|65.536|
|**C**|192.0.0.0 até 223.255.255.255|256|
|**D**|224.0.0.0 até 239.255.255.255|Multicast|
|**E**|240.0.0.0 até 255.255.255.254|Usado para testes pela IETF|

### Classes de IPs Reservados ou Privados

|**Classe**|**Faixa de endereço IP**|**Notação CIDR**|**Nº de redes**|**Números de IPs**|**IPs por rede**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**A**|10.0.0.0 até 10.255.255.255|10.0.0.0/8|128|16.777.216|16.777.214|
|**B**|172.16.0.0 até 127.31.255.255|172.16.0.0/12|16.384|1.048.576|65.534|
|**C**|192.168.0.0 até 192.168.255.255|192.168.0.0/16|2.097.152|65.535|254|

>As classes de IPs reservados ou privados são traduzidos(convertidos) para Internet(IP válido) pelo protocolo **NAT**. 

>**NAT(Network Address Translator):** também conhecido como masquerading. Converte os endereços privados para a uma saída de endereço público, usando o gateway como endereço de acesso na Internet.

>**DNAT()** Processo inverso ao NAT. Muito usado para acesso remoto.

>**ARP(Address Resolution Protocol)** conversão do endereço de internet para enlace.

**CIDR(Classeless Inter-Domain Routing):** Determina um padrão de divisão entre máscara e hosts. Na tabela acima 10.0.0.0/8 , o barra 8 equivale aos bits reservados à REDE.


#### IPv6 8x16 = 128

Zeros à esquerda são omitidos(comprimindo o endereço)

Nas redes privadas possuem um endereço padrão

1º endereço é rede,mas é válido para endereçar Host.

o endereço ponto a ponto, (/127), 2^1 = 2 (rede pode ser usado no host).
