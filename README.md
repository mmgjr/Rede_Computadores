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

### Classes de IPs Reservados ou Privados

|**Classes**|**Faixa de endereço IP**|**Notação CIDR**|**Nº de redes**|**Números de IPs**|**IPs por rede**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**A**|10.0.0.0 até 10.255.255.255|10.0.0.0/8|128|16.777.216|16.777.214|
|**B**|172.16.0.0 até 127.31.255.255|172.16.0.0/12|16.384|1.048.576|65.534|
|**C**|192.168.0.0 até 192.168.255.255|192.168.0.0/16|2.097.152|65.535|254|

>As classes de IPs reservados ou privados são traduzidos(convertidos) para Internet(IP válido) pelo protocolo **NAT**. 

>**NAT(Network Address Translator):** 

**CIDR(Classeless Inter-Domain Routing):** Determina um padrão de divisão entre máscara e hosts. Na tabela acima 10.0.0.0/8 , o barra 8 equivale aos bits reservados à REDE.
