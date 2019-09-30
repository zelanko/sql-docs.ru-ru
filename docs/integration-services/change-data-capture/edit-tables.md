---
title: Редактирование таблиц | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- tabProps
ms.assetid: fed8fada-2abc-45e2-8228-0656f9c599cb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9c25ae3771a8ca7087f4668b717643fbe4b2648
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71298798"
---
# <a name="edit-tables"></a>Редактирование таблиц

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  На вкладке **Таблицы** можно изменять таблицы и столбцы, выбранные в базе данных-источнике Oracle. Эта вкладка содержит следующие элементы.  
  
 **Список «Таблица»**  
 Список таблиц состоит из трех столбцов:  
  
-   **Имя таблицы Oracle**. Имя таблицы с указанием схемы таблицы.  
  
-   **Экземпляр системы отслеживания**. Имя экземпляра системы отслеживания, используемого для внутреннего именования объектов системы отслеживания измененных данных. Значение экземпляра отслеживания не может быть равно NULL. Если имя не указано, то оно образуется из имен исходных схемы и таблицы в формате `<schema-name>_<table-name>.` Длина имени экземпляра отслеживания не должна превышать 100 символов, а само имя должно быть уникальным в рамках базы данных. Щелкните любую ячейку в этом столбце, чтобы изменить **capture_instance**вручную.  
  
-   **Роль безопасности**. Имя роли базы данных, используемой для получения доступа к информации об изменениях. Щелкните любую ячейку в этом столбце, чтобы изменить **security_role**вручную.  
  
 **Добавить таблицы**  
 Нажмите кнопку **Добавить таблицы** , чтобы открыть диалоговое окно "Выбор таблицы", где вы можете [добавить таблицы в экземпляр CDC](../../integration-services/change-data-capture/add-tables-to-a-cdc-instance.md). Если доступ к базе данных Oracle осуществляется впервые в ходе данного сеанса, необходимо [Connect to Oracle](../../integration-services/change-data-capture/connect-to-oracle.md).  
  
 **Изменить**  
 Выберите таблицу из списка, а затем **Правка** , чтобы открыть диалоговое окно **Свойства** этой таблицы, позволяющее [Изменение свойств таблицы](../../integration-services/change-data-capture/edit-the-table-properties.md).  
  
> [!NOTE]  
>  Нельзя изменить сопоставление типа для таблиц, у которых уже есть зеркальные таблицы. Это можно сделать только для новых таблиц.  
  
 **Удалить**  
 Выберите таблицу из списка и нажмите **Удалить** , чтобы удалить таблицу из экземпляра CDC.  
  
## <a name="see-also"></a>См. также:  
 [Как изменить свойства экземпляра CDC](../../integration-services/change-data-capture/how-to-edit-the-cdc-instance-properties.md)   
 [Выбор таблиц и столбцов Oracle](../../integration-services/change-data-capture/select-oracle-tables-and-columns.md)  
  
  
