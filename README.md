# atualiza-o-drivers

Atualizar os drivers de um computador via **Prompt de Comando (CMD)** no Windows pode ser feito através de alguns métodos que utilizam ferramentas nativas do sistema ou comandos específicos para ajudar a manter os drivers atualizados. Abaixo, explico os métodos mais eficazes para realizar essa tarefa.

### 1. **Atualizar Drivers Usando o Windows Update (via CMD)**
O Windows Update pode ser acessado diretamente pelo CMD para procurar e instalar atualizações de drivers. Para isso, siga os passos abaixo:

1. **Abrir o Prompt de Comando como Administrador**:
   - Pressione `Win + X` e selecione **"Prompt de Comando (Admin)"** ou **"Windows PowerShell (Admin)"**.
   - Ou pesquise por "cmd" no menu Iniciar, clique com o botão direito e selecione "Executar como administrador".

2. **Executar o Windows Update via CMD**:
   - No Prompt de Comando, digite o seguinte comando para forçar o Windows a procurar atualizações de drivers:

     ```bash
     wuauclt /detectnow
     ```

   - Este comando faz com que o Windows procure por atualizações disponíveis imediatamente, incluindo drivers.

3. **Forçar a instalação de atualizações**:
   Se você deseja que o Windows baixe e instale as atualizações de drivers automaticamente, pode usar o seguinte comando:

     ```bash
     wuauclt /updatenow
     ```

   Esses comandos não permitem selecionar drivers individualmente, mas fazem com que o sistema procure e instale as atualizações automaticamente, incluindo os drivers.

### 2. **Usar o `pnputil` para Instalar ou Atualizar Drivers Manualmente**

O **`pnputil`** é uma ferramenta de linha de comando poderosa no Windows para gerenciar drivers. Você pode usá-la para adicionar, remover ou atualizar drivers no sistema.

1. **Abrir o Prompt de Comando como Administrador** (como descrito anteriormente).

2. **Listar os drivers instalados**:
   Para listar todos os drivers instalados no seu computador, use o comando:

   ```bash
   pnputil /enum-drivers
   ```

   Isso mostrará uma lista de drivers instalados no seu sistema, o que pode ser útil para saber se algum driver específico precisa ser atualizado.

3. **Instalar um driver manualmente**:
   Se você tiver um arquivo de driver (com extensão `.inf`), pode instalá-lo manualmente com o seguinte comando:

   ```bash
   pnputil /add-driver "C:\caminho\para\driver\driver.inf" /install
   ```

4. **Remover um driver específico**:
   Caso precise remover um driver, use o comando:

   ```bash
   pnputil /delete-driver "C:\caminho\para\driver\driver.inf" /uninstall
   ```

### 3. **Usar o `devmgmt.msc` (Gerenciador de Dispositivos via CMD)**
O Gerenciador de Dispositivos do Windows pode ser acessado pelo CMD e também oferece uma interface para atualizar drivers.

1. **Abrir o Gerenciador de Dispositivos**:
   No Prompt de Comando, digite:

   ```bash
   devmgmt.msc
   ```

2. **Atualizar Drivers Manualmente**:
   O Gerenciador de Dispositivos se abrirá. Você pode expandir a lista de dispositivos, clicar com o botão direito no dispositivo que deseja atualizar e selecionar **"Atualizar driver"**. Embora esse método não seja inteiramente baseado em linha de comando, ele é acessado via CMD.

### 4. **Usar o `DISM` para Manutenção do Sistema**
Embora o **DISM (Deployment Imaging Service and Management Tool)** não atualize drivers diretamente, ele pode ser útil para corrigir erros no sistema que possam estar impedindo a atualização de drivers. Para usá-lo, faça o seguinte:

1. **Abrir o Prompt de Comando como Administrador**.

2. **Executar o comando DISM** para corrigir arquivos de sistema corrompidos:

   ```bash
   dism /online /cleanup-image /restorehealth
   ```

   Esse comando verifica e corrige problemas no sistema operacional, o que pode ajudar a corrigir falhas nas atualizações de drivers.

### 5. **Usar o PowerShell para Atualizações Automáticas**
Embora o PowerShell não seja estritamente o CMD, é uma ferramenta poderosa e de linha de comando que pode ser utilizada para automação. Aqui está como você pode usá-lo para instalar drivers:

1. **Abrir o PowerShell como Administrador** (pode ser acessado da mesma maneira que o CMD).

2. **Instalar drivers com PowerShell**:
   Você pode usar o seguinte comando no PowerShell para verificar e instalar atualizações de drivers:

   ```powershell
   Get-WindowsUpdate -AcceptAll -Install
   ```

   Este comando verifica e instala todas as atualizações disponíveis, incluindo drivers.

---

### Considerações Finais
Embora o Windows forneça algumas maneiras de atualizar drivers via linha de comando, muitas vezes a maneira mais eficiente de garantir que os drivers estão atualizados é através do **Windows Update** ou de ferramentas dedicadas, como o **Gerenciador de Dispositivos** ou programas de atualização de drivers de terceiros. Se você estiver enfrentando problemas com drivers específicos, procurar por atualizações manuais no site do fabricante também pode ser uma boa opção.
