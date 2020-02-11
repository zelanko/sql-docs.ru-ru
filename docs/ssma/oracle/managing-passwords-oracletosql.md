---
title: Управление паролями (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Managing Passwords in Oracle, Exporting or Importing Encrypted Password
- Managing passwords in Oracle, Securing Password
ms.assetid: 8c7d9f8e-06bb-476c-bbd2-15b61d5bba3c
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: d8520224662c02d1ffbe9fd2fd6ef76f8b1e698a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68262920"
---
# <a name="managing-passwords-oracletosql"></a>Управление паролями (OracleToSQL)
В этом разделе описывается защита паролей базы данных и процедура импорта или экспорта на серверах:  
  
1.  Защита пароля  
  
2.  Экспорт или импорт зашифрованного пароля  
  
## <a name="securing-password"></a>Защита пароля  
SSMA позволяет защитить пароль базы данных.  
  
Для реализации безопасного подключения используйте следующую процедуру.  
  
Укажите допустимый пароль, используя один из следующих трех методов:  
  
1.  **Открытый текст:** Введите пароль базы данных в атрибуте значение узла Password. Он находится в узле определение сервера в разделе сервер файла скрипта или файла соединения сервера.  
  
    Пароли в открытом тексте не являются безопасными. Поэтому в выходных данных консоли появится следующее предупреждение: *" &lt;пароль сервера Server-ID&gt; указан в небезопасном текстовом формате, SSMA консольное приложение предоставляет возможность защиты пароля с помощью шифрования. Дополнительные сведения см. в описании параметра-секурепассворд в файле справки SSMA."*  
  
    **Зашифрованные пароли:** В этом случае указанный пароль хранится в зашифрованном виде на локальном компьютере в Протектедстораже. SSMA.  
  
    -   **Защита паролей**  
  
        -   Выполните команду `SSMAforOracleConsole.exe` с параметром `-securepassword` и добавьте в командной строке, передав соединение с сервером или файл скрипта, содержащий узел Password, в разделе Определение сервера.  
  
        -   В командной строке пользователю предлагается ввести пароль базы данных и подтвердить его.  
  
            Идентификаторы определения сервера и соответствующие зашифрованные пароли хранятся в файле на локальном компьютере.  
            
            Пример 1:  
            
                Specify password
                
                C:\SSMA\SSMAforOracleConsole.EXE -securepassword -add all -s "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\ VariableValueFileSample.xml"
                
                Enter password for server_id 'XXX_1': xxxxxxx
                
                Re-enter password for server_id 'XXX_1': xxxxxxx
            
            Пример 2.
            
                C:\SSMA\SSMAforOracleConsole.EXE -securepassword -add "source_1,target_1" -c "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\ServersConnectionFileSample.xml" - v "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\ VariableValueFileSample.xml" -o
                
                Enter password for server_id 'source_1': xxxxxxx
                
                Re-enter password for server_id 'source_1': xxxxxxx
                
                Enter password for server_id 'target_1': xxxxxxx
                
                Re-enter password for server_id 'target _1': xxxxxxx  
    
    -   **Удаление зашифрованных паролей**  
  
        Выполните команду `SSMAforOracleConsole.exe` с`-securepassword` параметром `-remove` и в командной строке, передав идентификаторы серверов, чтобы удалить зашифрованные пароли из защищенного файла хранилища, присутствующего на локальном компьютере.  
        
        Пример  
        
            C:\SSMA\SSMAforOracleConsole.EXE -securepassword -remove all
            C:\SSMA\SSMAforOracleConsole.EXE -securepassword -remove "source_1,target_1"  
  
    -   **Вывод списка идентификаторов серверов, пароли которых шифруются**  
  
        Выполните команду `SSMAforOracleConsole.exe` с `-securepassword` параметром `-list` и в командной строке, чтобы вывести список всех идентификаторов серверов, пароли которых были зашифрованы.  
  
        Пример  
        
            C:\SSMA\SSMAforOracleConsole.EXE -securepassword -list  
  
    > [!NOTE]  
    > 1.  Пароль в открытом тексте, упомянутом в сценарии или файле соединения с сервером, имеет приоритет над зашифрованным паролем в защищенном файле.  
    > 2.  Если в разделе Server файла подключения сервера или файла скрипта нет пароля, или если он не защищен на локальном компьютере, то консоль предложит ввести пароль.  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>Экспорт или Импорт зашифрованных паролей  
Консольное приложение SSMA позволяет экспортировать зашифрованные пароли баз данных, находящиеся в файле на локальном компьютере, в защищенный файл и наоборот. Это помогает сделать зашифрованные пароли независимыми от компьютера. Функция экспорта считывает идентификатор и пароль сервера из локального защищенного хранилища и сохраняет их в зашифрованном файле. Пользователю предлагается ввести пароль для защищенного файла. Убедитесь, что пароль имеет длину 8 символов или более. Этот защищенный файл переносим на разные компьютеры. Функция импорта считывает идентификатор сервера и сведения о пароле из защищенного файла. Пользователю предлагается ввести пароль для защищенного файла и добавить сведения в локально защищенное хранилище.  
  
Пример  

    Export password
    
    Enter password for protecting the exported file C:\SSMA\SSMAforOracleConsole.EXE -securepassword -export all "machine1passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforOracleConsole.EXE -p -e "OracleDB_1_1,Sql_1" "machine2passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
Пример  

    Import an encrypted password
    
    Enter password for protecting the imported file C:\SSMA\SSMAforOracleConsole.EXE -securepassword -import all "machine1passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforOracleConsole.EXE -p -i "OracleDB_1,Sql_1" "machine2passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
## <a name="see-also"></a>См. также:  
[Запуск консоли SSMA (Oracle)](https://msdn.microsoft.com/7228ccba-c69f-4b4c-8664-01a2750183c5)  
  
