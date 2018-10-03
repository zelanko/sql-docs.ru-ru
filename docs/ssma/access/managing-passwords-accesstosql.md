---
title: Управление паролями (AccessToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: b099d0f9-dd37-4c87-8b6f-ed0177881ea4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 167496250631866c009caef0dfe2044db4d11d6d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47644592"
---
# <a name="managing-passwords-accesstosql"></a>Управление паролями (AccessToSQL)
Этот раздел посвящен защита пароли к базам данных и процедуру для импорта или экспорта их на серверах:  
  
1.  Защита пароля  
  
2.  Экспорт или импорт зашифрованный пароль  
  
## <a name="securing-password"></a>Защита пароля  
SSMA позволяет защищать пароль базы данных.  
  
Используйте следующую процедуру для установления безопасного соединения:  
  
Укажите допустимый пароль с помощью одного из следующих трех методов:  
  
1.  **Открытого текста:** введите пароль базы данных в атрибуте значение узла «пароль». Его можно найти в разделе Определение узел сервера в разделе сервера из файла сценария или файла соединения сервера.  
  
    Пароли в виде открытого текста не являются безопасными. Таким образом, возникнет следующее предупреждающее сообщение в выходных данных консоли: *«Server &lt;идентификатор сервера&gt; пароль предоставляется в виде открытого текста, небезопасный, SSMA консольное приложение предоставляет возможность защиты пароль с помощью шифрования, см. параметр – securepassword в SSMA файл справки для Дополнительные сведения.»*  
  
    **Зашифрованные пароли:** указанный пароль, таким образом, хранится в зашифрованном виде на локальном компьютере в ProtectedStorage.ssma.  
  
    -   **Защита паролей**  
  
        -   Выполнение `SSMAforAccessConsole.exe` с `–securepassword` и добавьте параметр командной строки, передав сервера соединение или скрипт файл, содержащий узел пароля в разделе "Определение" server.  
  
        -   В командной строке пользователю предлагается ввести пароль и подтвердите его.  
  
            Определения идентификаторов серверов и его соответствующие зашифрованные пароли хранятся в файле на локальном компьютере  
  
            Пример 1.
            
                Specify password
                
                C:\SSMA\SSMAforAccessConsole.EXE –securepassword –add all –s "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\AssessmentReportGenerationSample.xml" –v "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ VariableValueFileSample.xml"
                
                Enter password for server_id 'XXX_1': xxxxxxx
                
                Re-enter password for server_id 'XXX_1': xxxxxxx  
            
            Пример 2.
            
                C:\SSMA\SSMAforAccessConsole.EXE –securepassword –add "source_1,target_1" –c "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ServersConnectionFileSample.xml" – v "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ VariableValueFileSample.xml" -o
                
                Enter password for server_id 'source_1': xxxxxxx
                
                Re-enter password for server_id 'source_1': xxxxxxx
                
                Enter password for server_id 'target_1': xxxxxxx
                
                Re-enter password for server_id 'target _1': xxxxxxx  
  
    -   **Удаление зашифрованных паролей**  
  
        Выполнение `SSMAforAccessConsole.exe` с`–securepassword` и `–remove` переключиться в командной строке, передав идентификаторов серверов, чтобы удалить зашифрованные пароли из защищенного хранилища файле присутствует на локальном компьютере.  
  
            C:\SSMA\SSMAforAccessConsole.EXE –securepassword –remove all
            C:\SSMA\SSMAforAccessConsole.EXE –securepassword –remove "source_1,target_1"  
  
    -   **Список идентификаторов серверов, чьи пароли шифруются**  
  
        Выполнение SSMAforAccessConsole.exe с `–securepassword` и `–list` переключиться в командной строке, чтобы получить список идентификаторов серверов, чьи пароли были зашифрованы.  
  
            C:\SSMA\SSMAforAccessConsole.EXE –securepassword –list  
  
    > [!NOTE]  
    > 1.  Пароль в виде открытого текста, упомянутые в файле подключения скрипт или сервера имеет приоритет над зашифрованный пароль в защищенный файл.  
    > 2.  Если пароль не существует в разделе сервера файле подключения сервера или файла скрипта или при отсутствии защиты на локальном компьютере, консоли появится запрос на ввод пароля.  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>Экспорт или импорт зашифрованных паролей  
SSMA консольного приложения позволяет экспортировать пароли зашифрованной базы данных представлен в файле на локальном компьютере для защищенного файла и наоборот. Он помогает в создании независимых машины зашифрованные пароли. Функция экспорта считывает идентификатор сервера и пароль из локального защищенное хранилище и сохраняет данные в зашифрованном файле. Пользователю предлагается ввести пароль для защищенного файла. Убедитесь, что введенный пароль имеет значение не менее 8 символов. Этот защищенный файл можно переносить на разных компьютерах. Функции импорта считывает значения сервера идентификатор и пароль из защищенного файла. Пользователю предлагается ввести пароль для защищенного файла и добавляет данные в локальном защищенном хранилище.  


    Export password
    
    Enter password for protecting the exported file
    
    C:\SSMA\SSMAforAccessConsole.EXE –securepassword –export all "machine1passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforAccessConsole.EXE –p –e "AccessDB_1_1,Sql_1" "machine2passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  


    Import an encrypted password
    
    Enter password for protecting the imported file
    
    C:\SSMA\SSMAforAccessConsole.EXE –securepassword –import all "machine1passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforAccessConsole.EXE –p –i "AccessDB_1,Sql_1" "machine2passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
## <a name="see-also"></a>См. также  
[Выполнение команд консоли SSMA (доступ)](http://msdn.microsoft.com/en-us/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  
