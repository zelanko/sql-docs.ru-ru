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
ms.openlocfilehash: 06080937156afc4e38c9ef59bd9b92e98695eb57
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91867875"
---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a>Настройка хранилища данных точки управления служебной программы (служебная программа SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Данные, собранные управляемыми экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , хранятся в хранилище данных управления для программы (UMDW), имя файла UMDW — sysutility_mdw.  
  
 Можно задать сроком хранения данных в UMDW. Дополнительные сведения см. в статье [Администрирование программ (служебная программа SQL Server)](/previous-versions/sql/sql-server-2016/ee240832(v=sql.130)).  
  
 Перечисленные далее параметры конфигурации не могут быть изменены в этой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Имя UMDW: Sysutility_mdw.  
  
-   Частота передачи набора элементов сбора: каждые 15 минут.  
  
 Каталог UMDW можно настроить: \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<имя_UCP>\MSSQL\Data\\, где \<System drive> — это чаще всего диск C:\. Файл журнала Sysutility_mdw_\<GUID>_LOG находится в том же каталоге.  
  
> [!NOTE]  
>  Расположение файла UMDW (sysutility_mdw) можно изменить путем отсоединения и присоединения или с помощью инструкции ALTER DATABASE. Рекомендуется использовать инструкцию ALTER DATABASE. Дополнительные сведения см. в разделе [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Функции и задачи служебной программы SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
