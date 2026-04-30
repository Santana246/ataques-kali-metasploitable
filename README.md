# ataques-kali-metasploitable
Aqui serão simulados alguns tipos de ataques comuns de força bruta em um sistema vulnerável utilizando-se um laboratório virtual e o programa Medusa.

# Softwares usados
- [Oracle VirtualBox](https://www.virtualbox.org/)
- [Kali Linux para VirtualBox](https://www.kali.org/get-kali/#kali-virtual-machines)
- [Metasploitable 2](https://sourceforge.net/projects/metasploitable/files/Metasploitable2/)

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

### Criação das Wordlists de login e senha
- OBS: o termo **\n** é reservado para a quebra de linha, que separa um termo do outro. <img width="490" height="97" alt="image" src="https://github.com/user-attachments/assets/edfdb3a6-b47f-450f-be0f-6ecc6d58fe5b" />

### Tentativa de ataque com o Medusa
- Está destacado em marcatexto a iteração que decifrou com sucesso o login e a senha da máquina-alvo. <img width="631" height="373" alt="image" src="https://github.com/user-attachments/assets/dde75cf5-db55-4658-a3c9-ea682b34831e" />

### Conectando à máquina-alvo e transferindo um arquivo criado anteriormente
- <img width="320" height="165" alt="image" src="https://github.com/user-attachments/assets/64b67b98-32cf-4838-93e0-f90a8332fa0d" />
- <img width="615" height="181" alt="image" src="https://github.com/user-attachments/assets/63c04602-7580-42cf-8595-7abb5180eb58" />
- Na máquina-alvo: <img width="443" height="34" alt="image" src="https://github.com/user-attachments/assets/b1be3a3c-d007-43e6-a0dc-4f9786b84391" />

## Automação de tentativas em formulário web (DVWA)
- O Medusa também pode ser utilizado para automatizar requests em formulários HTTP. Aqui vai um exemplo em um site lançado na própria máquina virtual, o DWVA (**[IP_ADRESS]/dvwa/login.php**).
- Serão usadas as mesmas wordlists do outro exemplo.

- Testando o login para ver como funciona sua estrutura. <img width="1232" height="683" alt="image" src="https://github.com/user-attachments/assets/45c79547-f8e1-4144-9063-525a567380bc" />
- **ALERTA:** Na hora de executar o comando de bruteforce, não foi possível distinguir a combinação correta das outras; talvez o Medusa não seja o melhor programa para isso, irei procurar outras alternativas depois. <img width="636" height="452" alt="image" src="https://github.com/user-attachments/assets/8318889b-ebdb-49ef-8f16-73efbf86e64b" />


## Password spraying em SMB com enumeração de usuários.
- Primeiro, são enumerados os usuários por meio do protocolo SMB (Server Message Block) com a ferramenta enum4linux. O resultado é posto em um arquivo .txt. <img width="637" height="70" alt="image" src="https://github.com/user-attachments/assets/f6b6fae2-97ee-4c59-b4e2-4cea1be0e5fa" /> <img width="238" height="579" alt="image" src="https://github.com/user-attachments/assets/0907d07e-40de-43f2-aabb-26bce994b9f1" />
- **Criação de Wordlists para o SMB**: <img width="565" height="95" alt="image" src="https://github.com/user-attachments/assets/394d43b6-72d2-4538-8532-a996b9e3cf60" />

### Ataque
- <img width="635" height="435" alt="image" src="https://github.com/user-attachments/assets/5ab7fdee-bfe3-4df5-99c0-da162a6a8e47" />
- Testando acesso com o SMB_Client: <img width="647" height="363" alt="image" src="https://github.com/user-attachments/assets/4bad37f9-a5ac-4672-9110-0806ef18e10e" />

# Como evitar este tipo de ataque:
- Senhas fortes e atualizadas regularmente (em um período de 1-2 anos ou alguns meses, dependendo da criticalidade do serviço).
- Auditorias regulares para checar a segurança do sistema.
- Autenticação de Múltiplos Fatores, se possível.


