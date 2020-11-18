---
title: Перенос баз данных DB2 в SQL Server (DB2ToSQL) | Документация Майкрософт
description: Используйте этот рекомендуемый процесс для переноса баз данных DB2 в SQL Server или базу данных SQL Azure с помощью Помощник по миграции SQL Server (SSMA).
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 14d2e655-af7e-4aa5-ba28-0e3d0d025518
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: e31d4b1d31cb186276d8424f8c49450cb4ce9406
ms.sourcegitcommit: 82b92f73ca32fc28e1948aab70f37f0efdb54e39
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94869533"
---
# <a name="migrating-db2-databases-to-sql-server-db2tosql"></a>Перенос баз данных DB2 в SQL Server (DB2ToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Помощник по миграции (SSMA) для DB2 — это Комплексная среда, которая помогает быстро перенести базы данных DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure или. С помощью SSMA для DB2 можно просматривать объекты и данные базы данных, оценивать базы данных для миграции, переносить объекты базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure, а затем переносить данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure или из нее. Обратите внимание, что нельзя перенести схемы SYS и SYSTEM DB2.  
  
## <a name="recommended-migration-process"></a>Рекомендуемый процесс миграции  
Чтобы успешно перенести объекты и данные из баз данных DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базу данных SQL Azure, используйте следующую процедуру.  
  
1.  [Новый проект SSMA](./new-project-db2tosql.md).  
  
    После создания проекта можно задать параметры преобразования проекта, миграции и сопоставления типов. Сведения о параметрах проекта см. в разделе [Параметры проекта &#40;преобразование&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md) и связанные разделы. Сведения о настройке сопоставлений типов данных см. в разделе [Сопоставление типов данных DB2 и SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
2.  [Подключитесь к базе данных DB2](./connecting-to-db2-database-db2tosql.md).  
  
3.  [Подключение к SQL Server](./connecting-to-sql-server-db2tosql.md).  
  
4.  [Сопоставьте схемы DB2 с SQL Server схемами](./mapping-db2-schemas-to-sql-server-schemas-db2tosql.md).  
  
5.  При необходимости [отчеты об оценке](./assessment-report-db2tosql.md) позволяют оценить объекты базы данных для преобразования и оценить время преобразования.  
  
6.  [Преобразование схем DB2](./converting-db2-schemas-db2tosql.md).  
  
7.  [Загрузите преобразованные объекты базы данных в SQL Server](./loading-converted-database-objects-into-sql-server-db2tosql.md).  
  
    Это можно сделать одним из следующих способов:  
  
    -   Сохраните скрипт и запустите его в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    -   Синхронизируйте объекты базы данных.  
  
8.  [Перенос данных DB2 в SQL Server](./migrating-db2-data-into-sql-server-db2tosql.md).  
  
9. При необходимости обновите приложения базы данных.  
  
## <a name="see-also"></a>См. также:  
[Установка SSMA для DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-db2tosql.md)  
[Начало работы с SSMA для DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/getting-started-with-ssma-for-db2-db2tosql.md)  
