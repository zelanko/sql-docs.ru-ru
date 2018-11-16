---
title: Свойства базы данных (страница "Отслеживание изменений") | Документация Майкрософт
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.databaseproperties.changetracking.f1
ms.assetid: 9b929640-bc62-449b-9b06-b5a77b8cf372
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: bd6dc5a98da7bf06f4bd24bd045fcc76d880e93d
ms.sourcegitcommit: 96b2355d54dfad259826e88bdff91cc9344e16f2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2018
ms.locfileid: "51350036"
---
# <a name="database-properties-changetracking-page"></a>Свойства базы данных (страница «Отслеживание изменений»)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
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
  
  
