# Projeto de estudo Git e GitHub

## Objetivo 🎯
Esse repositório tem como objetivo estudar os comandos e funcionalidades do GIT para controle de versão e utilizando o GitHub como repositório.
A utilização dessas duas ferramentas no dia a dia de uma empresa permite uma gestão eficiente do trabalho em equipe no desenvolvimento de projetos.

## Criando chave SSH e adicionando ao GitHub 🔐
Uma chave SSH é um par de arquivos(um público e um privado) usados para autenticação segura entre o computador local e servidores remotos, como o GitHub.
A criação desse par de chaves permite que você se conecte ao repositório do GitHub sem precisar digitar usuário e senha toda vez que precisar fazer um `git pull` ou `git push`.

### ✅ 1. Verificar se já existe uma chave SSH na sua máquina
Abra um terminal e rode o comando abaixo:
```
ls -al ~/.ssh
```
Caso retorne arquivos como `id_rsa` e `id_rsa.pub`, você já possui um par de chaves criadas para o seu computador e pode urilizá-la.

### ✅ 2. Crie uma nova chave SSH
Para criação de um par de chaves rode o comando abaixo, substituindo pelo e-mail que utiliza no GitHub
```
ssh-keygen -t ed25519 -C "seu-email@exemplo.com"
```
Pressione Enter para aceitar o padrão do local onde as chaves serão salvas(_~/.ssh_), e na pergunta seguinte, caso queira, crie uma frase secreta (passphrase).

### ✅ 3. Adicione a chave SSH ao ssh-agent
Inicie o agente:
```
eval "$(ssh-agent -s)"
```

Adicione a chave:
```
ssh-add ~/.ssh/id_ed25519
```

### ✅ 4. Adicione a chave pública ao GitHub
Para mostrar a chave pública criada, execute o comando abaixo:
```
cat ~/.ssh/id_ed25519.pub
```

Copie o código que é gerado no console e siga as etapas abaixo:
- Com a sua conta do GitHub logada, acesse https://github.com/settings/key
- Clique em *New SSH Key*
- Dê um nome para a chave (normalmente identifica-se o computador ao qual a chave pertence)
- Cole a chave copiada e salve

### ✅ 5. Testando a conexão
Execute o comando abaixo:
```
ssh -T git@github.com
```
Se tudo estiver correto, uma mensagem similar a que está abaixo irá aparecer:
```
Hi username! You've successfully authenticated...
```

### ✅ 6. Configure o Git para usar o SSH
Para as configurações do Git, rode os comandos abaixo para definir seu nome e-mail:
```
git config --global user.name "Seu nome"
git config --global user.email "seu-email@exemplo.com"
```
