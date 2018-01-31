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
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- makChanToTab
ms.assetid: a309f82a-c6ef-464d-a6ef-df555bfb609a
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9ed1da57a1599bd386b8eed3d23db92dd427b36b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
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
  
## <a name="see-also"></a>См. также:  
 [Как создать экземпляр изменения базы данных SQL Server](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)   
 [Выбор таблиц и столбцов Oracle](../../integration-services/change-data-capture/select-oracle-tables-and-columns.md)  
  
  
