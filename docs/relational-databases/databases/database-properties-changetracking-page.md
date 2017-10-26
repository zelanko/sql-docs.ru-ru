---
title: "Свойства базы данных (страница \"Отслеживание изменений\") | Документация Майкрософт"
ms.custom: 
ms.date: 01/07/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.databaseproperties.changetracking.f1
ms.assetid: 9b929640-bc62-449b-9b06-b5a77b8cf372
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1c55b7b8b39e7b1ec296ee529bc66d2e14256994
ms.openlocfilehash: 6edc4a6d0a4a72e8cec739b78419ce8ce3b4f6cc
ms.contentlocale: ru-ru
ms.lasthandoff: 10/12/2017

---
# <a name="database-properties-changetracking-page"></a>Свойства базы данных (страница «Отслеживание изменений»)
  Эта страница позволяет просмотреть или изменить параметры отслеживания изменений для выбранной базы данных. Дополнительные сведения о параметрах, доступных на этой странице, см. в разделе [Включение и отключение отслеживания изменений (SQL Server)](../../relational-databases/track-changes/enable-and-disable-change-tracking-sql-server.md).  
  
## <a name="options"></a>Параметры  
 **Отслеживание изменений**  
 Используйте этот параметр, чтобы включить или отключить отслеживание изменений для базы данных.  
  
 Чтобы включить отслеживание изменений, необходимо иметь разрешение на изменение базы данных.  
  
 Значение **True** задает параметр базы данных, позволяющий включить отслеживание изменений для отдельных таблиц.  
  
 Можно также настроить отслеживание изменений с помощью инструкции [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md).  
  
 **Срок хранения**  
 Указывает минимальный срок хранения данных отслеживания изменений в базе данных. Данные удаляются, только если параметр **Автоматическая очистка** имеет значение **True**.  
  
 Значение по умолчанию — 2.  
  
 **Единицы измерения срока хранения**  
 Указывает единицы изменения для значения параметра «Срок хранения». Может быть выбрано одно из следующих значений: **Дней**, **Часов**или **Минут**. Значение по умолчанию — **Дней**.  
  
 Минимальный срок хранения составляет 1 минуту. Максимальный срок хранения не предусмотрен.  
  
 **Автоматическая очистка**  
 Указывает, производится ли автоматическое удаление данных отслеживания изменений по истечении заданного срока хранения.  
  
 Если параметр **Автоматическая очистка** включен, то любой ранее заданный срок хранения сбрасывается в значение по умолчанию — 2 дня.  
  
## <a name="see-also"></a>См. также:  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)  
  
  

