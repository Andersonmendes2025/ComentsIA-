# Gerenciador de Avaliações Google com IA

## Visão Geral

O **Gerenciador de Avaliações Google com IA** é um aplicativo web inovador que revoluciona a forma como empresas gerenciam suas avaliações no Google Meu Negócio. Combinando a robustez das APIs oficiais do Google com o poder da inteligência artificial do Google Gemini, esta solução oferece uma experiência completa e automatizada para resposta e gerenciamento de avaliações online.

### Principais Características

- **Autenticação Segura**: Integração completa com OAuth 2.0 do Google
- **Interface Intuitiva**: Design responsivo e moderno para desktop e mobile
- **IA Integrada**: Sugestões automáticas de respostas personalizadas
- **Gerenciamento Completo**: Visualização e resposta a todas as avaliações
- **Múltiplos Negócios**: Suporte para gerenciar vários perfis de empresa
- **Código Aberto**: Totalmente gratuito e customizável

## Tecnologias Utilizadas

### Backend
- **Python 3.7+**: Linguagem principal
- **Flask 2.2.3**: Framework web
- **Google APIs**: Integração com Google My Business
- **Google Gemini**: Inteligência artificial para sugestões

### Frontend
- **HTML5**: Estrutura semântica
- **CSS3**: Design moderno e responsivo
- **JavaScript**: Interatividade e animações
- **Bootstrap**: Framework CSS (opcional)

### APIs e Serviços
- **Google My Business API**: Acesso a avaliações e perfis
- **Google OAuth 2.0**: Autenticação segura
- **Google Gemini API**: Geração de sugestões por IA

## Funcionalidades Principais

### 🔐 Autenticação e Segurança
- Login seguro com conta Google
- Tokens OAuth gerenciados automaticamente
- Sessões criptografadas
- Conformidade com GDPR/LGPD

### 📊 Gerenciamento de Avaliações
- Listagem completa de todas as avaliações
- Filtros por data, classificação e status
- Visualização detalhada de cada avaliação
- Histórico de respostas enviadas

### 🤖 Inteligência Artificial
- Análise automática do sentimento das avaliações
- Sugestões personalizadas de respostas
- Adaptação ao tom e estilo da empresa
- Melhoria contínua baseada no feedback

### 🏢 Múltiplos Negócios
- Gerenciamento de vários perfis de empresa
- Troca rápida entre diferentes locais
- Estatísticas individuais por negócio
- Configurações personalizadas por perfil

## Instalação Rápida

### Pré-requisitos
```bash
# Verificar versão do Python
python --version  # Deve ser 3.7+

# Ter uma conta Google com acesso ao Google My Business
# Acesso ao Google Cloud Console
```

### Configuração do Google Cloud

1. **Criar Projeto**
   - Acesse [Google Cloud Console](https://console.cloud.google.com/)
   - Crie um novo projeto
   - Anote o ID do projeto

2. **Ativar APIs**
   - My Business Business Information API
   - My Business Account Management API
   - (Opcional) Business Profile Performance API

3. **Configurar OAuth**
   - Criar tela de consentimento OAuth
   - Adicionar escopo: `https://www.googleapis.com/auth/business.manage`
   - Criar credenciais OAuth 2.0
   - Baixar arquivo JSON como `client_secrets.json`

4. **Configurar API Gemini**
   - Acesse [Google AI Studio](https://aistudio.google.com/)
   - Gere uma chave de API
   - Configure como variável de ambiente

### Instalação Local

```bash
# 1. Clonar ou baixar o projeto
git clone [URL_DO_REPOSITORIO]
cd google_reviews_app

# 2. Criar ambiente virtual
python -m venv venv

# 3. Ativar ambiente virtual
# Windows PowerShell:
.\venv\Scripts\Activate.ps1
# Windows CMD:
venv\Scripts\activate.bat
# Linux/macOS:
source venv/bin/activate

# 4. Instalar dependências
pip install flask google-auth google-auth-oauthlib google-auth-httplib2 google-api-python-client requests python-dotenv google-generativeai

# 5. Configurar variáveis de ambiente
echo "GEMINI_API_KEY=sua_chave_api_aqui" > .env

# 6. Executar aplicativo
python src/main.py
```

### Acesso
Abra seu navegador e acesse: `http://127.0.0.1:5000`

## Estrutura do Projeto

```
google_reviews_app/
├── src/
│   ├── main.py                 # Aplicativo principal
│   ├── templates/              # Templates HTML
│   │   ├── base.html          # Template base
│   │   ├── index.html         # Página inicial
│   │   ├── locations.html     # Lista de locais
│   │   └── reviews.html       # Lista de avaliações
│   └── static/                # Arquivos estáticos
│       ├── css/
│       │   └── style.css      # Estilos CSS
│       └── js/
│           └── script.js      # JavaScript
├── client_secrets.json        # Credenciais OAuth (criar)
├── .env                       # Variáveis de ambiente (criar)
├── requirements.txt           # Dependências Python
└── README.md                  # Este arquivo
```

## Guia de Uso

### 1. Primeiro Acesso
1. Execute o aplicativo
2. Clique em "Entrar com Google"
3. Autorize o acesso às suas contas do Google My Business
4. Aguarde o carregamento dos seus perfis de empresa

### 2. Gerenciando Avaliações
1. Selecione um perfil de empresa
2. Visualize todas as avaliações recebidas
3. Use filtros para encontrar avaliações específicas
4. Clique em uma avaliação para ver detalhes

### 3. Respondendo com IA
1. Na página de uma avaliação, clique em "Sugerir Resposta"
2. Aguarde a IA gerar uma sugestão personalizada
3. Edite a sugestão conforme necessário
4. Clique em "Enviar Resposta" para publicar

### 4. Resposta Manual
1. Na página de uma avaliação, digite sua resposta no campo de texto
2. Use o preview para verificar a formatação
3. Clique em "Enviar Resposta" para publicar

## Solução de Problemas

### Problemas Comuns

#### `ModuleNotFoundError: No module named 'flask'`
**Solução**: Ative o ambiente virtual e instale as dependências
```bash
.\venv\Scripts\Activate.ps1  # Windows
pip install flask
```

#### `Arquivo 'client_secrets.json' não encontrado`
**Solução**: Baixe o arquivo de credenciais do Google Cloud Console e coloque na pasta raiz

#### `RuntimeError: A sessão está indisponível`
**Solução**: Adicione uma chave secreta ao Flask
```python
app.secret_key = "sua_chave_secreta_unica"
```

#### `jinja2.exceptions.TemplateNotFound`
**Solução**: Verifique se os templates estão na pasta correta
```python
app = Flask(__name__, template_folder='templates')
```

#### Acesso bloqueado pelo Google
**Solução**: Adicione seu e-mail como testador na tela de consentimento OAuth ou use "Avançado" > "Ir para [app] (não seguro)"

### Logs e Debug
Para habilitar logs detalhados:
```python
import logging
logging.basicConfig(level=logging.DEBUG)
```

## Configuração Avançada

### Variáveis de Ambiente
Crie um arquivo `.env` na raiz do projeto:
```env
GEMINI_API_KEY=sua_chave_api_gemini
FLASK_ENV=development
FLASK_DEBUG=True
SECRET_KEY=sua_chave_secreta_flask
```

### Personalização da IA
Edite os prompts no arquivo `main.py` para personalizar o comportamento da IA:
```python
def generate_ai_response(review_text, rating, business_type="geral"):
    prompt = f"""
    Como especialista em atendimento ao cliente, gere uma resposta profissional 
    para esta avaliação de {rating} estrelas de um negócio do tipo {business_type}:
    
    "{review_text}"
    
    A resposta deve ser:
    - Profissional e empática
    - Específica ao conteúdo da avaliação
    - Adequada ao rating recebido
    - Em português brasileiro
    """
```

### Deploy em Produção

#### Heroku
```bash
# Criar Procfile
echo "web: python src/main.py" > Procfile

# Deploy
heroku create seu-app-name
git push heroku main
```

#### Google Cloud Run
```bash
# Criar Dockerfile
# Build e deploy
gcloud run deploy --source .
```

## Contribuição

### Como Contribuir
1. Fork o repositório
2. Crie uma branch para sua feature (`git checkout -b feature/nova-funcionalidade`)
3. Commit suas mudanças (`git commit -am 'Adiciona nova funcionalidade'`)
4. Push para a branch (`git push origin feature/nova-funcionalidade`)
5. Abra um Pull Request

### Diretrizes
- Siga as convenções de código Python (PEP 8)
- Adicione testes para novas funcionalidades
- Atualize a documentação conforme necessário
- Mantenha compatibilidade com versões anteriores

## Licença

Este projeto é licenciado sob a Licença MIT - veja o arquivo [LICENSE](LICENSE) para detalhes.

## Suporte

### Documentação
- [Documentação Técnica Completa](documentacao_tecnica.md)
- [Site Oficial do Projeto](https://seu-site-oficial.com)

### Comunidade
- [Issues no GitHub](https://github.com/seu-usuario/google-reviews-app/issues)
- [Discussões](https://github.com/seu-usuario/google-reviews-app/discussions)

### Contato
- Email: suporte@seu-dominio.com
- Website: https://seu-site.com

## Agradecimentos

- Google Cloud Platform pelas APIs robustas
- Google AI pela API Gemini
- Comunidade Flask pela documentação excelente
- Todos os contribuidores do projeto

---

**Desenvolvido com ❤️ para a comunidade empresarial brasileira**

