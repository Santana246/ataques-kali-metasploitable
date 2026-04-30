# ataques-kali-metasploitable
Aqui serão explorados alguns tipos de ataques que se pode simular com um lab utilizando o Kali Linux e o Metasploitable 2.

# Softwares usados
- [Oracle VirtualBox](https://www.virtualbox.org/)
- [Kali Linux para VirtualBox] (https://www.kali.org/get-kali/#kali-virtual-machines)
- [Metasploitable 2] (https://sourceforge.net/projects/metasploitable/files/Metasploitable2/)

# Configurações iniciais
- Ambas as máquinas foram setadas para funcionar com 2 GB de RAM; foram separados 2 núcleos de processamento para o Kali e 1 para o Metasploitable.
- A rede de ambas é host-only. <img width="623" height="245" alt="image" src="https://github.com/user-attachments/assets/099a86a4-2e27-4295-b3c4-9b1ecbd3fada" />
- Cada máquina vem com user e senha padrão -> para Kali: kali nos dois campos; para Metasploitable 2: msfadmin nos 2 campos.

## Checagem inicial da conexão
- No Metasploitable 2, foi checado o IP (destacado em amarelo) com o comando **ip a**.<img width="704" height="189" alt="image" src="https://github.com/user-attachments/assets/1a94b16e-a609-4ffe-b77c-d24f4b882522" />
- No Kali, foram feitos 3 pings à máquina-alvo para checar se ela é alcançável (**ping -c 3 192.168.xx.xxx**).<img width="505" height="170" alt="image" src="https://github.com/user-attachments/assets/034bec55-2baf-49bb-9113-afd7448f643b" />
- Com a máquina-alvo estando ao alcance da atacante, foi feito um scan com verificação de versão de serviço em alguns ports (**nmap -sV -p [PORTS] [IP_ADDRESS]**). <img width="625" height="355" alt="image" src="https://github.com/user-attachments/assets/45bc5663-eada-4db2-8744-1ad7df0b5ec2" />

# Exploração de alguns tipos de ataques

## Força Bruta em FTP
- Neste tipo de ataque, é usado algum software como o **Medusa** para rodar listas de possíveis nomes de usuário e senhas com o objetivo de ganhar acesso a um outro sistema.
- Combinações de login e senha fracos e/ou repetidos são particularmente vulneráveis a esse tipo de ataque; redefinir os usuários e senhas padrão de seu sistema para que sejam mais fortes é crítico para evitar este tipo de ataque.

### Criação dos arquivos de login e senha
- OBS: o termo **\n** é reservado para a quebra de linha, que separa um termo do outro. <img width="490" height="97" alt="image" src="https://github.com/user-attachments/assets/edfdb3a6-b47f-450f-be0f-6ecc6d58fe5b" />

### Tentativa de ataque com o Medusa
- Está destacado em marcatexto a iteração que decifrou com sucesso o login e a senha da máquina-alvo. <img width="631" height="373" alt="image" src="https://github.com/user-attachments/assets/dde75cf5-db55-4658-a3c9-ea682b34831e" />

### Conectando à máquina-alvo e transferindo um arquivo criado anteriormente
<img width="320" height="165" alt="image" src="https://github.com/user-attachments/assets/64b67b98-32cf-4838-93e0-f90a8332fa0d" />
<img width="615" height="181" alt="image" src="https://github.com/user-attachments/assets/63c04602-7580-42cf-8595-7abb5180eb58" />
- Na máquina-alvo: <img width="443" height="34" alt="image" src="https://github.com/user-attachments/assets/b1be3a3c-d007-43e6-a0dc-4f9786b84391" />

## Automação de tentativas em formulário web (DVWA)
- TODO

## Password spraying em SMB com enumeração de usuários.
- TODO



