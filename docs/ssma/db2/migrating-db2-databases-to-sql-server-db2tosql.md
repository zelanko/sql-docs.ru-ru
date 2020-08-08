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
ms.openlocfilehash: c0a762cbe49a3186a29feb5aa3424b083d2f8978
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87933745"
---
# <a name="migrating-db2-databases-to-sql-server-db2tosql"></a>Перенос баз данных DB2 в SQL Server (DB2ToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Помощник по миграции (SSMA) для DB2 — это Комплексная среда, которая помогает быстро перенести базы данных DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure или. С помощью SSMA для DB2 можно просматривать объекты и данные базы данных, оценивать базы данных для миграции, переносить объекты базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure, а затем переносить данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure или из нее. Обратите внимание, что нельзя перенести схемы SYS и SYSTEM DB2.  
  
## <a name="recommended-migration-process"></a>Рекомендуемый процесс миграции  
Чтобы успешно перенести объекты и данные из баз данных DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базу данных SQL Azure, используйте следующую процедуру.  
  
1.  [Новый проект SSMA](https://msdn.microsoft.com/66437b45-4686-4fc7-a91b-ebde45e0f1b0).  
  
    После создания проекта можно задать параметры преобразования проекта, миграции и сопоставления типов. Сведения о параметрах проекта см. в разделе [Параметры проекта &#40;преобразование&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md) и связанные разделы. Сведения о настройке сопоставлений типов данных см. в разделе [Сопоставление типов данных DB2 и SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
2.  [Подключитесь к базе данных DB2](https://msdn.microsoft.com/5eb5801d-f0c3-4127-97c0-0b1ef49f4844).  
  
3.  [Подключение к SQL Server](https://msdn.microsoft.com/b59803cb-3cc6-41cc-8553-faf90851410e).  
  
4.  [Сопоставьте схемы DB2 с SQL Server схемами](https://msdn.microsoft.com/05ff7bd4-e60b-4f48-a893-bc2346aa9a8a).  
  
5.  При необходимости [отчеты об оценке](https://msdn.microsoft.com/9e13eba0-e3cf-4205-974f-c00f982061de) позволяют оценить объекты базы данных для преобразования и оценить время преобразования.  
  
6.  [Преобразование схем DB2](https://msdn.microsoft.com/7947efc3-ca86-4ec5-87ce-7603059c75a0).  
  
7.  [Загрузите преобразованные объекты базы данных в SQL Server](https://msdn.microsoft.com/f4ea1ced-9f9f-4a9d-88ab-81dbab64adc3).  
  
    Это можно сделать одним из следующих способов:  
  
    -   Сохраните скрипт и запустите его в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    -   Синхронизируйте объекты базы данных.  
  
8.  [Перенос данных DB2 в SQL Server](https://msdn.microsoft.com/86cbd39f-6dac-409a-9ce1-7dd54403f84b).  
  
9. При необходимости обновите приложения базы данных.  
  
## <a name="see-also"></a>См. также:  
[Установка SSMA для DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-db2tosql.md)  
[Начало работы с SSMA для DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/getting-started-with-ssma-for-db2-db2tosql.md)  
  
