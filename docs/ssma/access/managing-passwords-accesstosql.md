---
title: Управление паролями (Акцесстоскл) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 07/01/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: b099d0f9-dd37-4c87-8b6f-ed0177881ea4
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 0023e6d04b2f339fbd67337b7b241da2df275a79
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87938048"
---
# <a name="managing-passwords-accesstosql"></a>Управление паролями (Акцесстоскл)
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
  
        -   Выполните `SSMAforAccessConsole.exe` команду с параметром `-securepassword` и добавьте в командной строке, передав соединение с сервером или файл скрипта, содержащий узел Password, в разделе Определение сервера.  
  
        -   В командной строке пользователю предлагается ввести пароль базы данных и подтвердить его.  
  
            Идентификаторы определения сервера и соответствующие зашифрованные пароли хранятся в файле на локальном компьютере.  

            &nbsp;

            _Пример 1_.
            
            Укажите пароль

            ```console
            C:\SSMA\SSMAforAccessConsole.EXE -securepassword -add all -s "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ VariableValueFileSample.xml"
            ```

            Введите пароль для server_id "XXX_1": xxxxxxx
                
            Повторно введите пароль для server_id "XXX_1": xxxxxxx  

            &nbsp;

            _Пример 2._

            ```console
            C:\SSMA\SSMAforAccessConsole.EXE -securepassword -add "source_1,target_1" -c "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ServersConnectionFileSample.xml" - v "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ VariableValueFileSample.xml" -o
            ```

            Введите пароль для server_id "source_1": xxxxxxx
                
            Повторно введите пароль для server_id "source_1": xxxxxxx
                
            Введите пароль для server_id "target_1": xxxxxxx
                
            Повторно введите пароль для server_id "Target _1": xxxxxxx  
  
    -   **Удаление зашифрованных паролей**  
  
        Выполните `SSMAforAccessConsole.exe` команду с параметром `-securepassword` и в `-remove` командной строке, передав идентификаторы серверов, чтобы удалить зашифрованные пароли из защищенного файла хранилища, присутствующего на локальном компьютере.  

        ```console
        C:\SSMA\SSMAforAccessConsole.EXE -securepassword -remove all
        C:\SSMA\SSMAforAccessConsole.EXE -securepassword -remove "source_1,target_1"
        ```
  
    -   **Вывод списка идентификаторов серверов, пароли которых шифруются**  
  
        Выполните SSMAforAccessConsole.exe с `-securepassword` `-list` параметром и в командной строке, чтобы вывести список всех идентификаторов серверов, пароли которых были зашифрованы.  

        ```console
        C:\SSMA\SSMAforAccessConsole.EXE -securepassword -list
        ```
  
    > [!NOTE]  
    > 1.  Пароль в открытом тексте, упомянутом в сценарии или файле соединения с сервером, имеет приоритет над зашифрованным паролем в защищенном файле.  
    > 2.  Если в разделе Server файла подключения сервера или файла скрипта нет пароля, или если он не защищен на локальном компьютере, то консоль предложит ввести пароль.  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>Экспорт или Импорт зашифрованных паролей  
Консольное приложение SSMA позволяет экспортировать зашифрованные пароли баз данных, находящиеся в файле на локальном компьютере, в защищенный файл и наоборот. Это помогает сделать зашифрованные пароли независимыми от компьютера. Функция экспорта считывает идентификатор и пароль сервера из локального защищенного хранилища и сохраняет их в зашифрованном файле. Пользователю предлагается ввести пароль для защищенного файла. Убедитесь, что пароль имеет длину 8 символов или более. Этот защищенный файл переносим на разные компьютеры. Функция импорта считывает идентификатор сервера и сведения о пароле из защищенного файла. Пользователю предлагается ввести пароль для защищенного файла и добавить сведения в локально защищенное хранилище.  

### <a name="export-password"></a>Экспорт пароля

1. Введите пароль для защиты экспортированного файла

2. `C:\SSMA\SSMAforAccessConsole.EXE -securepassword -export all "machine1passwords.file"`

3. Введите пароль для защиты экспортированного файла: XXXXXXXX

4. Подтвердите пароль: XXXXXXXX.

5. `C:\SSMA\SSMAforAccessConsole.EXE -p -e "AccessDB_1_1,Sql_1" "machine2passwords.file"`

6. Введите пароль для защиты экспортированного файла: XXXXXXXX

7. Подтвердите пароль: XXXXXXXX.  

### <a name="import-an-encrypted-password"></a>Импорт зашифрованного пароля

1. Введите пароль для защиты импортированного файла

2. `C:\SSMA\SSMAforAccessConsole.EXE -securepassword -import all "machine1passwords.file"`

3. Введите пароль для импорта серверов из зашифрованного файла: XXXXXXXX

4. Подтвердите пароль: XXXXXXXX.

5. `C:\SSMA\SSMAforAccessConsole.EXE -p -i "AccessDB_1,Sql_1" "machine2passwords.file"`

6. Введите пароль для импорта серверов из зашифрованного файла: XXXXXXXX

7. Подтвердите пароль: XXXXXXXX.  

## <a name="see-also"></a>См. также:  
[Запуск консоли SSMA (доступ)](https://msdn.microsoft.com/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  
