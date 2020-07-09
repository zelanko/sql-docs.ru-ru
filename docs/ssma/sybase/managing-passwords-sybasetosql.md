---
title: Управление паролями (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 07/07/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Sybase Console,Exporting or Importing Encrypted Passwords
- Sybase Console,Managing Passwords
- Sybase Console,Securing Password
ms.assetid: 9b6a70f9-6840-4140-a059-bb7bd7ccc67c
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: a228f8d624d3a4250d10a258a7e51c9162d885a2
ms.sourcegitcommit: 21c14308b1531e19b95c811ed11b37b9cf696d19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "86159852"
---
# <a name="managing-passwords-sybasetosql"></a>Управление паролями (SybaseToSQL)
В этом разделе описывается защита паролей базы данных и процедура импорта или экспорта на серверах.

## <a name="securing-password"></a>Защита пароля  
SSMA позволяет защитить пароль базы данных.  
  
Для реализации безопасного подключения используйте следующую процедуру.  
  
Укажите допустимый пароль, используя один из следующих трех методов:  
  
1.  **Открытый текст:** Введите пароль базы данных в атрибуте значение узла Password. Он находится в узле определение сервера в разделе сервер файла скрипта или файла соединения сервера.  
  
    Пароли в открытом тексте не являются безопасными. Поэтому в выходных данных консоли появится следующее предупреждение: *"пароль сервера Server &lt; -ID указан &gt; в небезопасном ТЕКСТОВОМ формате, SSMA консольное приложение предоставляет возможность защиты пароля с помощью шифрования. Дополнительные сведения см. в описании параметра-секурепассворд в файле справки SSMA."*  
  
    **Зашифрованные пароли:** В этом случае указанный пароль хранится в зашифрованном виде на локальном компьютере в Протектедстораже. SSMA.  
  
    -   **Защита паролей**  
  
        -   Выполните `SSMAforSybaseConsole.exe` команду с параметром `-securepassword` и добавьте в командной строке, передав соединение с сервером или файл скрипта, содержащий узел Password, в разделе Определение сервера.  
  
        -   В командной строке пользователю предлагается ввести пароль базы данных и подтвердить его.  
  
            Идентификаторы определения сервера и соответствующие зашифрованные пароли хранятся в файле на локальном компьютере.  
            
            Пример 1:  
            
            1. Укажите пароль
                
            2. `C:\SSMA\SSMAforSybaseConsole.EXE -securepassword -add all -s "D:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "D:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ VariableValueFileSample.xml"`
                
            3. Введите пароль для server_id "XXX_1": xxxxxxx
                
            4. Повторно введите пароль для server_id "XXX_1": xxxxxxx
            
            Пример 2.
            
            1. `C:\SSMA\SSMAforSybaseConsole.EXE -securepassword -add "source_1,target_1" -c "D:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ServersConnectionFileSample.xml" - v "D:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ VariableValueFileSample.xml" -o`
                
            2. Введите пароль для server_id "source_1": xxxxxxx
                
            3. Повторно введите пароль для server_id "source_1": xxxxxxx
                
            4. Введите пароль для server_id "target_1": xxxxxxx
                
            5. Повторно введите пароль для server_id "Target _1": xxxxxxx  
    
    -   **Удаление зашифрованных паролей**  
  
        Выполните `SSMAforSybaseConsole.exe` команду с параметром `-securepassword` и в `-remove` командной строке, передав идентификаторы серверов, чтобы удалить зашифрованные пароли из защищенного файла хранилища, присутствующего на локальном компьютере.  
  
        Пример.  
        
        ```console
            C:\SSMA\SSMAforSybaseConsole.EXE -securepassword -remove all
            C:\SSMA\SSMAforSybaseConsole.EXE -securepassword -remove "source_1,target_1"  
        ```
  
    -   **Вывод списка идентификаторов серверов, пароли которых шифруются**  
  
        Выполните `SSMAforSybaseConsole.exe` команду с параметром `-securepassword` и в `-list` командной строке, чтобы вывести список всех идентификаторов серверов, пароли которых были зашифрованы.  
  
        Пример.  

        ```console
            C:\SSMA\SSMAforSybaseConsole.EXE -securepassword -list  
        ```
  
    > [!NOTE]  
    > 1.  Пароль в открытом тексте, упомянутом в сценарии или файле соединения с сервером, имеет приоритет над зашифрованным паролем в защищенном файле.  
    > 2.  Если в разделе Server файла подключения сервера или файла скрипта нет пароля, или если он не защищен на локальном компьютере, то консоль предложит ввести пароль.  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>Экспорт или Импорт зашифрованных паролей  
Консольное приложение SSMA позволяет экспортировать зашифрованные пароли баз данных, находящиеся в файле на локальном компьютере, в защищенный файл и наоборот. Это помогает сделать зашифрованные пароли независимыми от компьютера. Функция экспорта считывает идентификатор и пароль сервера из локального защищенного хранилища и сохраняет их в зашифрованном файле. Пользователю предлагается ввести пароль для защищенного файла. Убедитесь, что пароль имеет длину 8 символов или более. Этот защищенный файл переносим на разные компьютеры. Функция импорта считывает идентификатор сервера и сведения о пароле из защищенного файла. Пользователю предлагается ввести пароль для защищенного файла и добавить сведения в локально защищенное хранилище.  
  
### <a name="export-example"></a>Пример экспорта:  

1. Экспорт пароля
    
2. Введите пароль для защиты экспортированного файла
    
3. `C:\SSMA\SSMAforSybaseConsole.EXE -securepassword -export all "machine1passwords.file"`
    
4. Введите пароль для защиты экспортированного файла: XXXXXXXX
    
5. Подтвердите пароль: XXXXXXXX.
    
6. `C:\SSMA\SSMAforSybaseConsole.EXE -p -e "SybaseDB_1_1,Sql_1" "machine2passwords.file"`
    
7. Введите пароль для защиты экспортированного файла: XXXXXXXX
    
8. Подтвердите пароль: XXXXXXXX.  
  
### <a name="import-example"></a>Пример импорта:  

1. Импорт зашифрованного пароля
    
2. Введите пароль для защиты импортированного файла
    
3. `C:\SSMA\SSMAforSybaseConsole.EXE -securepassword -import all "machine1passwords.file"`
    
4. Введите пароль для импорта серверов из зашифрованного файла: XXXXXXXX
    
5. Подтвердите пароль: XXXXXXXX.
    
6. `C:\SSMA\SSMAforSybaseConsole.EXE -p -i "SybaseDB_1,Sql_1" "machine2passwords.file"`
    
7. Введите пароль для импорта серверов из зашифрованного файла: XXXXXXXX
    
8. Подтвердите пароль: XXXXXXXX.  
  
## <a name="see-also"></a>См. также:  
[Запуск консоли SSMA (Sybase)](https://msdn.microsoft.com/ea8950b7-fabc-4aa4-89f8-9573a2617d70)  
  
