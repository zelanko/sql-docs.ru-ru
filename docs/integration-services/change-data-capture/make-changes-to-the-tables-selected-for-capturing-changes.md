---
title: "Внесение изменений в выбранные для отслеживания изменений таблицы | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: change-data-capture
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: makChanToTab
ms.assetid: a309f82a-c6ef-464d-a6ef-df555bfb609a
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4d6df6c0e20cb81a1525998da5934637d6ad6c29
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="make-changes-to-the-tables-selected-for-capturing-changes"></a>Внесение изменений в выбранные для отслеживания изменений таблицы
  В этом диалоговом окне можно выбрать столбцы из выбранной таблицы, изменения данных в которых будут отслеживаться. Можно также изменить **Роль безопасности** и **Экземпляр отслеживания** .  
  
 В этом диалоговом окне можно выбрать столбцы из выбранной таблицы, изменения данных в которых будут отслеживаться.  
  
 **Изменение списка столбцов, включенных в экземпляр CDC**  
  
 Выполните одно из следующих действий (или оба).  
  
-   Установите флажки для всех дополнительных столбцов, которые необходимо включить.  
  
-   Снимите флажки для тех столбцов, которые необходимо исключить.  
  
 **Изменить тип данных для определенного столбца**.  
  
 Для столбца можно выбрать другой тип данных. В качестве нового типа данных можно выбрать только тип, совместимый с исходным.  
  
 Чтобы изменить тип данных, щелкните столбец **Тип данных** и выберите другой тип данных. Доступны только те типы данных, которые совместимы с исходным.  
  
> [!NOTE]  
>  Если нельзя выбрать ни одного типа данных, то раскрывающийся список будет недоступен.  
  
 **Изменение роли безопасности**  
  
 Введите новое имя или измените имя роли безопасности в поле **Роль безопасности** .  
  
 **Изменение или добавление экземпляра отслеживания**  
  
 В поле **Экземпляр отслеживания** введите имя экземпляра отслеживания.  
  
## <a name="see-also"></a>См. также  
 [Как создать экземпляр изменения базы данных SQL Server](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)   
 [Выбор таблиц и столбцов Oracle](../../integration-services/change-data-capture/select-oracle-tables-and-columns.md)  
  
  
