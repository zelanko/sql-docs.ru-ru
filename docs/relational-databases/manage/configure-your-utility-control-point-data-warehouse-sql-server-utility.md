---
title: Настройка хранилища данных для точки управления служебной программой (служебная программа SQL Server) | Документация Майкрософт
description: Сведения о хранилище данных управления служебной программой, где экземпляры SQL Server хранят данные. Сведения о том, как настроить каталог и срок хранения данных.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e35e6e779a138633c8ea15c79a2d1370c1b3edcf
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775991"
---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a>Настройка хранилища данных точки управления служебной программы (служебная программа SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Данные, собранные управляемыми экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , хранятся в хранилище данных управления для программы (UMDW), имя файла UMDW — sysutility_mdw.  
  
 Можно задать сроком хранения данных в UMDW. Дополнительные сведения см. в статье [Администрирование программ (служебная программа SQL Server)](https://msdn.microsoft.com/library/3e5a00c3-8905-40f0-9ddc-d924df9c2f0d).  
  
 Перечисленные далее параметры конфигурации не могут быть изменены в этой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Имя UMDW: Sysutility_mdw.  
  
-   Частота передачи набора элементов сбора: каждые 15 минут.  
  
 Каталог UMDW можно настроить: \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<имя_UCP>\MSSQL\Data\\, где \<System drive> — это чаще всего диск C:\. Файл журнала Sysutility_mdw_\<GUID>_LOG находится в том же каталоге.  
  
> [!NOTE]  
>  Расположение файла UMDW (sysutility_mdw) можно изменить путем отсоединения и присоединения или с помощью инструкции ALTER DATABASE. Рекомендуется использовать инструкцию ALTER DATABASE. Дополнительные сведения см. в разделе [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Функции и задачи служебной программы SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  
