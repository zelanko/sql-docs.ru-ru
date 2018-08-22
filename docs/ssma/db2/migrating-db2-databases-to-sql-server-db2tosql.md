---
title: Миграция DB2 баз данных в SQL Server (DB2ToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 14d2e655-af7e-4aa5-ba28-0e3d0d025518
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 26b95bc37f1ba7726c607e6275889ecd6a3fecd9
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "40393905"
---
# <a name="migrating-db2-databases-to-sql-server-db2tosql"></a>Миграция баз данных DB2 в SQL Server (DB2ToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) для DB2 — это комплексное среда, которая поможет вам быстро перенос баз данных DB2 для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure. С помощью SSMA для DB2, можно просмотреть объекты базы данных и данных, оценка баз данных для миграции, миграция объектов базы данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или база данных SQL Azure, и затем перенести данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure. Обратите внимание на то, не может выполнить миграцию схемы SYS и системы DB2.  
  
## <a name="recommended-migration-process"></a>Рекомендуемый процесс миграции  
Для успешного переноса объектов и данных из баз данных DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или база данных SQL Azure, воспользуйтесь следующей процедурой:  
  
1.  [Создание проекта SSMA](http://msdn.microsoft.com/66437b45-4686-4fc7-a91b-ebde45e0f1b0).  
  
    После создания проекта можно задать преобразование проекта, миграции и параметры сопоставления типов. Сведения о параметрах проекта см. в разделе [параметры проекта &#40;преобразования&#41; &#40;DB2ToSQL&#41; ](../../ssma/db2/project-settings-conversion-db2tosql.md) и связанных разделах. Сведения о том, как настроить сопоставления типов данных, см. в разделе [сопоставление DB2 и типов данных SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
2.  [Подключение к базе данных DB2](http://msdn.microsoft.com/5eb5801d-f0c3-4127-97c0-0b1ef49f4844).  
  
3.  [Подключение к SQL Server](http://msdn.microsoft.com/b59803cb-3cc6-41cc-8553-faf90851410e).  
  
4.  [Сопоставление схем DB2 и схемы SQL Server](http://msdn.microsoft.com/05ff7bd4-e60b-4f48-a893-bc2346aa9a8a).  
  
5.  При необходимости [отчетов с оценкой](http://msdn.microsoft.com/9e13eba0-e3cf-4205-974f-c00f982061de) обращаться к таким объектам базы данных для преобразования и оценить время преобразования.  
  
6.  [Преобразование схем DB2](http://msdn.microsoft.com/7947efc3-ca86-4ec5-87ce-7603059c75a0).  
  
7.  [Загрузка преобразованных объектов в SQL Server](http://msdn.microsoft.com/f4ea1ced-9f9f-4a9d-88ab-81dbab64adc3).  
  
    Это можно сделать одним из следующих способов:  
  
    -   Сохраните сценарий и запустите его [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Синхронизируйте объекты базы данных.  
  
8.  [Миграция данных DB2 в SQL Server](http://msdn.microsoft.com/86cbd39f-6dac-409a-9ce1-7dd54403f84b).  
  
9. При необходимости обновите приложений баз данных.  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-db2tosql.md)  
[Начало работы с SSMA для DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/getting-started-with-ssma-for-db2-db2tosql.md)  
  
