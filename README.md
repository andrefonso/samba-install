# samba-install
Tutorial para instalação e configuração do Samba em distros do Debian/Ubuntu</br>
---

**Passo 1: Instalar o Samba**
1) Abra o terminal.
Atualize a lista de pacotes:</br>
`sudo apt update`

2) Atualize a lista de pacotes:</br>
`sudo apt update`

3) Instale o Samba:</br>
`sudo apt install samba` </br> </br>

**Passo 2: Configurar o Samba**
1) Editar o arquivo de configuração do Samba.</br>
`sudo nano /etc/samba/smb.conf`
2) Inserir no final do arquivo as seguintes linhas e depois salvá-lo:</br>

```
Documentos]
        comment = pasta compartilhada
        path = /home/andre/Documentos
        browseable = yes
        writable = yes
        read only = no
        guest ok = no
        create mask = 0777
        directory mask = 0777
```
3) Alterar o usuário do arquivo smb.conf conforme comando a seguir:</br>
`sudo chown andre /etc/samba/smb.conf`
4) Alterar o grupo do arquivo smb.conf conforme comando a seguir:</br>
`sudo chown :andre /etc/samba/smb.conf`
5) Ajustar Permissões da Pasta compartilhada conforme comando a seguir:</br>
`sudo chmod -R 0777 /home/andre/Documentos`
6) Criar usuário e samba para o Samba:</br>
`sudo smbpasswd -a andre` </br> </br> 

**Passo 3: Inciar os Serviços do Samba**
1) Habilitar os serviços do Samba para iniciar automaticamente na inicialização do sistema:</br>
`sudo systemctl enable samba smbd nmbd` </br>

2) Para reiniciar ambos os serviços (caso precise aplicar novas configurações):</br>
`sudo systemctl restart smbd nmbd` </br>

3) Para verificar o status do Samba:</br>
`sudo systemctl status smbd nmbd`




 




