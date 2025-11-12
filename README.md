# automatizacao
#Projeto de automatização de tarefas, criado em Python.

import pyautogui
import time

#pyautogui.click -> clicar em algum lugar
#pyautogui.press -> apertar 1 tecla
#pyautogui.write -> escrever um texto
#pyautogui.hotkey -> apertar uma combinação de tecals.

pyautogui.PAUSE = 4

#Passo 1: Acessar o site da empresa : https://dlp.hashtagtreinamentos.com/python/intensivao/login
# Abrir o navegaor
pyautogui.press("win") #Você poderá escolher a tecla que quiser apertar.
pyautogui.write("chrome") #Você poderá escolher qualquer programa.
pyautogui.press("enter")

# Digitar o site
site = "https://dlp.hashtagtreinamentos.com/python/intensivao/login"
pyautogui.write(site)
pyautogui.press("enter")

#Esperar 5 segundos (é possivel fazer a alteração do tempo de espera)
time.sleep(4)


#Passo 2: Fazer login
#preencher email
pyautogui.click(x=617, y=422) 
pyautogui.write("teste@gmail.com")
pyautogui.press('tab')
time.sleep(3)
#preencher a senha
pyautogui.write("senhafacil1234")
pyautogui.press("tab")
#Se logar
pyautogui.press("enter")

#espera de 5 seg
time.sleep(5)

#Passo 3: Importar base dados
import pandas

tabela = pandas.read_csv("produtos.csv")   

print(tabela)
#Passo 4: Cadastrar os produtos
for linha in tabela.index:
    pyautogui.click(x=587, y=301)

    pyautogui.write(str(tabela.loc[linha, "codigo"]))
    pyautogui.press("tab")

    pyautogui.write(str(tabela.loc[linha, "marca"]))
    pyautogui.press("tab")

    pyautogui.write(str(tabela.loc[linha, "tipo"]))
    pyautogui.press("tab")

    pyautogui.write(str(tabela.loc[linha, "categoria"]))
    pyautogui.press("tab")

    pyautogui.write(str(tabela.loc[linha, "preco_unitario"]))
    pyautogui.press("tab")

    pyautogui.write(str(tabela.loc[linha, "custo"]))
    pyautogui.press("tab")

    if pandas.notna(tabela.loc[linha, "obs"]):
        pyautogui.write(str(tabela.loc[linha, "obs"]))

    pyautogui.press("tab")
    pyautogui.press("enter")
    pyautogui.scroll(10000)

#Passo 5: Repetir para todos os produtos
#pyautogui -> fazer automações com python