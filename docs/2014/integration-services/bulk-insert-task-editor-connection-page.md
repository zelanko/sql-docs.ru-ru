---
title: Массовое редактор задачи Insert (страница «соединение») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.bulkinserttask.connection.f1
helpviewer_keywords:
- Bulk Insert Task Editor
ms.assetid: 51252c20-8865-4ede-a3fd-bd73a968f47d
caps.latest.revision: 30
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ed6ab27e4c60aa398cafe1be0d4bbcb19ce3bb3d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201814"
---
# <a name="bulk-insert-task-editor-connection-page"></a>Редактор задачи «Массовая вставка» (страница «Соединение»)
  Страница **Соединение** диалогового окна **Редактор задачи «Массовая вставка»** используется для указания источника и места назначения операции массовой вставки и формата для использования.  
  
 Дополнительные сведения о работе с массовыми вставками см. в разделах [Задача "Массовая вставка"](control-flow/bulk-insert-task.md) и [Файлы форматирования для импорта или экспорта данных (SQL Server)](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).  
  
## <a name="options"></a>Параметры  
 **Соединение**  
 Выберите диспетчер подключений OLE DB в списке или щелкните \<**Создать подключение...**>, чтобы создать соединение.  
  
 **См. также:**  [Диспетчер подключений OLE DB](connection-manager/ole-db-connection-manager.md), [Настройка диспетчера подключений OLE DB](../../2014/integration-services/configure-ole-db-connection-manager.md)  
  
 **DestinationTable**  
 Введите имя целевой таблицы или представления или выберите таблицу или представление из списка.  
  
 **Формат**  
 Выберите источник формата для массовой вставки. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Использовать файл**|Выберите файл, содержащий спецификацию формата. При выборе этого параметра отображается динамический параметр **FormatFile**.|  
|**Указать**|Укажите формат. При выборе этого параметра отображаются динамические параметры, `RowDelimiter` и `ColumnDelimiter`.|  
  
 **Файл**  
 Выберите диспетчер подключений файлов или неструктурированных файлов в списке или щелкните \<**Создать подключение...**>, чтобы создать соединение.  
  
 Расположение файла задается относительно компонента SQL Server Database Engine, указанного в диспетчере соединений для выполнения этой задачи. Доступ к тестовому файлу можно получить с помощью компонента SQL Server Database Engine на локальном жестком диске на сервере или через общий диск или сопоставленный диск относительно SQL Server. Этот файл не имеет доступа к среде выполнения служб SSIS.  
  
 Если пользователь осуществляет доступ к исходному файлу с помощью диспетчера соединений с неструктурированным файлом, в задаче «Массовая вставка» не используется формат, указанный в диспетчере соединений с неструктурированными файлами. Вместо этого задача "Массовая вставка" использует либо формат, указанный в файле форматирования, либо значения свойств задачи RowDelimiter и ColumnDelimiter.  
  
 **См. также:** [Диспетчер подключений](connection-manager/file-connection-manager.md), [Редактор диспетчера соединения файлов](../../2014/integration-services/file-connection-manager-editor.md), [Диспетчер соединений с неструктурированными файлами](connection-manager/flat-file-connection-manager.md), [Редактор диспетчера соединений с неструктурированными файлами (страница "Общие")](general-page-of-integration-services-designers-options.md), [Редактор диспетчера соединений с неструктурированными файлами (страница "Столбцы")](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md), [Редактор диспетчера соединений с неструктурированными файлами (страница "Дополнительно")](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)  
  
 **Обновить таблицы**  
 Обновите список таблиц и представлений.  
  
## <a name="format-dynamic-options"></a>Динамические параметры формата  
  
### <a name="format--use-file"></a>Формат = Использовать файл  
 **FormatFile**  
 Введите путь к файлу форматирования или нажмите кнопку с многоточием **(…)** для поиска файла формата.  
  
### <a name="format--specify"></a>Формат = Указать  
 `RowDelimiter`  
 Укажите разделитель строк в файле источника. Значением по умолчанию является **{CR}{LF}**.  
  
 `ColumnDelimiter`  
 Укажите разделитель столбцов в файле источника. Значение по умолчанию составляет **Табуляция**.  
  
## <a name="see-also"></a>См. также  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Массовая вставка редактор задачи &#40;страница "Общие"&#41;](../../2014/integration-services/bulk-insert-task-editor-general-page.md)   
 [Массовая вставка редактор задачи &#40;страница параметров&#41;](../../2014/integration-services/bulk-insert-task-editor-options-page.md)   
 [Страница «выражения»](expressions/expressions-page.md)   
 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [Поток управления](control-flow/control-flow.md)  
  
  
