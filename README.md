# azurefloripa
Apresentação 23/06/2021


# Para sincronizar o Active Directory local é necessário instalar o Azure Ad Connect 
https://docs.microsoft.com/pt-br/azure/active-directory/hybrid/how-to-connect-install-express


#Instalar os módulos da Galeria do PowerShell no servidor do AD que está fazendo o sync com o tenant
Install-Module -Name AzureRM -AllowClobber


## Download do FILES HYBRID dentro do AD
https://github.com/Azure-Samples/azure-files-samples/releases


##Como adicionar o storage account no domínio
https://docs.microsoft.com/pt-br/azure/storage/files/storage-files-identity-ad-ds-enable


## Listar a chave de autenticação do Storage Account
Get-AzStorageAccountKey -ResourceGroupName "RG-FLORIPA" -AccountName "stofloripa"


## Mapear as unidades de rede
net use G: \\stofloripa.file.core.windows.net\compartilhamento /user:Azure\stofloripa *chave*

## Fazer a cópia dos arquivos do file server
robocopy \\SRV-FILESERVER\C$\Todos G:\Todos /E /TEE /ETA /SEC /MT:32 /MIR /R:0 /W:0 /COPYALL /B /XD 


## Fazer a cópia dos arquivos do file server gerando logs
robocopy \\SRV-FILESERVER\C$\Todos G:\Todos /E /TEE /ETA /SEC /MT:32 /MIR /R:0 /W:0 /COPYALL /B /XD /LOG:c:\temp\log.txt


