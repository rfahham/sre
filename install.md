# INSTALAÇÃO

A instalação do **Datadog** depende do sistema operacional e do tipo de monitoramento que você deseja configurar (como infraestrutura, logs ou APM). Abaixo, vou fornecer as etapas gerais para instalar o **Datadog Agent**, que é o principal componente usado para coletar métricas e logs.

### 1. **Criando uma Conta no Datadog**
Antes de instalar o Datadog Agent, você precisa de uma conta no Datadog. Se ainda não tem, acesse o site do Datadog:

- [Criar conta no Datadog](https://www.datadoghq.com/)

### 2. **Instalando o Datadog Agent**

O **Datadog Agent** é responsável por coletar métricas e logs dos sistemas monitorados. Aqui estão as instruções para instalar o agente em diferentes sistemas operacionais:

#### **a. Para Linux**

1. **Adicionar o repositório Datadog:**
   
   Em distribuições baseadas no Debian (como Ubuntu), adicione o repositório do Datadog:

   ```bash
   DD_AGENT_MAJOR_VERSION=7 \
   DD_API_KEY=<YOUR_DATADOG_API_KEY> \
   bash -c "$(curl -L https://s3.amazonaws.com/dd-agent/scripts/install_script.sh)"
   ```

   Para distribuições baseadas no RHEL (como CentOS ou Amazon Linux), use:

   ```bash
   DD_AGENT_MAJOR_VERSION=7 \
   DD_API_KEY=<YOUR_DATADOG_API_KEY> \
   bash -c "$(curl -L https://s3.amazonaws.com/dd-agent/scripts/install_script_rhel.sh)"
   ```

2. **Substitua `<YOUR_DATADOG_API_KEY>` pela sua chave API** (você pode encontrar sua chave API no painel do Datadog, em **Integrations > APIs**).

3. **Verifique a instalação do agente**:

   Após a instalação, você pode verificar se o Datadog Agent está em funcionamento com o comando:

   ```bash
   sudo datadog-agent status
   ```

#### **b. Para macOS**

1. **Instalar via Homebrew** (se você tiver o Homebrew instalado):

   ```bash
   brew install datadog-agent
   ```

2. **Configurar o Datadog Agent**:

   Após a instalação, edite o arquivo de configuração do agente para adicionar sua chave API:

   ```bash
   sudo vim /etc/datadog-agent/datadog.yaml
   ```

   Adicione sua chave API no campo `api_key`.

3. **Iniciar o Datadog Agent**:

   Para iniciar o Datadog Agent no macOS, use o comando:

   ```bash
   sudo launchctl load /Library/LaunchDaemons/com.datadoghq.agent.plist
   ```

#### **c. Para Windows**

1. **Baixar o instalador do Datadog**:

   Acesse a [página de downloads do Datadog](https://www.datadoghq.com/download/) e baixe o instalador para Windows.

2. **Executar o Instalador**:

   Após o download, execute o instalador `.msi` e siga as instruções na tela.

3. **Configurar o Datadog Agent**:

   Após a instalação, abra o arquivo `datadog.yaml` localizado em `C:\ProgramData\Datadog` e insira sua chave API.

4. **Iniciar o Datadog Agent**:

   O agente deve iniciar automaticamente, mas se não iniciar, você pode iniciá-lo manualmente através dos serviços do Windows.

#### **d. Para Kubernetes/Docker**

Se você estiver usando **Kubernetes** ou **Docker**, você pode instalar o Datadog Agent usando o Kubernetes Operator ou por meio de containers Docker. O Datadog fornece arquivos de configuração para facilitar essa instalação.

Para **Kubernetes**, você pode usar o seguinte comando (após configurar o `datadog.yaml` com sua chave API):

```bash
kubectl apply -f https://raw.githubusercontent.com/DataDog/datadog-agent/master/deployments/kubernetes/datadog-agent.yaml
```

Para **Docker**, você pode rodar o Datadog Agent com o seguinte comando Docker:

```bash
docker run -d --name datadog-agent -e DD_API_KEY=<YOUR_DATADOG_API_KEY> -e DD_SITE="datadoghq.com" datadog/agent:latest
```

### 3. **Configurando o Datadog para Monitoramento**

Após a instalação do agente, você pode configurar o Datadog para monitorar serviços específicos (bancos de dados, servidores web, etc.). Você pode habilitar integrações através do painel do Datadog ou editando o arquivo de configuração do agente para incluir a monitorização de serviços específicos.

### 4. **Verificando a Instalação**

Após a instalação e configuração, acesse o **painel de controle do Datadog** para verificar se o agente está enviando dados corretamente. Você deve começar a ver métricas, logs e outras informações sobre seus sistemas monitorados.

---

Esses são os passos principais para instalar e configurar o Datadog. O processo pode variar um pouco dependendo do ambiente ou da infraestrutura que você está usando, mas o Datadog tem uma [documentação extensa](https://docs.datadoghq.com/) para orientações adicionais e para resolver problemas específicos de instalação.

Amazon linux

```bash
DD_API_KEY= DD_INSTALL_ONLY=true DD_SITE="datadoghq.com" bash -c "$(curl -L https://install.datadoghq.com/scripts/install_script_agent7.sh)"
```