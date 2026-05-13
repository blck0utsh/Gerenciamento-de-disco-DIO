
![Banner Dark Tech](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExYzd4eXg2dGh1dXYzM24xdjB3aXd1OW4zYjN2MHE2bmlqYXlkMHBiNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/h0AhBLqVKfha8/giphy.gif)


# 🐧 Guia de Gerenciamento de Discos no Linux

Este repositório contém um guia prático e objetivo sobre os comandos essenciais para a administração de dispositivos de armazenamento em sistemas Linux. Gerenciar discos segue uma lógica linear, comparável à organização de um armário: verificar o hardware, dividir o espaço, preparar o terreno e definir o local de uso.

---

## 🛠️ Fluxo de Trabalho (Passo a Passo)

| Ordem | Comando | Descrição Prática |
| :--- | :--- | :--- |
| **1º** | `lsblk` | Localiza e identifica se o disco novo foi reconhecido pelo sistema. |
| **2º** | `fdisk` | Cria o espaço ou as partições necessárias no dispositivo. |
| **3º** | `mkfs` | Realiza a formatação, definindo o Sistema de Arquivos. |
| **4º** | `mkdir` | Cria a pasta que servirá como ponto de montagem. |
| **5º** | `mount` | Ativa o acesso ao disco, ligando o hardware à pasta criada. |

---

## 📖 Detalhamento dos Comandos

### 1. Localização e Identificação
Antes de qualquer alteração, é fundamental identificar o nome atribuído ao dispositivo (ex: `/dev/sdb`).
* **`lsblk`**: Exibe a árvore de dispositivos em blocos para confirmar o reconhecimento e o tamanho do disco.

### 2. Particionamento (O "Corte")
* **`fdisk`**: Ferramenta interativa utilizada para a criação da tabela de partições.
    * **Uso comum**: `sudo fdisk /dev/sdb`.
    * **Comandos internos**: `n` (nova partição), `w` (gravar e sair) e `p` (listar partições).

### 3. Formatação (O Sistema de Arquivos)
Define o formato que o sistema operacional utilizará para ler e gravar dados (ex: ext4, xfs).
* **`mkfs`**: Transforma a partição bruta em um volume utilizável.
    * **Exemplo**: `sudo mkfs.ext4 /dev/sdb1` (Formata a primeira partição do disco B).

### 4. Preparação do Ponto de Montagem
No Linux, os discos devem ser vinculados a diretórios específicos para serem acessados.
* **`mkdir`**: Cria o diretório que servirá de destino.
    * **Dica**: Recomenda-se o uso de `/mnt` ou `/media` (Ex: `sudo mkdir /mnt/meu_disco`).

### 5. Montagem e Uso
* **`mount`**: Realiza a ligação efetiva entre a partição e a pasta.
    * **Exemplo**: `sudo mount /dev/sdb1 /mnt/meu_disco`.
* **`umount`**: Desconecta o dispositivo com segurança.
    * **Nota**: Escreve-se **`umount`** (sem o primeiro 'n').

---

## 💡 Informações Importantes

* **Persistência**: O comando `mount` é temporário; a ligação é desfeita ao reiniciar o sistema.
* **Montagem Permanente**: Para que o disco seja montado automaticamente no boot, é necessário configurar o arquivo `/etc/fstab`.
