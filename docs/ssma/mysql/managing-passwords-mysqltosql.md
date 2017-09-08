---
title: "Управление паролями (MySQLToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Password management, importing or exporting encrypted password
- Password management, securing password
ms.assetid: 4ffbc587-ea3f-49ad-bc42-a654f672325e
caps.latest.revision: 13
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0dbff0566c8fb72d482503d28e09747f0c3a76a0
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="managing-passwords-mysqltosql"></a>Управление паролями (MySQLToSQL)
Этот раздел посвящен безопасности пароли к базам данных и процедуру для импорта и экспорта их между серверами:  
  
1.  Защита паролем  
  
2.  Экспорт или импорт зашифрованный пароль  
  
## <a name="securing-password"></a>Защита паролем  
SSMA позволяет защищать пароль базы данных.  
  
Используйте следующую процедуру для реализации безопасного соединения:  
  
Укажите допустимый пароль, с помощью одного из следующих трех способов:  
  
1.  **Открытым текстом:** в атрибут "value" узла «пароль» введите пароль базы данных. Он находится на узле сервера определения в разделе "сервер" из файла сценария или файла соединения сервера.  
  
    Пароли в виде открытого текста не являются безопасными. Таким образом, будет возникать следующее предупреждающее сообщение в окно консоли: *«Server &lt;идентификатор сервера&gt; пароль предоставляется в виде открытого текста, не является безопасной, SSMA консольное приложение предоставляет возможность защитить пароль с помощью шифрования, см. в разделе securepassword — параметр в файле справки SSMA для получения дополнительной информации.»*  
  
    **Зашифрованные пароли:** указанный пароль в этом случае сохраняется в зашифрованном виде на локальном компьютере в ProtectedStorage.ssma.  
  
    -   **Защита паролей**  
  
        -   Выполнение `SSMAforMySQLConsole.exe` с `–securepassword` и добавьте параметр командной строки, передав сервере соединение или скрипт файл, содержащий узел пароля в разделе Определение сервера.  
  
        -   В строке пользователю предлагается ввести пароль базы данных и подтвердите его.  
  
            Идентификаторы определение сервера и его соответствующие зашифрованные пароли хранятся в файле на локальном компьютере  
            
            Пример 1.
            
                Specify password
                
                C:\SSMA\SSMAforMySQLConsole.EXE –securepassword –add all –s "D:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\AssessmentReportGenerationSample.xml" –v "D:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ VariableValueFileSample.xml"
                
                Enter password for server_id 'XXX_1': xxxxxxx
                
                Re-enter password for server_id 'XXX_1': xxxxxxx
            
            Пример 2.
            
                C:\SSMA\SSMAforMySQLConsole.EXE –securepassword –add "source_1,target_1" –c "D:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ServersConnectionFileSample.xml" – v "D:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ VariableValueFileSample.xml" -o
                
                Enter password for server_id 'source_1': xxxxxxx
                
                Re-enter password for server_id 'source_1': xxxxxxx
                
                Enter password for server_id 'target_1': xxxxxxx
                
                Re-enter password for server_id 'target _1': xxxxxxx
            
    -   **Удаление зашифрованных паролей**  
  
        Выполнение `SSMAforMySQLConsole.exe` с`–securepassword` и `–remove` переключения командной строки, передав идентификаторы сервера, необходимо удалить зашифрованные пароли из файла защищенное хранилище существует на локальном компьютере.  
  
        Пример  

            C:\SSMA\SSMAforMySQLConsole.EXE –securepassword –remove all
            C:\SSMA\SSMAforMySQLConsole.EXE –securepassword –remove "source_1,target_1"  
  
    -   **Перечисление идентификаторы серверов, чьи пароли шифруются**  
  
        Выполнение `SSMAforMySQLConsole.exe` с `–securepassword` и `–list` переключения командной строки, чтобы перечислить все идентификаторы сервера, чьи пароли были зашифрованы.  
  
        Пример  
        
            C:\SSMA\SSMAforMySQLConsole.EXE –securepassword –list  
  
    > [!NOTE]  
    > 1.  Пароль в виде открытого текста, упомянутые в скрипте или серверном файле подключения имеет приоритет над зашифрованный пароль в защищенного файла.  
    > 2.  Если пароль не существует в области сервера файл подключения сервера или файла скрипта или не защищен на локальном компьютере, консоль предложит ввести пароль.  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>Экспорт или импорт зашифрованные пароли  
SSMA консольного приложения позволяет экспортировать пароли зашифрованной базы данных содержатся в файле на локальном компьютере для защищенного файла и наоборот. Это помогает сделать независимых машины зашифрованные пароли. Функции экспорта считывает идентификатор сервера и пароль из локального защищенное хранилище и сохраняет информацию в зашифрованный файл. Пользователю предлагается ввести пароль для защищенного файла. Убедитесь, что введенный пароль имеет значение не менее 8 символов. Это защищенного файла можно переносить на разных компьютерах. Возможность импорта считывает значения сервера идентификатор и пароль из защищенного файла. Пользователю предлагается ввести пароль для защищенного файла и добавляет данные в локальном защищенном хранилище.  
  
Пример  

    Export password
    
    Enter password for protecting the exported file
    
    C:\SSMA\SSMAforMySQLConsole.EXE –securepassword –export all "machine1passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforMySQLConsole.EXE –p –e "MySQLDB_1_1,Sql_1" "machine2passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
Пример  

    Import an encrypted password
    
    Enter password for protecting the imported file
    
    C:\SSMA\SSMAforMySQLConsole.EXE –securepassword –import all "machine1passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforMySQLConsole.EXE –p –i "MySQLDB_1,Sql_1" "machine2passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
## <a name="see-also"></a>См. также:  
[Выполнение консоли SSMA (MySQL)](http://msdn.microsoft.com/en-us/e3e9f7e4-0619-4861-a202-3d5d39953b26)  
  

