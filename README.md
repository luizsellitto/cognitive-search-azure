# Cognitive Search com Azure AI

Este repositório documenta o passo a passo para criar e realizar consultas utilizando o serviço Azure AI Search, com integração ao Azure AI Services e Storage Accounts.
Adendo: Mesmo com o conteúdo das imagens estando em português, decidi colocar as instruções para o site com língua inglesa

---

## 🚀 Sumário

- [1. Criando o Azure AI Services](#1-criando-o-azure-ai-services)
- [2. Criando o Azure AI Search](#2-criando-o-azure-ai-search)
- [3. Criando a Storage Account](#3-criando-a-storage-account)
- [4. Configurando o Sistema de Pesquisa](#4-configurando-o-sistema-de-pesquisa)
  - [4.1 Criando um contêiner para armazenar os documentos](#41-criando-um-contêiner-para-armazenar-os-documentos)
  - [4.2 Fazendo upload dos arquivos de simulação](#42-fazendo-upload-dos-arquivos-de-simula%C3%A7%C3%A3o)
- [5. Configurando o Azure AI Search para usar o contêiner](#5-configurando-o-azure-ai-search-para-usar-o-contêiner)
- [6. Realizando consultas](#6-realizando-consultas)

---

## 1. Criando o Azure AI Services

1. Acesse o portal do Azure e clique em **"Criar um novo recurso"**.
2. Pesquise por **"Azure AI Services"** e clique em **"Create"**.

![Azure AI Services](https://github.com/user-attachments/assets/846d25e4-156f-4302-aa37-27fc84c795dd)

3. Selecione o **Resource Group** e defina o nome do recurso.
4. Escolha a versão desejada em **"Pricing Tier"**.
5. Clique em **"Review + Create"** e, após a validação, em **"Create"**.

---

## 2. Criando o Azure AI Search

1. Acesse o portal do Azure e clique em **"Criar um novo recurso"**.
2. Pesquise por **"Azure AI Search"** e clique em **"Create"**.

![Criando Serviço de Pesquisa](https://github.com/user-attachments/assets/3cc9858b-4c1e-42e8-9011-4f217b687723)

3. Configure o **Resource Group** e o **Service Name**.
4. Defina a região como **"Central US"**.
5. Selecione o plano **Basic** recomendado para testes.
6. Clique em **"Review + Create"** e, após a validação, em **"Create"**.

---

## 3. Criando a Storage Account

1. No painel do Azure, clique em **"Criar um novo recurso"**.
2. Selecione **"Storage Accounts"** e clique em **"Create"**.

![Storage Accounts](https://github.com/user-attachments/assets/8a899517-e882-44a7-9c4d-53dea2e9476b)

3. Configure:
   - **Resource Group**.
   - Nome único (3 a 24 caracteres).
   - Versão **Standard**.
   - Redundância **LRS**.

![Storage Account Criado](https://github.com/user-attachments/assets/7e384766-9593-4819-822e-902079a80840)

4. Clique em **"Review + Create"** e, após a revisão, em **"Create"**.

---

## 4. Configurando o Sistema de Pesquisa

### 4.1 Criando um contêiner para armazenar os documentos

1. Acesse a **Storage Account** criada.
2. No menu lateral, clique em **"Settings"** > **"Configuration"**.
3. Ative o **Acesso Anônimo Blob**.

![Ativando Acesso Anônimo](https://github.com/user-attachments/assets/3aba41da-5753-418f-934e-82bf4b3c3888)

4. Vá em **"Data Storage"** > **"Containers"**.
5. Clique no ícone **"+"** para criar um novo contêiner.
6. Defina:
   - Nome do contêiner.
   - **Anonymous Access Level**: selecione **"Container (anonymous read access for containers and blobs)"**.
7. Clique em **"Create"**.

---

### 4.2 Fazendo upload dos arquivos de simulação

1. Acesse novamente o menu **"Containers"** e selecione o contêiner criado.
2. Baixe os arquivos de exemplo:  
   ➡️ [https://aka.ms/mslearn-coffee-reviews](https://aka.ms/mslearn-coffee-reviews)
3. No contêiner, clique em **"Upload"**.

![Upload de Arquivos](https://github.com/user-attachments/assets/473fcba5-9ff1-43fe-aed3-3b66d9383017)

4. Selecione todos os arquivos baixados e clique em **"Upload"**.

---

## 5. Configurando o Azure AI Search para usar o contêiner

1. No serviço **Azure AI Search**, clique em **"Import Data"**.

![Importando Dados](https://github.com/user-attachments/assets/366bab99-a5ee-40e9-a9b4-de0000fae406)

2. Em **"Data Source"**, selecione **"Azure Blob Storage"**.
3. Configure:
   - Nome da fonte.
   - Sua **Subscription**.
   - Em **"Connection String"**, selecione **"Choose an existing connection"**.
4. Selecione a **Storage Account** e o contêiner com os documentos.
5. Caso o campo **"Container Name"** não seja preenchido automaticamente, insira manualmente.
6. Clique em **"Add"** e aguarde a validação.
7. Clique em **"Skip to"**.
8. Clique em **"Create an Indexer"**.
9. Finalize clicando em **"Submit"**.

---

## 6. Realizando consultas

1. No **Azure Search Service**, clique em **"Search Explorer"**.

![Explorador de Pesquisa](https://github.com/user-attachments/assets/366bab99-a5ee-40e9-a9b4-de0000fae406)

2. Verifique se a cadeia de consulta está **"On"**.

![Consulta Ativada](https://github.com/user-attachments/assets/6b39fdd1-5b54-4241-a760-150ba1b28dab)

3. Execute a consulta para buscar comentários sobre cafés em Chicago:

```bash
search=locations:'Chicago'
```

![Captura de tela 2025-05-21 225103](https://github.com/user-attachments/assets/6f373786-7aa5-4149-b13b-a20929a7d411)
