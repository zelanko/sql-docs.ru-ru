---
title: "Выберите столбцы и таблицы Oracle | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- selTabCol
ms.assetid: bf73f80e-a954-4c5f-874e-17fdd4082715
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a32dc9416e79380cb9ce289960ad2ab0942e99fb
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="select-oracle-tables-and-columns"></a>Выберите столбцы и таблицы Oracle
  Страница «Выбор столбцов и таблиц Oracle» используется для выбора таблиц из базы данных-источника Oracle, изменения в которых будут отслеживаться. Эта страница содержит следующие элементы:  
  
## <a name="options"></a>Параметры  
 **Список «Таблица»**  
 Список таблиц состоит из трех столбцов:  
  
-   **Имя таблицы Oracle**: имя таблицы с указанием схемы.  
  
-   **Экземпляр отслеживания**: имя экземпляра отслеживания, используемое для именования объектов отслеживания изменений данных по экземплярам. Значение экземпляра отслеживания не может быть равно NULL.  
  
     Если это имя не задано, то оно является производным от имени схемы источника и имени исходной таблицы в формате `<schema-name>_<table-name>`. Длина имени экземпляра отслеживания не может превышать 100 символов, оно должно быть уникальным в пределах базы данных.  
  
     Щелкните любую ячейку в этом столбце, чтобы изменить **capture_instance**вручную.  
  
-   **Роль безопасности**. Имя шлюзовой роли базы данных, используемой для управления доступом к информации об изменениях.  
  
     Щелкните любую ячейку в этом столбце, чтобы изменить **security_role**вручную.  
  
 **Добавить таблицы**  
 Нажмите кнопку **Добавить таблицы** , чтобы открыть диалоговое окно "Выбор таблицы", где вы можете [выбрать таблицы Oracle для отслеживания изменений](../../integration-services/change-data-capture/select-oracle-tables-for-capturing-changes.md).  
  
 **Правка**  
 Выберите таблицу из списка, а затем **Правка** , чтобы открыть диалоговое окно **Свойства** этой таблицы, позволяющее [вносить изменений в выбранные для отслеживания изменений таблицы](../../integration-services/change-data-capture/make-changes-to-the-tables-selected-for-capturing-changes.md).  
  
 **Удалить**  
 Выберите таблицу из списка и нажмите **Удалить** , чтобы удалить таблицу из экземпляра CDC.  
  
 После [выбора таблиц Oracle для отслеживания изменений](../../integration-services/change-data-capture/select-oracle-tables-for-capturing-changes.md) и (или) [внесения изменений в выбранные для отслеживания изменений таблицы](../../integration-services/change-data-capture/make-changes-to-the-tables-selected-for-capturing-changes.md) с помощью соответствующих диалоговых окон нажмите кнопку **Далее** , чтобы [создать и запустить скрипт дополнительного журналирования](../../integration-services/change-data-capture/generate-and-run-the-supplemental-logging-script.md).  
  
## <a name="see-also"></a>См. также  
 [Как создать экземпляр изменения базы данных SQL Server](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)   
 [Редактирование таблиц](../../integration-services/change-data-capture/edit-tables.md)   
 [Добавление таблиц в экземпляр CDC](../../integration-services/change-data-capture/add-tables-to-a-cdc-instance.md)   
 [Изменение свойств таблицы](../../integration-services/change-data-capture/edit-the-table-properties.md)  
  
  
