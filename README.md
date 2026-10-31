# Saúde na Palma da Mão | Aplicativo React Native

Aplicativo mobile do projeto integrador **Saúde para Todos**, desenvolvido com **React Native, Expo e TypeScript**. O objetivo é disponibilizar uma interface para acesso a serviços de saúde, incluindo, conforme a evolução da integração, consulta a clínicas, profissionais, especialidades e agendamentos.

> **Estado do projeto:** configuração inicial do aplicativo concluída. O template padrão do Expo está em execução no Expo Go em um celular Android. As telas de negócio e a integração com a API ainda serão implementadas.

## Tecnologias

- React Native: interface mobile.
- Expo: ferramentas de desenvolvimento, inicialização e testes.
- TypeScript e TSX: implementação dos componentes e telas.
- Expo Router: organização de telas e navegação baseada em arquivos.
- Expo Go: execução inicial em um celular Android físico.
- Metro Bundler: empacotamento do código durante o desenvolvimento.

### Backend existente

O aplicativo será integrado posteriormente à API do projeto Saúde na Palma da Mão:

- Node.js com Express.js.
- TypeORM.
- PostgreSQL.
- Autenticação por JWT.
- API organizada sob o prefixo `/api/v1`.

O endereço de produção da API e os contratos dos endpoints deverão ser confirmados antes da integração. **Nenhum endpoint está integrado neste frontend até o momento.**

## Ambiente utilizado na configuração inicial

| Item | Configuração |
| --- | --- |
| Sistema operacional | Windows |
| Terminal | Windows PowerShell |
| Editor | Visual Studio Code |
| Node.js | `v22.23.3` |
| npm | `10.9.9` |
| Criação do projeto | `create-expo-app@5.0.0` |
| Template | `default@sdk-57`, compatível com Expo Go |
| Testes | Celular Android físico com Expo Go |
| Acesso ao servidor | Túnel do Expo |

As versões listadas registram o ambiente inicial do projeto, não representam requisitos universais para futuras versões.

**Android Studio, emulador Android, ADB e Java não foram necessários para esta execução inicial via Expo Go.** Essas ferramentas podem ser necessárias futuramente para tarefas de compilação nativa local ou testes específicos.

## Pré-requisitos para executar

1. Instalar o [Node.js](https://nodejs.org/), em versão compatível com o SDK utilizado no projeto.
2. Ter npm disponível.
3. Instalar [Visual Studio Code](https://code.visualstudio.com/) ou outro editor.
4. Instalar [Expo Go](https://expo.dev/go) no celular Android.
5. Ter acesso à internet no computador e no celular.
6. Criar uma conta gratuita no [Expo](https://expo.dev/signup) caso utilize o modo de túnel assinado.

Verificar as ferramentas no PowerShell:

```powershell
node -v
npm -v
```

## Como executar o projeto após clonar o repositório

Clone o repositório pelo endereço que será disponibilizado no GitHub:

```powershell
git clone <URL-DO-REPOSITORIO>
cd saude-na-palma-da-mao-react-native
```

Instale as dependências:

```powershell
npm install
```

### Login no Expo sem abrir o navegador

Durante a configuração no Windows, `npx expo login` falhou ao tentar abrir automaticamente o navegador. A alternativa que **funcionou neste ambiente** foi:

```powershell
npx expo login --no-browser
```

O terminal solicita o **nome de usuário ou e-mail** e a **senha** da conta Expo. Não inclua credenciais em comandos, arquivos versionados ou mensagens públicas.

Confirme o login:

```powershell
npx expo whoami
```

Se estiver autenticado, o comando retorna o nome de usuário Expo. Não é necessário repetir o login a cada inicialização enquanto a sessão permanecer válida.

### Iniciar o aplicativo no celular Android

Neste ambiente, a conexão local não abriu o aplicativo, mas o **modo Tunnel funcionou**:

```powershell
npx expo start --tunnel
```

1. Mantenha o terminal com o Metro Bundler aberto.
2. Abra o aplicativo Expo Go no Android.
3. Escaneie o QR Code exibido no terminal.
4. Aguarde o carregamento do aplicativo.
5. Ao alterar um arquivo, o Expo Go normalmente atualiza a tela por Fast Refresh.

Para encerrar o servidor, use `Ctrl + C` no terminal.

Se o computador e o celular estiverem em uma rede local que permita comunicação direta, também é possível tentar:

```powershell
npx expo start
```

O modo Tunnel depende da conexão com a internet e pode ser mais lento que uma conexão local.

## Como o projeto foi criado inicialmente

O comando utilizado para gerar a estrutura foi:

```powershell
npx create-expo-app@latest saude-na-palma-da-mao-react-native
```

O assistente de criação selecionou o template **Expo Go-compatible `default@sdk-57`**. Depois, o projeto foi acessado com:

```powershell
cd saude-na-palma-da-mao-react-native
npm install
```

**Para quem clonar o repositório, não execute `create-expo-app` novamente.** Use apenas `git clone`, `npm install` e os comandos de inicialização.

## Estrutura inicial e arquivos importantes

```text
saude-na-palma-da-mao-react-native/
├── src/
│   └── app/
│       ├── index.tsx          # Tela inicial do template Expo
│       └── _layout.tsx        # Layout e configuração da navegação
├── package.json              # Scripts e dependências
└── ...                       # Demais arquivos e pastas do template
```

A estrutura acima é **parcial e ilustrativa**. O projeto também utiliza componentes importados da pasta `components` e constantes importadas de `constants/theme`, conforme os arquivos iniciais compartilhados. Consulte o repositório para a árvore completa.

### `src/app/index.tsx`

É a tela inicial do template. Atualmente contém o componente `HomeScreen`, elementos de interface como `ThemedView` e `ThemedText`, estilos com `StyleSheet` e orientações padrão do Expo.

### `src/app/_layout.tsx`

Define o layout da navegação utilizado pelo Expo Router. Atualmente utiliza `ThemeProvider`, `useColorScheme`, `AnimatedSplashOverlay` e `AppTabs`.

**Atenção:** os componentes e nomes acima descrevem o template inicial. Ainda não representam telas próprias do Saúde na Palma da Mão.

## Problemas encontrados na configuração e soluções

### 1. Falha de rede no `npm install`

**Sintoma:** `npm error code ECONNRESET` durante a criação do projeto, acompanhado de aviso de limpeza `EPERM` em `node_modules`.

**Solução aplicada:** entrar na pasta criada e executar novamente:

```powershell
npm install
```

A instalação foi concluída com **562 pacotes adicionados e 563 auditados**.

### 2. Avisos de segurança do npm

A instalação apresentou **12 vulnerabilidades de severidade moderada**. Os alertas ainda precisam ser analisados; não foram considerados resolvidos.

Para consultar os detalhes:

```powershell
npm audit
```

Evite executar `npm audit fix --force` sem avaliar as alterações, pois atualizações incompatíveis podem afetar o projeto Expo.

### 3. Erro no login com navegador

**Sintoma:** falha em `cmd.exe /c start` ao tentar abrir o endereço de autenticação do Expo.

**Solução aplicada:**

```powershell
npx expo login --no-browser
npx expo whoami
```

### 4. Conexão local com Expo Go não abriu

**Sintoma:** `npx expo start` gerou QR Code, mas o aplicativo não abriu no dispositivo.

**Solução aplicada após o login:**

```powershell
npx expo start --tunnel
```

O terminal confirmou o processamento do bundle Android.

### 5. Tentativa de túnel sem autenticação

**Sintoma:** `Couldn't create a signed tunnel URL ... You're not logged in`.

**Solução aplicada:** autenticar com `npx expo login --no-browser` e reiniciar com `npx expo start --tunnel`.

### 6. ADB não encontrado

**Sintoma:** `adb` não reconhecido como comando no Windows.

**Observação:** isso não impediu o uso do Expo Go em celular físico. Não foi necessário instalar Android Studio ou configurar `ANDROID_HOME` nesta fase.

### 7. Aviso de animação reduzida

**Sintoma:** `[Reanimated] Reduced motion setting is enabled on this device`.

**Significado:** o dispositivo está configurado para reduzir movimentos; algumas animações podem ser desativadas. Não indica falha na compilação.

## Próximas etapas planejadas

- Estudar JSX/TSX, componentes, propriedades, estados e estilos.
- Definir a organização das telas e componentes do aplicativo.
- Implementar interfaces de login e cadastro.
- Integrar os serviços HTTP com a API Express existente.
- Implementar autenticação JWT de acordo com os contratos reais da API.
- Desenvolver consultas de clínicas, profissionais, especialidades e agendamentos.
- Realizar testes funcionais e preparar uma distribuição adequada.

Essas funcionalidades são **planejadas, não implementadas**.

## Publicar no GitHub

Depois de criar um repositório vazio no GitHub, confira se já existe um repositório Git local:

```powershell
git status
```

Se a pasta ainda não tiver sido inicializada como repositório:

```powershell
git init
```

Confira o `.gitignore` do Expo antes de adicionar arquivos e garanta que `node_modules/`, arquivos `.env` com segredos e arquivos locais gerados não sejam enviados.

Em seguida:

```powershell
git add .
git commit -m "docs: adiciona README e configuracao inicial do Expo"
git branch -M main
git remote add origin <URL-DO-REPOSITORIO>
git push -u origin main
```

Se `origin` já existir, consulte `git remote -v` antes de tentar adicioná-lo novamente. Para projetos com commits prévios, revise a branch e o histórico antes de executar `git branch -M main`.

## Referências oficiais

- [React Native, documentação](https://reactnative.dev/docs/getting-started)
- [Expo, documentação](https://docs.expo.dev/)
- [Expo, configuração do ambiente](https://docs.expo.dev/get-started/set-up-your-environment/)
- [Expo, iniciar o desenvolvimento](https://docs.expo.dev/get-started/start-developing/)
- [Expo CLI, comandos e túnel](https://docs.expo.dev/more/expo-cli/)
- [Expo Router, introdução](https://docs.expo.dev/router/introduction/)

---

Projeto integrador **Saúde para Todos**. Aplicativo **Saúde na Palma da Mão**.
