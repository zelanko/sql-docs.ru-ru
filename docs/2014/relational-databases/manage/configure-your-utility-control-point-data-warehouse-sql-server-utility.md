---
title: Настройка хранилища данных для точки управления служебной программой (служебная программа SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d2a9f40c2d1566a1f8ca5f054467f61da1920e5f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62805940"
---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a>Настройка хранилища данных точки управления служебной программы (служебная программа SQL Server)
  Данные, собранные управляемыми экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , хранятся в хранилище данных управления для программы (UMDW), имя файла UMDW — sysutility_mdw.  
  
 Можно задать сроком хранения данных в UMDW. Дополнительные сведения см. в статье [Администрирование программ (служебная программа SQL Server)](../../database-engine/utility-administration-sql-server-utility.md).  
  
 Перечисленные далее параметры конфигурации не могут быть изменены в этой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Имя UMDW: Sysutility_mdw.  
  
-   Частота передачи набора элементов сбора: каждые 15 минут.  
  
 Каталог UMDW можно настроить: <системный диск\<:\Program Files\Microsoft SQL Server\MSSQL10_50.<имя_UCP>\MSSQL\Data\\, где \<системный диск> — это чаще всего диск C:\. Файл журнала Sysutility_mdw_\<GUID>_LOG находится в том же каталоге.  
  
> [!NOTE]  
>  Расположение файла UMDW (sysutility_mdw) можно изменить путем отсоединения и присоединения или с помощью инструкции ALTER DATABASE. Рекомендуется использовать инструкцию ALTER DATABASE. Дополнительные сведения см. в разделе [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql).  
  
## <a name="see-also"></a>См. также:  
 [Функции и задачи служебной программы SQL Server](sql-server-utility-features-and-tasks.md)  
  
  
