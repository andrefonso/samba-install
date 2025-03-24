# samba-install
Tutorial para instalação e configuração do Samba em distros do Debian/Ubuntu</br>
---

<img src="/imagens/samba.png">


**Passo 1: Instalar o Samba**
1) Abra o terminal.
Atualize a lista de pacotes:
```sh
sudo apt update
```

3) Atualize a lista de pacotes:
```sh
sudo apt upgrade
```

5) Instale o Samba:
```sh
sudo apt install samba
```

**Passo 2: Configurar o Samba**
1) Editar o arquivo de configuração do Samba.
```sh
sudo nano /etc/samba/smb.conf
```
3) Inserir no final do arquivo as seguintes linhas e depois salvá-lo:</br>

```
[Documentos]
        comment = pasta compartilhada
        path = /home/andre/Documentos
        browseable = yes
        writable = yes
        read only = no
        guest ok = no
        create mask = 0777
        directory mask = 0777
```
4) Alterar o usuário e o grupo do arquivo smb.conf conforme comando a seguir:
```sh
sudo chown andre:andre /etc/samba/smb.conf
```
5) Ajustar Permissões da Pasta compartilhada conforme comando a seguir:
```sh
sudo chmod -R 0777 /home/andre/Documentos
```
6) Criar usuário e senha para o Samba:
```sh
sudo smbpasswd -a andre
```

**Passo 3: Iniciar os Serviços do Samba**
1) Habilitar os serviços do Samba para iniciar automaticamente na inicialização do sistema:</br>

```sh
sudo systemctl enable samba smbd nmbd
ou se der erro
sudo systemctl enable smbd nmbd
```

2) Para reiniciar ambos os serviços (caso precise aplicar novas configurações):
```sh
sudo systemctl restart smbd nmbd
```

3) Para verificar o status do Samba:
```sh
sudo systemctl status smbd nmbd
```




 




