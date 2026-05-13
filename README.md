
![Banner Dark Tech](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExYzd4eXg2dGh1dXYzM24xdjB3aXd1OW4zYjN2MHE2bmlqYXlkMHBiNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/h0AhBLqVKfha8/giphy.gif)


# 🐧 Guia de Gerenciamento de Discos no Linux

[cite_start]Este repositório contém um guia prático e objetivo sobre os comandos essenciais para a administração de dispositivos de armazenamento em sistemas Linux[cite: 2, 53]. [cite_start]Gerenciar discos segue uma lógica linear, comparável à organização de um armário: verificar o hardware, dividir o espaço, preparar o terreno e definir o local de uso[cite: 3, 4, 54].

---

## 🛠️ Fluxo de Trabalho (Passo a Passo)

| Ordem | Comando | Descrição Prática |
| :--- | :--- | :--- |
| **1º** | `lsblk` | [cite_start]Localiza e identifica se o disco novo foi reconhecido pelo sistema[cite: 20, 56]. |
| **2º** | `fdisk` | [cite_start]Cria o espaço ou as partições necessárias no dispositivo[cite: 21, 57]. |
| **3º** | `mkfs` | [cite_start]Realiza a formatação, definindo o Sistema de Arquivos[cite: 21, 58]. |
| **4º** | `mkdir` | [cite_start]Cria a pasta que servirá como ponto de montagem[cite: 22, 59]. |
| **5º** | `mount` | [cite_start]Ativa o acesso ao disco, ligando o hardware à pasta criada[cite: 22, 60]. |

---

## 📖 Detalhamento dos Comandos

### 1. Localização e Identificação
[cite_start]Antes de qualquer alteração, é fundamental identificar o nome atribuído ao dispositivo (ex: `/dev/sdb`)[cite: 5, 61].
* [cite_start]**`lsblk`**: Exibe a árvore de dispositivos em blocos para confirmar o reconhecimento e o tamanho do disco[cite: 6, 62].

### 2. Particionamento (O "Corte")
* [cite_start]**`fdisk`**: Ferramenta interativa utilizada para a criação da tabela de partições[cite: 8, 63].
    * [cite_start]**Uso comum**: `sudo fdisk /dev/sdb`[cite: 9, 64].
    * [cite_start]**Comandos internos**: `n` (nova partição), `w` (gravar e sair) e `p` (listar partições)[cite: 9, 65].

### 3. Formatação (O Sistema de Arquivos)
[cite_start]Define o formato que o sistema operacional utilizará para ler e gravar dados (ex: ext4, xfs)[cite: 10, 66].
* [cite_start]**`mkfs`**: Transforma a partição bruta em um volume utilizável[cite: 11, 67].
    * [cite_start]**Exemplo**: `sudo mkfs.ext4 /dev/sdb1` (Formata a primeira partição do disco B)[cite: 12, 68].

### 4. Preparação do Ponto de Montagem
[cite_start]No Linux, os discos devem ser vinculados a diretórios específicos para serem acessados[cite: 13, 14, 69].
* [cite_start]**`mkdir`**: Cria o diretório que servirá de destino[cite: 14, 70].
    * [cite_start]**Dica**: Recomenda-se o uso de `/mnt` ou `/media` (Ex: `sudo mkdir /mnt/meu_disco`)[cite: 15, 71].

### 5. Montagem e Uso
* [cite_start]**`mount`**: Realiza a ligação efetiva entre a partição e a pasta[cite: 16, 72].
    * [cite_start]**Exemplo**: `sudo mount /dev/sdb1 /mnt/meu_disco`[cite: 17, 73].
* [cite_start]**`umount`**: Desconecta o dispositivo com segurança[cite: 17, 74].
    * [cite_start]**Nota**: Escreve-se **`umount`** (sem o primeiro 'n')[cite: 18, 75].

---

## 💡 Informações Importantes

* [cite_start]**Persistência**: O comando `mount` é temporário; a ligação é desfeita ao reiniciar o sistema[cite: 24, 77].
* [cite_start]**Montagem Permanente**: Para que o disco seja montado automaticamente no boot, é necessário configurar o arquivo `/etc/fstab`[cite: 25, 78].
