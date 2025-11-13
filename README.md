## 🛠️ Zabbix Lab: Ambiente de Estudo com Docker Compose

Este projeto é um ambiente de laboratório completo e leve para estudar e praticar monitoramento com **Zabbix**, utilizando o **Docker Compose** para orquestrar todos os serviços necessários SEM A NECESSIDADE DE INSTALAÇÃO DE MÁQUINAS VIRTUAIS (VMs).

Ao construir o docker-compose será montado os seguintes servidores (containers):

- zabbix-server
- zabbix-web (frontend)
- zabbix-db (banco de dados)
- 3 zabbix-agentes (servidor1, servidor2 e servidor3).

Caso necessite adicionar mais servidores para serem monitorados (zabbix-agentes), alterar o arquivo docker-compose.yml

---

### 🚀 Mão na massa!!!
#### 1. Pré-requisitos
Certifique-se de que o **Docker** e o **Docker Compose** (ou o `docker compose` CLI) estão instalados e em execução no seu sistema operacional (Windows, macOS ou Linux).

#### 2. Inicialização do Ambiente
1. Clone este repositório ou baixe os arquivos para a sua máquina local.
2. Navegue até o diretório do projeto onde o arquivo `docker-compose.yml` está localizado.
3. Execute o comando para construir e iniciar todos os contêineres em segundo plano:
    ```
    docker-compose up -d
    ```
    
#### 3. Acessando o Zabbix
Após alguns minutos, o Zabbix Server, o Banco de Dados e o Frontend estarão em execução.
- **Acesso Web:** Navegue até `http://localhost:8080`
- **Credenciais Padrão:** Admin / zabbix
---

### 💡 Habilitar a Monitoração dos Servidores (containers):

Para que o Zabbix Server reconheça e colete dados dos agentes, siga este procedimento no Frontend do Zabbix:

1. Acessar via web: `http://localhost:8080` (Usuário: Admin / Senha: zabbix)
2. Vá para **Data collection** > **Hosts**.
3. Clique em **Create host** e cadastre o primeiro agente (`servidor1`):
    - **Host name:** servidor1.
4. Opção **Host groups**: **`Linux servers`**   
4. Na opção **Interfaces**, clique em **Add** e depois **Agent**:        
    - **IP address:** **`127.0.0.1`**
    - **Nome DNS: **`servidor1`**
    - **Connect to**: Selecionar **`DNS`**
    - **Porta:** `10050`
5. Repita o processo para os demais servidores (containers) **`servidor2`** e **`servidor3`**.
    

Após o cadastro e vinculação do template, o ícone ZBX de disponibilidade deve ficar **verde** em poucos minutos.
