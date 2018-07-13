---
title: Установка и изменение параметров сортировки для сервера| Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- server collations [SQL Server]
- collations [SQL Server], server
ms.assetid: 3242deef-6f5f-4051-a121-36b3b4da851d
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5d26e7d3569d069c01cf75459cb4cb898587d2f2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37176071"
---
# <a name="set-or-change-the-server-collation"></a>Задание или изменение параметров сортировки сервера
  Параметры сортировки сервера применяются по умолчанию для всех установленных системных баз данных с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также для новых пользовательских баз данных. Параметры сортировки сервера задаются во время установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в статье [Collation and Unicode Support](collation-and-unicode-support.md).  
  
## <a name="changing-the-server-collation"></a>Изменение параметров сортировки сервера  
 Чтобы изменить параметры сортировки по умолчанию для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (эта операция может оказаться сложной), выполните следующие шаги:  
  
-   Проверьте наличие данных и скриптов, необходимых для повторного создания пользовательской базы данных и всех ее объектов.  
  
-   Экспортируйте все данные с помощью такого средства, как [bcp Utility](../../tools/bcp-utility.md). Дополнительные сведения см. в разделе [Массовый импорт и экспорт данных (SQL Server)](../import-export/bulk-import-and-export-of-data-sql-server.md).  
  
-   Удалите все пользовательские базы данных.  
  
-   Перестройте базу данных master, указав новые параметры сортировки в свойстве SQLCOLLATION команды **setup** . Например:  
  
    ```  
    Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName   
    /SQLSYSADMINACCOUNTS=accounts /[ SAPWD= StrongPassword ]   
    /SQLCOLLATION=CollationName  
    ```  
  
     Дополнительные сведения см. в статье [Перестроение системных баз данных](../databases/system-databases.md).  
  
-   Создайте все базы данных и все их объекты.  
  
-   Импортируйте все данные.  
  
> [!NOTE]  
>  Вместо изменения параметров сортировки по умолчанию для всего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]можно указывать параметры сортировки по умолчанию для каждой новой базы данных.  
  
## <a name="see-also"></a>См. также  
 [Collation and Unicode Support](collation-and-unicode-support.md)   
 [Установка и изменение параметров сортировки базы данных](set-or-change-the-database-collation.md)   
 [Задание или изменение параметров сортировки столбца](set-or-change-the-column-collation.md)   
 [Перестроение системных баз данных](../databases/system-databases.md)  
  
  
