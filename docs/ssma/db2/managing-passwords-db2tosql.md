---
description: Управление паролями (DB2ToSQL)
title: Управление паролями (DB2ToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 07/05/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 56d546e3-8747-4169-aace-693302667e94
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 25a6063863355fe40f36ab00bf7473d5d3d690d2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88472483"
---
# <a name="managing-passwords-db2tosql"></a>Управление паролями (DB2ToSQL)
В этом разделе описывается защита паролей базы данных и процедура импорта или экспорта на серверах:  
  
1.  Защита пароля  
  
2.  Экспорт или импорт зашифрованного пароля  
  
## <a name="securing-password"></a>Защита пароля  
SSMA позволяет защитить пароль базы данных.  
  
Для реализации безопасного подключения используйте следующую процедуру.  
  
Укажите допустимый пароль, используя один из следующих трех методов:  
  
1.  **Открытый текст:** Введите пароль базы данных в атрибуте значение узла Password. Он находится в узле определение сервера в разделе сервер файла скрипта или файла соединения сервера.  
  
    Пароли в открытом тексте не являются безопасными. Поэтому в выходных данных консоли появится следующее предупреждение: *"пароль сервера Server &lt; -ID указан &gt; в небезопасном ТЕКСТОВОМ формате, SSMA консольное приложение предоставляет возможность защиты пароля с помощью шифрования. Дополнительные сведения см. в описании параметра-секурепассворд в файле справки SSMA."*  
  
    **Зашифрованные пароли:** В этом случае указанный пароль хранится в зашифрованном виде на локальном компьютере в Протектедстораже. SSMA.  
  
    -   **Защита паролей**  
  
        -   Выполните `SSMAforDB2Console.exe` команду с параметром `-securepassword` и добавьте в командной строке, передав соединение с сервером или файл скрипта, содержащий узел Password, в разделе Определение сервера.  
  
        -   В командной строке пользователю предлагается ввести пароль базы данных и подтвердить его.  
  
            Идентификаторы определения сервера и соответствующие зашифрованные пароли хранятся в файле на локальном компьютере.  
            
            Пример 1:
            
            ```console
            Specify password
            C:\SSMA\SSMAforDB2Console.EXE -securepassword -add all -s "D:\Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "D:\Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts\ VariableValueFileSample.xml"
            
            Enter password for server_id 'XXX_1': xxxxxxx
            
            Re-enter password for server_id 'XXX_1': xxxxxxx
            ```
            
            Пример 2.
            
            ```console
            C:\SSMA\SSMAforDB2Console.EXE -securepassword -add "source_1,target_1" -c "D:\Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts\ServersConnectionFileSample.xml" - v "D:\Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts\ VariableValueFileSample.xml" -o
            
            Enter password for server_id 'source_1': xxxxxxx
            
            Re-enter password for server_id 'source_1': xxxxxxx
            
            Enter password for server_id 'target_1': xxxxxxx
            
            Re-enter password for server_id 'target _1': xxxxxxx  
            ```
    
    -   **Удаление зашифрованных паролей**  
  
        Выполните `SSMAforDB2Console.exe` команду с параметром `-securepassword` и в `-remove` командной строке, передав идентификаторы серверов, чтобы удалить зашифрованные пароли из защищенного файла хранилища, присутствующего на локальном компьютере.  
  
        Пример  

        ```console
        C:\SSMA\SSMAforDB2Console.EXE -securepassword -remove all
        C:\SSMA\SSMAforDB2Console.EXE -securepassword -remove "source_1,target_1"
        ```

    -   **Вывод списка идентификаторов серверов, пароли которых шифруются**  
  
        Выполните `SSMAforDB2Console.exe` команду с параметром `-securepassword` и в `-list` командной строке, чтобы вывести список всех идентификаторов серверов, пароли которых были зашифрованы.  
  
        Пример  

        ```console
        C:\SSMA\SSMAforDB2Console.EXE -securepassword -list
        ```

    > [!NOTE]  
    > 1.  Пароль в открытом тексте, упомянутом в сценарии или файле соединения с сервером, имеет приоритет над зашифрованным паролем в защищенном файле.  
    > 2.  Если в разделе Server файла подключения сервера или файла скрипта нет пароля, или если он не защищен на локальном компьютере, то консоль предложит ввести пароль.  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>Экспорт или Импорт зашифрованных паролей  
Консольное приложение SSMA позволяет экспортировать зашифрованные пароли баз данных, находящиеся в файле на локальном компьютере, в защищенный файл и наоборот. Это помогает сделать зашифрованные пароли независимыми от компьютера.

_Функция экспорта_ считывает идентификатор и пароль сервера из локального защищенного хранилища. Затем система сохраняет идентификатор и пароль в зашифрованном файле. Пользователю предлагается ввести пароль для защищенного файла. Убедитесь, что длина пароля не превышает 8 символов. Этот защищенный файл переносим на разные компьютеры.

_Функция импорта_ считывает идентификатор сервера и сведения о пароле из защищенного файла. Пользователю предлагается ввести пароль защищенного файла и добавить сведения в локально защищенное хранилище.  

### <a name="export-example"></a>Пример экспорта

1. Экспортируйте пароль.

2. Введите пароль для защиты экспортированного файла.

3. Выполните команду: &nbsp;`C:\SSMA\SSMAforDB2Console.EXE -securepassword -export all "machine1passwords.file"`

4. Введите пароль для защиты экспортированного файла: XXXXXXXX

5. Подтверждение пароля: XXXXXXXX

6. Выполните команду: &nbsp;`C:\SSMA\SSMAforDB2Console.EXE -p -e "DB2DB_1_1,Sql_1" "machine2passwords.file"`

7. Введите пароль для защиты экспортированного файла: XXXXXXXX

8. Подтверждение пароля: XXXXXXXX  

### <a name="import-example"></a>Пример импорта

1. Импортируйте зашифрованный пароль.

2. Введите пароль для защиты импортированного файла.

3. Выполните команду: &nbsp;`C:\SSMA\SSMAforDB2Console.EXE -securepassword -import all "machine1passwords.file"`

4. Введите пароль для импорта серверов из зашифрованного файла: XXXXXXXX

5. Подтверждение пароля: XXXXXXXX

6. Выполните команду: &nbsp;`C:\SSMA\SSMAforDB2Console.EXE -p -i "DB2DB_1,Sql_1" "machine2passwords.file"`

7. Введите пароль для импорта серверов из зашифрованного файла: XXXXXXXX

8. Подтверждение пароля: XXXXXXXX

## <a name="see-also"></a>См. также  
[Выполнение команд консоли SSMA](https://msdn.microsoft.com/ce63f633-067d-4f04-b8e9-e1abd7ec740b)  
  
