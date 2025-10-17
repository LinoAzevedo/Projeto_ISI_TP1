# Como executar isto

## 1) Instalar o Knime

1. [Aqui](https://www.knime.com/downloads)

## 2) Instalar e executar o Node-RED

**macOS / Linux (npm):**
~~~bash
sudo npm install -g --unsafe-perm node-red
node-red
~~~

**Windows (npm):**
~~~cmd
npm install -g --unsafe-perm node-red
node-red
~~~

Depois abrir o editor em: [http://localhost:1880](http://localhost:1880)

---

## 3) Instalar o *add-on* de *dashboard* do Node-RED

No editor:  
**Menu → Manage Palette → Install** e procura por:
- `@flowfuse/node-red-dashboard`

A *Dashboard* fica em: [http://localhost:1880/ui](http://localhost:1880/ui)

---

## 4) Abrir os Projetos nos devidos programas

Node Red:

1. Copiar o JSON
2. na interface gráfica do Node-Red vai a Importar > Clipboard
3. Colar o JSON
4. Selecionar New Flow
5. Carregar em OK

Knime:

1. Abrir o ficheiro .Knwf com o Knime


## 5) Escolher o caminho dos logs (ficheiros) — KNIME

Em cada nó que deseja ler, definir o caminho do CSV.
Exemplo:
- **Windows:** `C:\Users\<user>\Projetos\ProjetoISI_1\Data\`
  
Em cada nó que escreve ficheiros (*CSV/JSON Writer*), definir o caminho onde quer guardar os respetivos ficheiros.  
Exemplo:
- **Windows:** `C:\Users\<user>\Projetos\ProjetoISI_1\Exports\`

## 6) Executar a workflow no botão do Knime

Este passo é autoexplicativo :] 

## 7) Vídeo de Demonstração

Um vídeo completo a demonstrar a execução do projeto está disponível no seguinte link:

[**Vídeo de Demonstração do Projeto**](https://alunosipca-my.sharepoint.com/:v:/g/personal/a23015_alunos_ipca_pt/EWFqwDptrOtLlUX-K-WdLAYBgy2yDIsUbMgniom1WhJIug)

---

## Autor

* **Lino Azevedo** - [Lino Azevedo](https://github.com/LinoAzevedo)
