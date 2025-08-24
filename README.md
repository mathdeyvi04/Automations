# Sumário

- [Objetivo](#objetivo)
- [Absorção de Caminho](#absorção-de-caminho)
- [Tag de Caminho](#tag-de-caminho)

# Objetivo

Reunir e disponibilizar códigos e scripts específicos capazez de oferecer conveniências em ambiente Linux.

Códigos `bash` triviais apenas serão acrescentados e descritos neste arquivo, enquanto códigos mais complexos estarão apenas descritos e suas pastas referenciadas.

# Absorção de Caminho

Desejamos solucionar o problema: Cada terminal apresentado apresenta o _nome de usuário_, 
_nome do dispositivo_ e _caminho completo do diretório presente_, o que por vezes é muito chato.

![](https://github.com/user-attachments/assets/4540e197-ab8a-44a1-b289-00dbad64bfb1)

Sendo assim, apresentarei uma forma de solucionar este problema. Estarei enviando as imagens para demonstrar 
como até as cores das letras podem ser alteradas.

- Execute o comando `nano ~/.bashrc`. 
  - Isso abrirá um arquivo no sistema linux responsável por personalizar e configurar o ambiente do terminal.
- Adicione ao final do código: `export PS1='\033[1;32m\W\033[1;34m\$\033[0m '`
- Salve e execute `source ~/.bashrc`

Você terá:

![](https://github.com/user-attachments/assets/7201ef2c-5abd-4585-80ef-c8a28c0b0c14)

Observe o diagrama de cores e como há apenas o nome do diretório atual.
Caso você deseje adicionar mais informações e mais cores, é possível:

```
\u    # Nome do usuário
\h    # Nome do host (máquina)
\H    # Nome completo do host
\w    # Caminho completo do diretório
\W    # Nome do diretório atual (basename)
\s    # Nome do shell (bash, zsh, etc.)
\v    # Versão do bash
\V    # Versão completa do bash
\$    # "#" para root, "$" para usuários normais
\!    # Número do comando no histórico
\@    # Hora atual em formato AM/PM
\A    # Hora atual (24h) sem segundos
\t    # Hora completa (24h:min:seg)
\d    # Data no formato "Dia da Semana Mês Dia"
```

# Tag de Caminho

Por vezes, acessar um determinado diretório é uma tarefa difícil, pois exige que um caminho seja
percorrido utilizando `cd` e `ls` diversas vezes.

Entretanto, é interessante utilizar `alias=` para evitar percorrer os comandos. Utilizando essa ferramenta,
torna-se possível apenas digitar o nome desejado da pasta e o terminal será automaticamente direcionado
para ela.

- Execute o comando `nano ~/.bashrc`. 
  - Isso abrirá um arquivo no sistema linux responsável por personalizar e configurar o ambiente do terminal.

- Adicione ao arquivo:

```
#######################################
# Cria um `alias` para o diretório de execução,
# automatiza o `source ~/.bashrc`.
# Caso seja digitado um `alias` já existente, haverá 
# erro de ambiguidade, logo atente-se a isso.
# 
# Argumentos:
#   $1 - Nome Desejado Para Alias do Diretório
#
# Returno:
#   Nada
#######################################
add_alias(){
  local name=$1

  if [ -z "$name" ]; then
    echo "Faltando nome de alias"
    return 1
  fi

  echo "alias '$name'='cd $(pwd)'" >> ~/.bashrc

  source ~/.bashrc
}
```
- Execute `source ~/.bashrc`

A partir disso, encontrar seus diretórios de trabalho será muito mais fácil.

Para deletar determinados `alias`, basta abrir novamente `bashrc` e apagar a linha correspondente.










