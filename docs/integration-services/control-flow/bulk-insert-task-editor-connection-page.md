---
title: "Редактор задачи &#171;Массовая вставка&#187; (страница &#171;Соединение&#187;) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.bulkinserttask.connection.f1"
helpviewer_keywords: 
  - "редактор задачи «Массовая вставка»"
ms.assetid: 51252c20-8865-4ede-a3fd-bd73a968f47d
caps.latest.revision: 30
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 30
---
# Редактор задачи &#171;Массовая вставка&#187; (страница &#171;Соединение&#187;)
  Страница **Соединение** диалогового окна **Редактор задачи «Массовая вставка»** используется для указания источника и места назначения операции массовой вставки и формата для использования.  
  
 Дополнительные сведения о работе с массовыми вставками см. в разделах [Задача "Массовая вставка"](../../integration-services/control-flow/bulk-insert-task.md) и [Файлы форматирования для импорта или экспорта данных (SQL Server)](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).  
  
## Параметры  
 **Соединение**  
 Выберите диспетчер подключений OLE DB из списка или щелкните \<**Создать подключение...**>, чтобы создать соединение.  
  
 **См. также: ** [Диспетчер подключений OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md), [Настройка диспетчера подключений OLE DB](../../integration-services/connection-manager/configure-ole-db-connection-manager.md)  
  
 **DestinationTable**  
 Введите имя целевой таблицы или представления или выберите таблицу или представление из списка.  
  
 **Формат**  
 Выберите источник формата для массовой вставки. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**Использовать файл**|Выберите файл, содержащий спецификацию формата. При выборе этого параметра отображается динамический параметр **FormatFile**.|  
|**Указать**|Укажите формат. При выборе этого параметра отображаются динамические параметры **RowDelimiter** и **ColumnDelimiter**.|  
  
 **Файл**  
 Выберите диспетчер подключений файлов или неструктурированных файлов из списка или щелкните \<**Создать подключение...**>, чтобы создать соединение.  
  
 Расположение файла задается относительно компонента SQL Server Database Engine, указанного в диспетчере соединений для выполнения этой задачи. Доступ к тестовому файлу можно получить с помощью компонента SQL Server Database Engine на локальном жестком диске на сервере или через общий диск или сопоставленный диск относительно SQL Server. Этот файл не имеет доступа к среде выполнения служб SSIS.  
  
 Если пользователь осуществляет доступ к исходному файлу с помощью диспетчера соединений с неструктурированным файлом, в задаче «Массовая вставка» не используется формат, указанный в диспетчере соединений с неструктурированными файлами. Вместо этого задача "Массовая вставка" использует либо формат, указанный в файле форматирования, либо значения свойств задачи RowDelimiter и ColumnDelimiter.  
  
 **См. также:** [Диспетчер подключений](../../integration-services/connection-manager/file-connection-manager.md), [Редактор диспетчера соединения файлов](../../integration-services/connection-manager/file-connection-manager-editor.md), [Диспетчер соединений с неструктурированными файлами](../../integration-services/connection-manager/flat-file-connection-manager.md), [Редактор диспетчера соединений с неструктурированными файлами (страница "Общие")](../../integration-services/connection-manager/flat-file-connection-manager-editor-general-page.md), [Редактор диспетчера соединений с неструктурированными файлами (страница "Столбцы")](../../integration-services/connection-manager/flat-file-connection-manager-editor-columns-page.md), [Редактор диспетчера соединений с неструктурированными файлами (страница "Дополнительно")](../../integration-services/connection-manager/flat-file-connection-manager-editor-advanced-page.md)  
  
 **Обновить таблицы**  
 Обновите список таблиц и представлений.  
  
## Динамические параметры формата  
  
### Формат = Использовать файл  
 **FormatFile**  
 Введите путь к файлу форматирования или нажмите кнопку с многоточием **(…)** для поиска файла формата.  
  
### Формат = Указать  
 **RowDelimiter**  
 Укажите разделитель строк в файле источника. Значением по умолчанию является **{CR}{LF}**.  
  
 **ColumnDelimiter**  
 Укажите разделитель столбцов в файле источника. Значение по умолчанию составляет **Табуляция**.  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "Массовая вставка" (страница "Общие")](../../integration-services/control-flow/bulk-insert-task-editor-general-page.md)   
 [Редактор задачи "Массовая вставка" (страница "Параметры")](../../integration-services/control-flow/bulk-insert-task-editor-options-page.md)   
 [Страница «Выражения»](../../integration-services/expressions/expressions-page.md)   
 [BULK INSERT (Transact-SQL)](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [Поток управления](../../integration-services/control-flow/control-flow.md)  
  
  