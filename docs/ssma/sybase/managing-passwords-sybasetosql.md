---
title: Управление паролями (SybaseToSQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Sybase Console,Exporting or Importing Encrypted Passwords
- Sybase Console,Managing Passwords
- Sybase Console,Securing Password
ms.assetid: 9b6a70f9-6840-4140-a059-bb7bd7ccc67c
caps.latest.revision: 12
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 39b3d63391d8df1ca38858fa8d2a749dd79c5b12
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="managing-passwords-sybasetosql"></a>Управление паролями (SybaseToSQL)
Этот раздел посвящен безопасности пароли к базам данных и процедуру для импорта и экспорта их между серверами:  
  
1.  Защита паролем  
  
2.  Экспорт или импорт зашифрованный пароль  
  
## <a name="securing-password"></a>Защита паролем  
SSMA позволяет защищать пароль базы данных.  
  
Используйте следующую процедуру для реализации безопасного соединения:  
  
Укажите допустимый пароль, с помощью одного из следующих трех способов:  
  
1.  **Открытым текстом:** в атрибут "value" узла «пароль» введите пароль базы данных. Он находится на узле сервера определения в разделе "сервер" из файла сценария или файла соединения сервера.  
  
    Пароли в виде открытого текста не являются безопасными. Таким образом, будет возникать следующее предупреждающее сообщение в окно консоли: *«Server &lt;идентификатор сервера&gt; пароль предоставляется в виде открытого текста, не является безопасной, приложение консоли SSMA обеспечивает возможность защиты пароль с помощью шифрования, см. в разделе параметр – securepassword в SSMA файл справки для получения дополнительной информации.»*  
  
    **Зашифрованные пароли:** указанный пароль в этом случае сохраняется в зашифрованном виде на локальном компьютере в ProtectedStorage.ssma.  
  
    -   **Защита паролей**  
  
        -   Выполнение `SSMAforSybaseConsole.exe` с `–securepassword` и добавьте параметр командной строки, передав сервере соединение или скрипт файл, содержащий узел пароля в разделе Определение сервера.  
  
        -   В строке пользователю предлагается ввести пароль базы данных и подтвердите его.  
  
            Идентификаторы определение сервера и его соответствующие зашифрованные пароли хранятся в файле на локальном компьютере  
            
            Пример 1.  
            
                Specify password
                
                C:\SSMA\SSMAforSybaseConsole.EXE –securepassword –add all –s "D:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\AssessmentReportGenerationSample.xml" –v "D:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ VariableValueFileSample.xml"
                
                Enter password for server_id 'XXX_1': xxxxxxx
                
                Re-enter password for server_id 'XXX_1': xxxxxxx
            
            Пример 2.
            
                C:\SSMA\SSMAforSybaseConsole.EXE –securepassword –add "source_1,target_1" –c "D:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ServersConnectionFileSample.xml" – v "D:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ VariableValueFileSample.xml" -o
                
                Enter password for server_id 'source_1': xxxxxxx
                
                Re-enter password for server_id 'source_1': xxxxxxx
                
                Enter password for server_id 'target_1': xxxxxxx
                
                Re-enter password for server_id 'target _1': xxxxxxx  
    
    -   **Удаление зашифрованных паролей**  
  
        Выполнение `SSMAforSybaseConsole.exe` с`–securepassword` и `–remove` переключения командной строки, передав идентификаторы сервера, необходимо удалить зашифрованные пароли из файла защищенное хранилище существует на локальном компьютере.  
  
        Пример  
        
            C:\SSMA\SSMAforSybaseConsole.EXE –securepassword –remove all
            C:\SSMA\SSMAforSybaseConsole.EXE –securepassword –remove "source_1,target_1"  
  
    -   **Перечисление идентификаторы серверов, чьи пароли шифруются**  
  
        Выполнение `SSMAforSybaseConsole.exe` с `–securepassword` и `–list` переключения командной строки, чтобы перечислить все идентификаторы сервера, чьи пароли были зашифрованы.  
  
        Пример  
        
            C:\SSMA\SSMAforSybaseConsole.EXE –securepassword –list  
  
    > [!NOTE]  
    > 1.  Пароль в виде открытого текста, упомянутые в скрипте или серверном файле подключения имеет приоритет над зашифрованный пароль в защищенного файла.  
    > 2.  Если пароль не существует в области сервера файл подключения сервера или файла скрипта или не защищен на локальном компьютере, консоль предложит ввести пароль.  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>Экспорт или импорт зашифрованные пароли  
SSMA консольного приложения позволяет экспортировать пароли зашифрованной базы данных содержатся в файле на локальном компьютере для защищенного файла и наоборот. Это помогает сделать независимых машины зашифрованные пароли. Функции экспорта считывает идентификатор сервера и пароль из локального защищенное хранилище и сохраняет информацию в зашифрованный файл. Пользователю предлагается ввести пароль для защищенного файла. Убедитесь, что введенный пароль имеет значение не менее 8 символов. Это защищенного файла можно переносить на разных компьютерах. Возможность импорта считывает значения сервера идентификатор и пароль из защищенного файла. Пользователю предлагается ввести пароль для защищенного файла и добавляет данные в локальном защищенном хранилище.  
  
Пример  

    Export password
    
    Enter password for protecting the exported file
    
    C:\SSMA\SSMAforSybaseConsole.EXE –securepassword –export all "machine1passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforSybaseConsole.EXE –p –e "SybaseDB_1_1,Sql_1" "machine2passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
Пример  

    Import an encrypted password
    
    Enter password for protecting the imported file
    
    C:\SSMA\SSMAforSybaseConsole.EXE –securepassword –import all "machine1passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforSybaseConsole.EXE –p –i "SybaseDB_1,Sql_1" "machine2passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
## <a name="see-also"></a>См. также  
[Выполнение консоли SSMA (Sybase)](http://msdn.microsoft.com/en-us/ea8950b7-fabc-4aa4-89f8-9573a2617d70)  
  
