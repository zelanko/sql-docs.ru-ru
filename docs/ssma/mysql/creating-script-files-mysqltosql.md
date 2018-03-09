---
title: "Создание файлов скрипта (MySQLToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-mysql
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Creating script files, configuring console settings
- Creating script files, Script commands
- Creating script files, script file validation
- Creating script files, server connection parameters
ms.assetid: b4608fe7-c777-4ba5-b853-4402f02109e3
caps.latest.revision: "22"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ddfe50aa62403c1dda26ebf1f2017bdf45bf7864
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="creating-script-files-mysqltosql"></a>Создание файлов скрипта (MySQLToSQL)
В первую очередь перед запуском приложения консоли SSMA для создания файла сценария и при необходимости создания файла значение переменной и файла подключения сервера.  
  
Файл сценария можно разделить на три раздела viz..,:  
  
1.  **config:** позволяет пользователю задавать параметры конфигурации для консольного приложения.  
  
2.  **серверы:** позволяет пользователю задать исходную и целевую определений с сервера. Также можно в файле подключения отдельный сервер.  
  
3.  **команды сценария:** позволяет пользователю выполнять команды SSMA рабочего процесса.  
  
Ниже подробно описан каждый раздел:  
  
## <a name="configuring-mysql-console-settings"></a>Настройка параметров консоли MySQL  
Конфигурации сценария, отображаются в файле скрипта консоли.  
  
Если какие-либо элементы в узле конфигурации заданы, они заданы как глобальное значение т. е. они применимы для всех команд скрипта. Эти элементы конфигурации можно также задать в пределах каждой команды в разделе команды сценария, если требуется переопределить глобальные настройки.  
  
Доступны следующие варианты настраивается пользователем.  
  
1.  **Поставщик окна вывода:** Если подавления сообщений атрибут имеет значение «true», связанные с командой сообщения не отображаются на консоли. Ниже дается описание атрибутов:  
  
    -   Назначение: Указывает, должна ли выходные данные get на печать в файл или stdout. Это по умолчанию — false.  
  
    -   Имя файла: путь к файлу (необязательно).  
  
    -   подавлять сообщения: подавляет сообщения на консоль. Это значение по умолчанию «false».  
  
    **Пример:**  
  
    ```xml  
    <output-providers>  
  
      <output-window  
  
        suppress-messages="<true/false>"   (optional)  
  
        destination="<file/stdout>"        (optional)  
  
        file-name="<file-name>"            (optional)  
  
       />  
  
    </output-providers>  
    ```  
    *или*  
  
    ```xml  
    <…All commands…>  
  
      <output-window  
  
         suppress-messages="<true/false>"   (optional)  
  
         destination="<file/stdout>"        (optional)  
  
         file-name="<file-name>"            (optional)  
  
       />  
  
    </…All commands…>  
    ```  
  
2.  **Поставщик подключения данных миграции:** определяет, какая исходной или целевой сервер будет считаться для переноса данных.  Источник использование последние использованные указывает, что последнего используется исходного сервера используется для переноса данных. Аналогичным образом целевой использование последние использованные указывает, что последнего используется целевого сервера используется для переноса данных. Пользователь также может указать сервер (исходная или целевая) с помощью атрибутов исходном или целевом сервере.  
  
    Только один указанный атрибут может использоваться или т. е.:  
  
    - Источник использование последние использованные = «true» (по умолчанию) или исходный сервер = «source_servername»  
  
    - target использование последние использованные = «true» (по умолчанию) или целевой сервер = «target_servername»  
  
    **Пример:**  
  
    ```xml  
    <output-providers>  
  
      <data-migration-connection  source-use-last-used="true"  
  
                                  target-server="<target-server-unique-name>"/>  
  
    </output-providers>  
    ```  
    *или*  
  
    ```xml  
    <migrate-data>  
  
      <data-migration-connection   source-server="<source-server-unique-name>"  
  
                                   target-use-last-used="true"/>  
  
    </migrate-data>  
    ```  
  
3.  **Всплывающее окно ввода пользователя:** это позволяет обработку ошибок, когда объекты загружаются из базы данных. Пользователь предоставляет режимы ввода, и в случае возникновения ошибки консоли выполняется как пользователь указывает.  
  
    Следующие режимы.  
  
    -   **Попросите пользователя -** предлагает пользователю continue('yes') или ошибка («нет»).  
  
    -   **Ошибка -** консоль выводится сообщение об ошибке и прекращает.  
  
    -   **Продолжить-** консоли продолжается с выполнением.  
  
    По умолчанию используется режим **ошибка**.  
  
    **Пример:**  
  
    ```xml  
    <output-providers>  
  
      <user-input-popup mode="<ask-user/continue/error>"/>  
  
    </output-providers>  
    ```  
    *или*  
  
    ```xml  
    <!-- Connect to target database -->  
  
    <connect-target-database server="<target-server-unique-name>">  
  
      <user-input-popup mode="<ask-user/continue/error>"/>  
  
    </connect-target-database>  
    ```  
  
4.  **Повторное подключение поставщика:** позволяет пользователю задать повторное подключение, если параметры отказов при соединениях. Это можно задать для исходных и целевых серверов.  
  
    Доступны режима восстановления подключения.  
  
    -   повторного подключения и последней используется сервером: Если соединение не активен, предпринимается попытка повторного подключения к последней сервера, используемого не более 5 раз.  
  
    -   создать произошла ошибка: Если соединение не активна, возникнет ошибка.  
  
    По умолчанию используется режим **создания произошла ошибка**.  
  
    **Пример:**  
  
    ```xml  
    <output-providers>  
  
    <reconnect-manager  on-source-reconnect="<reconnect-to-last-used-server/generate-an-error>"  
  
                        on-target-reconnect="<reconnect-to-last-used-server/generate-an-error>"/>  
  
    </output-providers>  
    ```  
    *или*  
  
    ```xml  
    <!--synchronization-->  
  
    <synchronize-target>  
  
      <reconnect-manager on-target-reconnect="reconnect-to-last-used-server"/>  
  
    </synchronize-target>  
    ```  
    *или*  
  
    ```xml  
    <!--data migration-->  
  
    <migrate-data server="target-server-unique-name">  
  
      <reconnect-manager  
  
        on-source-reconnect="reconnect-to-last-used-server"  
  
        on-target-reconnect="generate-an-error"/>  
  
    </migrate-data>  
    ```  
  
5.  **Поставщик перезаписи преобразователя:** это позволяет пользователю обрабатывать объекты, которые уже присутствуют на конечном метабазы. Следующие возможные действия.  
  
    -   Ошибка: консоль выводится сообщение об ошибке и прекращает.  
  
    -   Перезаписать: перезаписывает существующие значения объекта. Это действие выполняется по умолчанию.  
  
    -   Пропустить: консоль пропускает объекты, которые уже существуют в базе данных  
  
    -   Попросите пользователя: предлагает пользователю ввести данные («Да» или «нет»)  
  
    **Пример:**  
  
    ```xml  
    <output-providers>  
  
      <object-overwrite action="<error/skip/overwrite/ask-user>"/>  
  
    </output-providers>  
    ```  
    *или*  
  
    ```xml  
    <convert-schema object-name="<object-name>">  
  
      <object-overwrite action="<error/skip/overwrite/ask-user>"/>  
  
    </convert-schema>  
    ```  
  
6.  **Сбой поставщика необходимые условия:** это позволяет пользователю обрабатывать все необходимые компоненты, необходимые для обработки команды. По умолчанию строгий режим — «false». Если задано значение «true», исключение формируется для сбоя выполнение необходимых условий.  
  
    **Пример:**  
  
    ```xml  
    <output-providers>  
  
      <prerequisites strict-mode="<true/false>"/>  
  
    </output-providers>  
    ```  
  
7.  **Операция остановки:** во время промежуточного операции, если пользователь хочет остановить эту операцию, затем **«Ctrl + C»** можно использовать сочетание клавиш. SSMA для консоли MySQL будет ожидать завершения операции и прекращает выполнение консоли.  
  
    Если пользователь хочет остановить выполнение немедленно, затем **«Ctrl + C»** сочетание клавиш можно снова нажата для внезапному прекращению SSMA консольного приложения  
  
8.  **Ход выполнения поставщик:** сообщает о ходе выполнения каждой команды консоли. Эта возможность отключена по умолчанию. Атрибуты хода составляют:  
  
    -   off  
  
    -   каждые 1%  
  
    -   каждые 2%  
  
    -   каждые 5%  
  
    -   каждые 10%  
  
    -   каждые 20%  
  
    **Пример:**  
  
    ```xml  
    <output-providers>  
  
      <progress-reporting enable="<true/false>"          (optional)  
  
                         report-messages="<true/false>"  (optional)  
  
                         report-progress="<every-1%/every-2%/every-5%/every-10%/every-20%/off>" (optional)/>  
  
    </output-providers>  
    ```  
    *или*  
  
    ```xml  
    <…All commands…>  
  
      <progress-reporting  
  
        enable="<true/false>"              (optional)  
  
        report-messages="<true/false>"     (optional)  
  
        report-progress="<every-1%/every-2%/every-5%/every-10%/every-20%/off>"     (optional)/>  
  
    </…All commands…>  
    ```  
  
9. **Степень подробности ведения журнала:** уровень детализации журнала наборов. Это соответствует с параметром всех категорий в пользовательском Интерфейсе. По умолчанию уровень детализации журнала — «ошибка».  
  
    Следующие параметры уровня ведения журнала.  
  
    -   Неустранимая ошибка: регистрируются только Неустранимая ошибка сообщения.  
  
    -   Ошибка: записываются только сообщения об ошибках и Неустранимая ошибка.  
  
    -   Предупреждение: регистрируются все уровни, за исключением сообщений отладки и сведения.  
  
    -   информация: все уровни, за исключением того, выводятся сообщения отладки.  
  
    -   Отладка: все уровни в журнал сообщений.  
  
    > [!NOTE]  
    > Обязательные сообщения регистрируются на любом уровне.  
  
    **Пример:**  
  
    ```xml  
    <output-providers>  
  
      <log-verbosity level="<fatal-error/error/warning/info/debug>"/>  
  
    </output-providers>  
    ```  
    *или*  
  
    ```xml  
    <…All commands…>  
  
      <log-verbosity level="<fatal-error/error/warning/info/debug>"/>  
  
    </…All commands…>  
    ```  
  
10. **Переопределение шифрование пароля:** значение 'true' незашифрованные пароли указанным в разделе Определение сервера файла соединения на сервере или в файле скрипта переопределения зашифрованный пароль, сохраненный в защищенное хранилище, если существует. Если пароль не указан в виде открытого текста, пользователю предлагается ввести пароль.  
  
    Здесь возникают два варианта:  
  
    1.  Если переопределить параметр — **false**, порядок поиска будет защищенного хранилища -&gt;файла скрипта -&gt;файла подключения сервера -&gt; запрашивать у пользователей.  
  
    2.  Если переопределить параметр — **true**, порядок поиска будет файл скрипта -&gt;файла подключения сервера -&gt;запрашивать у пользователей.  
  
    **Пример:**  
  
    ```xml  
    <output-providers>  
  
      <encrypted-password override="<true/false>"/>  
  
    </output-providers>  
    ```  
  
Ненастраиваемые параметр —:  
  
-   **Максимальное попыток подключения:** Если установленное соединение времени ожидания или останавливается из-за сбоя сети, сервер необходимо повторно подключить. Попыток повторного соединения разрешено более **5** повторных попыток, после чего консоль автоматически выполняет повторное подключение. Средство автоматическое переподключение уменьшает вашей трудозатраты в повторным выполнением скрипта.  
  
## <a name="server-connection-parameters"></a>Параметры подключения сервера  
Параметры подключения сервера можно определить в файле скрипта или в файле соединения сервера. Обратитесь к [Создание файлы подключения Server &#40; MySQLToSQL &#41; ](../../ssma/mysql/creating-the-server-connection-files-mysqltosql.md) более подробные сведения.  
  
## <a name="script-commands"></a>Команды скриптов  
Файл скрипта содержит последовательность команд рабочего процесса миграции в формате XML. SSMA консольное приложение обрабатывает миграции порядке команды отображаются в файле скрипта.  
  
Например, перенос данных обычно конкретной таблицы в базе данных MySQL следует иерархия: база данных —&gt; таблицы.  
  
При выполнении всех команд в файле скрипта SSMA консольное приложение завершает работу и возвращает элемент управления для пользователя. Содержимое файла скрипта, больше или меньше статический с сведения о переменных, содержащихся в [файлы значение переменной](http://msdn.microsoft.com/en-us/1dc56a7b-8e3a-4576-ad4f-47050bf7e28a) или в отдельном разделе в файлах скриптов для значений переменных.  
  
**Пример:**  
  
```xml  
<!--Sample of script file commands -->  
  
<ssma-script-file>  
  
  <script-commands>  
  
    <create-new-project project-folder="<project-folder>"  
  
                        project-name="<project-name>"  
  
                        overwrite-if-exists="<true/false>"/>  
  
    <connect-source-database server="<source-server-unique-name>"/>  
  
    <save-project/>  
  
    <close-project/>  
  
  </script-commands>  
  
</ssma-script-file>  
```  
В папке примеров сценариев консоли каталога продукта предоставляются шаблоны, состоящий из 3 файлы сценариев (для выполнения различных сценариев), значение переменной файл и файл подключения сервера:  
  
-   AssessmentReportGenerationSample.xml  
  
-   ConversionAndDataMigrationSample.xml  
  
-   SqlStatementConversionSample.xml  
  
-   VariableValueFileSample.xml  
  
-   ServersConnectionFileSample.xml  
  
Шаблоны (файлы) можно выполнять после изменения параметров, отображаемых в ней для релевантности.  
  
Полный список команд сценария можно найти в [выполнении консоли SSMA &#40; MySQLToSQL &#41;](../../ssma/mysql/executing-the-ssma-console-mysqltosql.md)  
  
## <a name="script-file-validation"></a>Проверка файла скрипта  
Пользователь может легко проверить свой файл скрипта соответствие файлу определения схемы **«M2SSConsoleScriptSchema.xsd»** доступны в папке «Схемы».  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг в работе консоли — [Создание переменной значение файлов &#40; MySQLToSQL &#41; ](../../ssma/mysql/creating-variable-value-files-mysqltosql.md).  
  
## <a name="see-also"></a>См. также:  
[Создание файлов значение переменной &#40; MySQLToSQL &#41;](../../ssma/mysql/creating-variable-value-files-mysqltosql.md)  
  
