# PROJETO REFLORESTAMENTO
![projetoreflorestamento](./projeto%20reflorestamento.jpg)

Este projeto é uma aplicação de interface gráfica desenvolvida com tkinter que simula o processo de reflorestamento no Nordeste do Brasil. O usuário pode selecionar uma sub-região e uma espécie para ser plantada, visualizando o tempo de reflorestamento necessário para aquela árvore naquela sub-região.
## Índice
- <a href= "#-Funcionalidades"> Funcionalidades do projeto </a>
- <a href= "#-Tecnologias"> Tecnologias utilizadas </a>
- <a href= "#-Executar"> Como executar o programa? </a>
## Funcionalidades do Projeto
- **Visualizar Tempo de Reflorestamento**: Mostra o tempo necessário para a recuperação de uma espécie selecionada em uma sub-região específica.
## Tecnologias Utilizadas
- `tkinter` (normalmente já incluído com Python)
## Como Executar o Programa:

```bash
#Importando biblioteca tkinter e configurando a janela principal
import tkinter as tk
from tkinter import messagebox

root = tk.Tk()
root.title('PROJETO REFLORESTAMENTO')
root.geometry('800x500')
root.configure(background='white')

#Dicionário do tempo de reflorestamento de cada subregião do nordeste, contendo chave (especie) e valor (tempo do reflorestamento).
tempo_reflorestamento_MN = {'Babaçu':'10 Anos', 'Buriti' : '10 Anos', 'Carnaúba': '8 Anos', 'Pequi':'15 Anos', 'Cajuí':'7 Anos', 'Anajá':'10 Anos'}
tempo_reflorestamento_sertao = {'Umbuzeiro':'7 Anos', 'Juazeiro':'10 Anos', 'Mandacaru':'5 Anos', 'Xique-Xique':'8 Anos', 'Aroeira do sertão':'15 Anos', 'Catingueira':'6 Anos', 'Jurema Preta':'7 Anos', 'Quixabeira':'10 Anos'}
tempo_reflorestamento_agreste = {'Umbuzeiro':'8 Anos', 'Cajueiro':'7 Anos', 'Juazeiro':'10 Anos', 'Pereiro':'10 Anos', 'Sabiá':'5 Anos', 'Ipê-Roxo':'12 Anos', 'Mulungu':'5 Anos', 'Angico':'8 Anos', 'Catingueira':'6 Anos'}
tempo_reflorestamento_ZDM = {'Pau-Brasil':'15 Anos', 'Jatobá':'15 Anos', 'Suxupira':'12 Anos', 'Gameleira':'8 Anos', 'Ingá': '5 Anos', 'Ipê-Amarelo':'10 Anos'}

#Função onde mostrará o tempo de reflorestamento, onde especie_tempo recebe o dicionario das regiões dos tempos de reflorestamento e especie_regiao é a lista desses dicionários
def tempo_reflorestamento(especie_tempo, especie_regiao):
    selecionar = especie_regiao.curselection()
    if selecionar:
        especie = especie_regiao.get(selecionar [0] ) # adicionou o 0
        tempo = especie_tempo.get(especie, "Tempo desconhecido")
        messagebox.showinfo("Tempo de Reflorestamento", f"A espécie  {especie}, leva {tempo} anos para se recuperar na sub-região escolhida.")
    else:
        messagebox.showwarning("Atenção", "É necessário selecionar uma espécie.")

#Função para criar a janela para o usuario selecionar na lista a especie que deseja
def janela_geral(especie_tempo, especie):

    janela = tk.Toplevel()
    janela.title('PROJETO REFLORESTAMENTO')
    janela.geometry('600x400')
    janela.configure(background='seagreen')

    tk.Label(janela, text='Informe a espécie que será plantada', font=('Arial', 12)).grid(row=0, column=0)

    lb = tk.Listbox(janela, height=len(especie))
    lb.grid(row=1, column=0)

    for i, especie in enumerate(especie): 
        lb.insert(i, especie)

    tk.Button(janela, text='Ver Tempo de Reflorestamento', command=lambda: tempo_reflorestamento(especie_tempo, lb )).grid(row=2, column=0) 
    tk.Button(janela, text='Fechar', command=janela.destroy).grid(row=3, column=0)

#Função de cada subregião, onde cada uma tem suas espécies e os tempos de reflorestamento
def reg_meio_norte():
    especie = list(tempo_reflorestamento_MN.keys())
    janela_geral(tempo_reflorestamento_MN, especie)

def reg_sertao():
    especie = list(tempo_reflorestamento_sertao.keys())
    janela_geral(tempo_reflorestamento_sertao, especie)

def reg_agreste():
    especie = list(tempo_reflorestamento_agreste.keys())
    janela_geral(tempo_reflorestamento_agreste, especie)

def reg_zona_da_mata():
    especie = list(tempo_reflorestamento_ZDM.keys())
    janela_geral(tempo_reflorestamento_ZDM, especie)

#Texto e botões da janela principal
tk.Label(root, text='Sub-região do Nordeste', font=('Arial', 12), background='seagreen').grid(row=0, column=0)

meio_norte = tk.Button(root, text='Meio-Norte', font=('Arial', 11), command=reg_meio_norte).grid(row=1, column=0)
sertao = tk.Button(root, text='Sertão', font=('Arial', 11), command=reg_sertao).grid(row=2, column=0)
agreste = tk.Button(root, text='Agreste', font=('Arial', 11), command=reg_agreste).grid(row=3, column=0)
zona_da_mata =tk.Button(root, text='Zona da Mata', font=('Arial', 11), command=reg_zona_da_mata).grid(row=4, column=0)






root.mainloop()
```
