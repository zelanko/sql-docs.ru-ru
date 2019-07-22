---
title: Параметры статьи для репликации транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], transactional replication options
- transactional replication, article options
ms.assetid: 3469b185-0ea5-4690-a71c-717230d886b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 42076200732500a58bce7010dd23e6f90c737317
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67904592"
---
# <a name="article-options-for-transactional-replication"></a>Параметры статьи для репликации транзакций
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Для статей в публикациях транзакций существует несколько параметров. Репликация транзакций позволяет выполнять следующее:  
  
-   Задавать способ передачи изменений от издателя подписчикам. Дополнительные сведения см. в статье [Указание способа распространения изменений для статей транзакций](../../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
-   Указывать, что необходима репликация выполнения хранимой процедуры. Это полезно при репликации результатов хранимых процедур, связанных с обслуживанием и работающих с большими объемами данных. Дополнительные сведения см. в статье [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
-   Укажите параметры схемы, например копируются ли ограничения и триггеры на подписчик. Дополнительные сведения см. в разделе [Указание параметров схемы](../../../relational-databases/replication/publish/specify-schema-options.md).  
  
-   Использовать фильтры строк и фильтры столбцов. Фильтрация статей таблиц позволяет создавать секции публикуемых данных. Дополнительные сведения см. в статье [Фильтрация опубликованных данных](../../../relational-databases/replication/publish/filter-published-data.md).  
  
## <a name="see-also"></a>См. также:  
 [Публикация данных и объектов базы данных](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
