---
title: Переход с Oracle баз данных в SQL Server (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 04/22/2018
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1d196dd6-4322-4c98-bb72-602c57d96134
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: f20b7271932cbbcc0538fc9923e45b2fc029f646
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983206"
---
# <a name="migrating-oracle-databases-to-sql-server-oracletosql"></a>Миграция баз данных Oracle в SQL Server (OracleToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) для Oracle — это комплексное среда, которая поможет вам быстро перенос баз данных Oracle для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], база данных SQL Azure или хранилище данных SQL Azure. С помощью SSMA для Oracle, можно просмотреть объекты базы данных и данных, оценка баз данных для миграции, миграция объектов базы данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], база данных SQL Azure или хранилище данных SQL Azure, и затем перенести данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], база данных SQL Azure, или данных SQL Azure Хранилище данных. Обратите внимание на то, не может выполнить миграцию схемы SYS и системе Oracle.
  
## <a name="recommended-migration-process"></a>Рекомендуемый процесс миграции  
Для успешного переноса объектов и данных из баз данных Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], база данных SQL Azure или хранилище данных SQL Azure, воспользуйтесь следующей процедурой:
  
1.  [Создание нового проекта SSMA](http://msdn.microsoft.com/ee5d94c0-c7a6-4779-bd32-729bdaf61e1b).  
  
    После создания проекта можно задать преобразование проекта, миграции и параметры сопоставления типов. Сведения о параметрах проекта см. в разделе [Настройка параметров проекта &#40;OracleToSQL&#41;](../../ssma/oracle/setting-project-options-oracletosql.md). Сведения о том, как настроить сопоставления типов данных, см. в разделе [сопоставление Oracle и типы данных SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
2.  [Подключиться к серверу базы данных Oracle](http://msdn.microsoft.com/e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6).  
  
3.  [Подключитесь к экземпляру SQL Server,](http://msdn.microsoft.com/1b2a8059-1829-4904-a82f-9c06de1e245f).  
  
4.  [Сопоставление схем базы данных Oracle и схем баз данных SQL Server](http://msdn.microsoft.com/0edeaa08-9c5d-4e3a-bc15-b9a1f0c8a9dc).  
  
5.  При необходимости [создание отчетов с оценкой](http://msdn.microsoft.com/4de9bcf6-1346-4740-87f9-7f24a8226357) обращаться к таким объектам базы данных для преобразования и оценить время преобразования.  
  
6.  [Преобразование схем баз данных Oracle в SQL Server схемы](http://msdn.microsoft.com/e021182d-31da-443d-b110-937f5db27272).  
  
7.  [Загрузка преобразованных объектов в SQL Server](http://msdn.microsoft.com/a8ae33b2-1883-4785-922b-ea0e31c0b37a).  
  
    Это можно сделать одним из следующих способов:  
  
    -   Сохраните сценарий и запустите его [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
    -   Синхронизируйте объекты базы данных.  
  
8.  [Перенос данных в SQL Server](http://msdn.microsoft.com/e23c5268-41ed-4e55-9fe7-a11376202a13).  
  
9. При необходимости обновите приложений баз данных.  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md)  
[Начало работы с SSMA для Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/getting-started-with-ssma-for-oracle-oracletosql.md)  
  
