# If you come from bash you might have to change your $PATH.

# export PATH=$HOME/bin:$HOME/.local/bin:/usr/local/bin:$PATH

# Path to your Oh My Zsh installation.

export ZSH="$HOME/.oh-my-zsh"
# Set name of the theme to load --- if set to "random", it will
# load a random theme each time Oh My Zsh is loaded, in which case,
# to know which specific one was loaded, run: echo $RANDOM_THEME
# See https://github.com/ohmyzsh/ohmyzsh/wiki/Themes
ZSH_THEME="spaceship"
plugins=(
  git 
  z 
  zsh-autosuggestions 
  zsh-syntax-highlighting
)


SPACESHIP_GIT_ASYNC=false


SPACESHIP_VENV_SHOW=true

SPACESHIP_VENV_GENERIC_NAMES=()

SPACESHIP_CHAR_SYMBOL="🐺 ➜ "        # Aqui você define o desenho da seta

manage_power() {
    if [ -f /sys/class/power_supply/ADP0/online ]; then
        local AC_STATUS=$(cat /sys/class/power_supply/ADP0/online)
        local BAT_LEVEL=$(cat /sys/class/power_supply/BAT0/capacity)
        if [[ "$AC_STATUS" == "1" ]]; then
            powerprofilesctl set performance
        else
            [[ "$BAT_LEVEL" -le 30 ]] && powerprofilesctl set power-saver || powerprofilesctl set balanced
        fi
    fi
}
manage_power


source $ZSH/oh-my-zsh.sh
SPACESHIP_PROMPT_ORDER=(dir venv python java package git line_sep char)
SPACESHIP_CHAR_COLOR_SUCCESS="magenta"
SPACESHIP_CHAR_COLOR_FAILURE="red"
SPACESHIP_DIR_COLOR="cyan"
SPACESHIP_VENV_SYMBOL="🐍 "
SPACESHIP_VENV_COLOR="yellow"
SPACESHIP_GIT_ASYNC=false
# Configuração da Seta (Char)


SPACESHIP_CHAR_COLOR_SUCCESS="magenta" # Cor quando o comando dá certo

SPACESHIP_CHAR_COLOR_FAILURE="red" 

SPACESHIP_PROMPT_ORDER=(

  dir

  venv

  python

  java

#  cpp

  package

  git

  line_sep

  char

)

alias game=" jstest-gtk"

# Controle Manual do Docker - Matheus
# Controle Manual do Docker - Com exigência de senha
alias d-on="sudo systemctl start docker docker.socket && echo '🐳 Docker subindo...'"
alias d-onw="sudo systemctl start docker docker.socket && sudo chmod 666 /var/run/docker.sock && echo '🐳 Docker e Whaler Prontos!'"
alias d-onv="sudo systemctl start docker docker.socket && sudo chmod 666 /var/run/docker.sock && echo '🐳 Docker e VS Code conectados!'"
alias d-off="sudo systemctl stop docker docker.socket && echo '💤 Docker desligado (RAM liberada!)'"
alias d-status="systemctl status docker"

# Atalho para rodar comandos docker com sudo mais rápido
alias dk="sudo docker"
# 2. Configuração de Cores (Tudo para Roxo)

SPACESHIP_VENV_COLOR="magenta"

SPACESHIP_PYTHON_COLOR="magenta"

SPACESHIP_JAVA_COLOR="magenta"

SPACESHIP_CPP_COLOR="magenta"

SPACESHIP_PACKAGE_COLOR="magenta" # Para projetos Web/HTML

SPACESHIP_DIR_COLOR="cyan"       # Deixei a pasta em ciano para destacar do roxo


# 3. Garantir que apareçam sempre que houver arquivos

SPACESHIP_PYTHON_SHOW=true

SPACESHIP_JAVA_SHOW=true

SPACESHIP_CPP_SHOW=true

SPACESHIP_PACKAGE_SHOW=true


# Configurações específicas do VENV

SPACESHIP_VENV_GENERIC_NAMES=() # Remove o filtro que esconde nomes comuns como .venv

SPACESHIP_VENV_COLOR="yellow"

SPACESHIP_VENV_SYMBOL="🐍 "


# Configurações do GIT

SPACESHIP_GIT_SHOW=true

SPACESHIP_GIT_ASYNC=false # Desativa o modo assíncrono para carregar na hora


# Definindo o ícone para Jupyter Notebooks

SPACESHIP_IPYNB_SYMBOL="📓 "  # Ou use "🤖 " para Machine Learning

SPACESHIP_IPYNB_COLOR="magenta" # Roxo como você pediu


# --- Configurações de Emojis e Cores ---



# JAVA (Aparece se tiver arquivo .java ou .jar)


SPACESHIP_JAVA_SHOW=true


SPACESHIP_JAVA_SYMBOL="☕"


SPACESHIP_JAVA_COLOR="magenta"

export JAVA_HOME=/usr/lib/jvm/java-21-openjdk-amd64

# PYTHON (Aparece se tiver .py ou venv)


SPACESHIP_PYTHON_SHOW=true


SPACESHIP_PYTHON_SYMBOL="🐍 "


SPACESHIP_PYTHON_COLOR="magenta"



# HTML / JAVASCRIPT / CSS (Detecta via package.json)


SPACESHIP_PACKAGE_SHOW=true


SPACESHIP_PACKAGE_SYMBOL="🌐 "


SPACESHIP_PACKAGE_COLOR="magenta"



# C++ (Geralmente via GCC ou arquivos de sistema)


SPACESHIP_GCC_SHOW=true


SPACESHIP_GCC_SYMBOL="⚙️ "


SPACESHIP_GCC_COLOR="magenta"




export VIRTUAL_ENV_DISABLE_PROMPT=1



# --- Meus Atalhos (Aliases) ---


# Python Venv - Ativa o .venv da pasta atual em 1 segundo
alias py='python3'
alias venv='python3 -m venv venv'
# Alias AV inteligente (Tenta .venv primeiro, depois venv)
alias av='[ -d .venv ] && source .venv/bin/activate || source venv/bin/activate'
alias py-clean='find . -type d -name "__pycache__" -exec rm -rf {} +'
export VIRTUAL_ENV_DISABLE_PROMPT=1 # O Spaceship já mostra o venv, não precisa do padrão
# Java - Compila e Executa com um comando só

# Exemplo: jrun MeuPrograma.java

jrun() { javac "$1" && java "${1%.*}"; }


# C++ - Compila com o padrão moderno e executa

# Exemplo: crun main.cpp

crun() { g++ -std=c++17 "$1" -o app && ./app; }


# Git - Atalhos rápidos

alias gs='git status'

alias gp='git pull'




# Personalizar a cor de comandos corretos para um verde limão brilhante
# Monitoramento de Bateria e Hardware
# Mostra TUDO: Saúde, ciclos, voltagem, fabricante e tempo restante
alias bat-info='upower -i /org/freedesktop/UPower/devices/battery_BAT0'
alias bat-health='upower -i /org/freedesktop/UPower/devices/battery_BAT0 | grep -E "capacity|energy-full-design"'
# Monitora CPU (Tctl), Placa-mãe e GPU integrada a cada 1 segundo
alias mem='free -h --si'
# Lê a temperatura direto dos arquivos térmicos do sistema
# Mostra apenas a temperatura principal seguida de um 'C' e encerra
alias temp='printf "%.0f C\n" $(awk "{print \$1/1000}" /sys/class/thermal/thermal_zone0/temp)'
# Atalhos para o Modo de Conservação (O limite de 80%)
alias bat-on='echo 1 | sudo tee /sys/bus/platform/drivers/ideapad_acpi/VPC2004:00/conservation_mode'
alias bat-off='echo 0 | sudo tee /sys/bus/platform/drivers/ideapad_acpi/VPC2004:00/conservation_mode'

# alias bat-status='
#   echo "--- 🔋 STATUS DA BATERIA ---";
#   MODE=$(cat /sys/bus/platform/drivers/ideapad_acpi/VPC2004:00/conservation_mode);
#   if [ "$MODE" = "1" ]; then 
#     echo "🟢 Modo de Conservação: ATIVADO (Limite 75-80%)";
#   else 
#     echo "⚪ Modo de Conservação: DESATIVADO (Carga Total)";
#   fi;
#   upower -i /org/freedesktop/UPower/devices/battery_BAT0 | grep -E "state|percentage|capacity" | sed "s/state/Estado/" | sed "s/percentage/Carga/" | sed "s/capacity/Saúde (Vida Útil)/"
# '

bat-status() {
    echo "--- 🔋 STATUS DA BATERIA ---"
    
    # 1. Verifica o modo de conservação
    local MODE=$(cat /sys/bus/platform/drivers/ideapad_acpi/VPC2004:00/conservation_mode)
    if [ "$MODE" = "1" ]; then 
        echo "🟢 Modo de Conservação: ATIVADO (Limite 80%)"
    else 
        echo "⚪ Modo de Conservação: DESATIVADO (Carga Total)"
    fi

    # 2. Extrai dados do upower
    local DATA=$(upower -i /org/freedesktop/UPower/devices/battery_BAT0)
    
    # Limpando espaços e pegando o valor exato
    local STATE=$(echo "$DATA" | grep -E "^\s*state:" | awk '{print $2}' | tr -d '[:space:]')
    local PERCENT=$(echo "$DATA" | grep -E "^\s*percentage:" | awk '{print $2}')
    local CAPACITY=$(echo "$DATA" | grep -E "^\s*capacity:" | awk '{print $2}')
    local TIME_EMPTY=$(echo "$DATA" | grep "time to empty" | sed 's/.*: //')
    local TIME_FULL=$(echo "$DATA" | grep "time to full" | sed 's/.*: //')

    # 3. Lógica de Fonte (Muito mais confiável agora)
    echo -n "🔌 Fonte: "
    if [ "$STATE" = "discharging" ]; then
        echo "BATERIA"
    else
        echo "REDE ELÉTRICA"
    fi

    # 4. Informações de Carga e Saúde
    echo "⚡ Carga Atual: $PERCENT"
    echo "❤️ Saúde (Vida Útil): $CAPACITY"

    # 5. Lógica de Tempo Estimado
    if [ "$STATE" = "discharging" ]; then
        echo "⏳ Tempo para descarga total: ${TIME_EMPTY:-Calculando...}"
    elif [ "$STATE" = "charging" ]; then
        echo "⏳ Tempo para carga completa: ${TIME_FULL:-Calculando...}"
    elif [ "$STATE" = "pending-charge" ]; then
        echo "⏳ Status: Em espera (bateria no limite configurado)."
    elif [ "$STATE" = "fully-charged" ]; then
        echo "⏳ Status: Usando a rede eletrica e bateria carregada total ${TIME_FULL:-Calculando...}"
    fi
}

# bat-on(){
#     bat-o    
#     bat-status


# }

# bat-off(){
#     bat-of
#     bat-status

# }

bat() {
    case "$1" in
        on)
            echo 1 | sudo tee /sys/bus/platform/drivers/ideapad_acpi/VPC2004:00/conservation_mode > /dev/null
            echo "✅ Modo de Conservação ATIVADO."
            bat-status
            ;;
        off)
            echo 0 | sudo tee /sys/bus/platform/drivers/ideapad_acpi/VPC2004:00/conservation_mode > /dev/null
            echo "❌ Modo de Conservação DESATIVADO."
            bat-status
            ;;
        status)
            bat-status
            ;;
        *)
            echo "Uso: bat {on|off|status}"
            ;;
    esac
}



# Gerenciamento de Energia Dinâmico - Lenovo Slim 3

# Configurações do Spaceship para Bateria
SPACESHIP_BATTERY_SHOW=always
SPACESHIP_BATTERY_THRESHOLD=30  # Fica vermelho abaixo de 30%
# Python e Venv
alias py='python3'
alias venv='python3 -m venv venv'
alias av='source venv/bin/activate'

# Limpeza de arquivos temporários do Python
alias py-clean='find . -type d -name "__pycache__" -exec rm -rf {} +'

# Git ultra-rápido
alias gs='git status'
alias ga='git add .'
alias gc='git commit -m'
alias gp='git push'
alias gpl='git pull'
alias gl='git log --oneline --graph --all'
# Trocar de branch
alias gco='git checkout'
alias gcb='git checkout -b'

# Ver branches
alias gb='git branch'

# Histórico em Log "Bonito" (Exibe como um grafo colorido)
alias gl='git log --oneline --graph --all'
# Adiciona tudo, commita com uma mensagem e sobe pro GitHub em um comando só
# Exemplo: gcap "ajuste no modelo de ML"
gitup() {
#   git status
  git add -A
 if git commit -m "$1"; then
    git push
  else
    echo "⚠️  Nada para subir (repositório já está limpo)."
  fi
  git status
}
# Reset suave: desfaz o commit mas mantém as mudanças nos arquivos
alias grsoft='git reset --soft HEAD~1'

# Reset total: volta tudo ao normal e limpa o terminal
alias grclean='git restore . && git clean -df'
# Automação Total Python (avp = Activate, Verify & Play)
avp() {
    # 1. Verifica se a venv existe, se não, cria uma
    if [ ! -d ".venv" ] && [ ! -d "venv" ]; then
        echo "✨ Criando ambiente virtual..."
        python3 -m venv .venv
    fi

    # 2. Automação do .gitignore (Garante que a venv não suba para o Git)
    if [ ! -f ".gitignore" ]; then
        echo "📄 Criando .gitignore e ignorando ambientes virtuais..."
        echo ".venv/\nvenv/\n__pycache__/\n*.pyc" > .gitignore
    else
        # Se o .gitignore existe, verifica se a venv já está lá dentro
        if ! grep -q ".venv/" .gitignore; then
            echo "📝 Adicionando .venv ao .gitignore existente..."
            echo "\n# Python Virtual Env\n.venv/\nvenv/" >> .gitignore
        fi
    fi

    # 3. Ativa o ambiente (prioriza .venv)
    if [ -d ".venv" ]; then
        source .venv/bin/activate
    else
        source venv/bin/activate
    fi

    # 4. Atualiza o pip silenciosamente
    pip install --upgrade pip --quiet
    pip install rich
    # 5. Se houver requirements.txt, instala as dependências novas
    if [ -f "requirements.txt" ]; then
        echo "📦 Instalando/Atualizando dependências..."
        pip install -r requirements.txt --quiet
    fi

    # 6. Executa o arquivo principal se ele existir
    if [ -f "main.py" ]; then
        echo "🚀 Executando main.py..."
        python main.py
    elif [ -f "app.py" ]; then
        echo "🚀 Executando app.py..."
        python app.py
    else
        echo "✅ Ambiente pronto! (Nenhum arquivo principal encontrado)"
    fi
}
# Python Run (prun) - Roda o arquivo passado ou o último modificado
prun() {
    # Se você passou um nome de arquivo (ex: prun main.py), ele usa ele
    if [ -n "$1" ]; then
        python "$1"
    else
        # Se não passou nada, ele procura o arquivo .py mais recente que foi mexido na pasta
        # Isso simula o "F5" no arquivo que você provavelmente está editando
        local latest_file=$(ls -t *.py 2>/dev/null | head -n 1)
        
        if [ -n "$latest_file" ]; then
            echo "🚀 Rodando o mais recente: $latest_file"
            python "$latest_file"
        else
            echo "❌ Nenhum arquivo .py encontrado nesta pasta."
        fi
    fi
}
# Rodar notebook como script rápido
alias nrun='jupyter nbconvert --to script --execute --stdout'
# --- Automação de Dependências PIP ---

# 1. 'pygen' (Python Generate): Cria ou atualiza o requirements.txt
alias pygen='pip freeze > requirements.txt && echo "✅ requirements.txt atualizado!"'

# 2. 'pyinst' (Python Install): Faz o check e instala tudo sozinho

pyinst() {
    echo "🔍 Escaneando diretório (Scripts e Notebooks)..."
    
    # 1. Garante que as ferramentas de scan estão presentes
    pip install pipreqs pipreqsnb --quiet

    # 2. Usa o pipreqsnb para varrer TUDO (.py e .ipynb)
    # Ele gera um arquivo temporário para não sujar sua pasta
    pipreqsnb . --savepath /tmp/missing_reqs.txt --force > /dev/null 2>&1

    if [ -s /tmp/missing_reqs.txt ]; then
        echo "📦 Bibliotecas detectadas no seu código!"
        echo "📥 Iniciando instalação..."
        
        # 3. Instala o que foi encontrado
        pip install -r /tmp/missing_reqs.txt
        
        # 4. Limpa e atualiza seu requirements.txt oficial
        rm /tmp/missing_reqs.txt
        pip freeze > requirements.txt
        echo "✅ Ambiente atualizado com sucesso!"
    else
        echo "✨ Tudo em ordem! Nenhuma biblioteca nova encontrada nos Notebooks."
    fi
}
pyinstp() {
    local target_file=""

    # 1. Define o alvo: ou o parâmetro $1 ou o .py mais recente
    if [ -n "$1" ]; then
        target_file="$1"
    else
        target_file=$(ls -t *.py 2>/dev/null | head -n 1)
    fi

    if [ -z "$target_file" ]; then
        echo "❌ Nenhum arquivo .py encontrado."
        return 1
    fi

    echo "🔍 Analisando dependências em: $target_file"

    # 2. Usa o pipreqs de forma cirúrgica apenas para este arquivo
    # Criamos uma pasta temporária porque o pipreqs exige uma pasta como entrada
    local tmp_dir=$(mktemp -d)
    cp "$target_file" "$tmp_dir/"
    
    # Executa o scan apenas naquela pasta com um único arquivo
    pip install pipreqs --quiet
    pipreqs "$tmp_dir" --force --savepath /tmp/single_reqs.txt > /dev/null 2>&1

    if [ -s /tmp/single_reqs.txt ]; then
        echo "📦 Bibliotecas faltantes detectadas:"
        cat /tmp/single_reqs.txt
        echo "📥 Instalando..."
        pip install -r /tmp/single_reqs.txt
        echo "✅ Concluído para $target_file!"
    else
        echo "✨ O arquivo já parece estar com todas as dependências em ordem (ou são bibliotecas nativas)."
    fi

    # Limpeza
    rm -rf "$tmp_dir"
    [ -f /tmp/single_reqs.txt ] && rm /tmp/single_reqs.txt
}
# Listar dependências de forma organizada
alias pylist='pip list'

# Ver a árvore de dependências (se tiver o pipdeptree instalado)
pytree() {
    # Verifica se o comando pipdeptree está disponível no ambiente atual
    if ! command -v pipdeptree &> /dev/null; then
        echo "🔍 'pipdeptree' não encontrado no seu .venv."
        echo "📥 Instalando para você agora..."
        pip install pipdeptree --quiet
    fi

    # Executa o comando e passa qualquer argumento que você digitar (ex: pytree -p pandas)
    pipdeptree "$@"
}
# Desfazer o último commit (mantendo os arquivos alterados)
alias guncommit='git reset --soft HEAD~1'
# Configuração do Pyenv
export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init - zsh)"

# Se você instalou o plugin virtualenv do pyenv:
eval "$(pyenv virtualenv-init - zsh)"

# Função para criar um arquivo .drawio básico e estruturado
create_drawio_file() {
    # Se não passar nenhum nome, define um padrão com a data atual
    local filename="${1:-diagrama_$(date +%Y%m%d_%H%M%S)}"
    
    # Garante que o arquivo terá a extensão .drawio
    if [[ "$filename" != *.drawio ]]; then
        filename="${filename}.drawio"
    fi

    # Estrutura XML mínima e válida que o Draw.io reconhece nativamente
    cat <<EOF > "$filename"
<mxfile host="Electron" modified="$(date -u +"%Y-%m-%dT%H:%M:%SZ")" agent="ZshScript" version="20.0.0" type="device">
  <diagram id="layout_base" name="Página-1">
    <mxGraphModel dx="1000" dy="1000" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="827" pageHeight="1169" math="0" shadow="0">
      <root>
        <mxCell id="0" />
        <mxCell id="1" parent="0" />
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
EOF

    echo "🎨 Arquivo criado com sucesso: \${filename}"
}

# Alias para permitir a sintaxe "new draw"
alias new_draw="create_drawio_file"

alias av='[ -d .venv ] && source .venv/bin/activate || [ -d venv ] && source venv/bin/activate || echo '
alias dv='deactivate'
# Comandos para o PostgreSQL
alias db-start="sudo systemctl start postgresql"
alias db-stop="sudo systemctl stop postgresql"
alias db-status="systemctl status postgresql"
# Set list of themes to pick from when loading at random
# Setting this variable when ZSH_THEME=random will cause zsh to load
# a theme from this variable instead of looking in $ZSH/themes/
# If set to an empty array, this variable will have no effect.
# ZSH_THEME_RANDOM_CANDIDATES=( "robbyrussell" "agnoster" )

# Uncomment the following line to use case-sensitive completion.
# CASE_SENSITIVE="true"

# Uncomment the following line to use hyphen-insensitive completion.
# Case-sensitive completion must be off. _ and - will be interchangeable.
# HYPHEN_INSENSITIVE="true"

# Uncomment one of the following lines to change the auto-update behavior
# zstyle ':omz:update' mode disabled  # disable automatic updates
# zstyle ':omz:update' mode auto      # update automatically without asking
# zstyle ':omz:update' mode reminder  # just remind me to update when it's time

# Uncomment the following line to change how often to auto-update (in days).~/.zshrc
# zstyle ':omz:update' frequency 13

# Uncomment the following line if pasting URLs and other text is messed up.
# DISABLE_MAGIC_FUNCTIONS="true"

# Uncomment the following line to disable colors in ls.
# DISABLE_LS_COLORS="true"

# Uncomment the following line to disable auto-setting terminal title.
# DISABLE_AUTO_TITLE="true"

# Uncomment the following line to enable command auto-correction.
# ENABLE_CORRECTION="true"

# Uncomment the following line to display red dots whilst waiting for completion.
# You can also set it to another string to have that shown instead of the default red dots.
# e.g. COMPLETION_WAITING_DOTS="%F{yellow}waiting...%f"
# Caution: this setting can cause issues with multiline prompts in zsh < 5.7.1 (see #5765)
# COMPLETION_WAITING_DOTS="true"

# Uncomment the following line if you want to disable marking untracked files
# under VCS as dirty. This makes repository status check for large repositories
# much, much faster.
# DISABLE_UNTRACKED_FILES_DIRTY="true"

# Uncomment the following line if you want to change the command execution time
# stamp shown in the history command output.
# You can set one of the optional three formats:
# "mm/dd/yyyy"|"dd.mm.yyyy"|"yyyy-mm-dd"
# or set a custom format using the strftime function format specifications,
# see 'man strftime' for details.
# HIST_STAMPS="mm/dd/yyyy"

# Would you like to use another custom folder than $ZSH/custom?
# ZSH_CUSTOM=/path/to/new-custom-folder

# Which plugins would you like to load?
# Standard plugins can be found in $ZSH/plugins/
# Custom plugins may be added to $ZSH_CUSTOM/plugins/
# Example format: plugins=(rails git textmate ruby lighthouse)
# Add wisely, as too many plugins slow down shell startup.
plugins=(git)
plugins=(git z zsh-autosuggestions zsh-syntax-highlighting)

source $ZSH/oh-my-zsh.sh
# User configuration

# export MANPATH="/usr/local/man:$MANPATH"

# You may need to manually set your language environment
# export LANG=en_US.UTF-8

# Preferred editor for local and remote sessions
# if [[ -n $SSH_CONNECTION ]]; then
#   export EDITOR='vim'
# else
#   export EDITOR='nvim'
# fi

# Compilation flags
# export ARCHFLAGS="-arch $(uname -m)"

# Set personal aliases, overriding those provided by Oh My Zsh libs,
# plugins, and themes. Aliases can be placed here, though Oh My Zsh
# users are encouraged to define aliases within a top-level file in
# the $ZSH_CUSTOM folder, with .zsh extension. Examples:
# - $ZSH_CUSTOM/aliases.zsh
# - $ZSH_CUSTOM/macos.zsh
# For a full list of active aliases, run `alias`.
#
# Example aliases
# alias zshconfig="mate ~/.zshrc"
# alias ohmyzsh="mate ~/.oh-my-zsh"

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

