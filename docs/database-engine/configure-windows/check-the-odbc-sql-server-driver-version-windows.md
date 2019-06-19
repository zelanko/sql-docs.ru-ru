---
title: Проверка версии драйвера ODBC для SQL Server (Windows) | Документы Майкрософт
ms.custom: ''
ms.date: 11/07/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- driver version number [ODBC]
- ODBC drivers, version number
ms.assetid: 43451080-a562-4231-b1d4-1ba35ca0ea79
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: fb6646d96991785b7c94a48ad4601fdcc6e35b60
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66799549"
---
# <a name="check-the-odbc-sql-server-driver-version-windows"></a>Проверка версии драйвера ODBC для SQL Server (Windows)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  На компьютере могут быть установлены разнообразные драйверы ODBC, разработанные как [!INCLUDE[msCoName](../../includes/msconame-md.md)] , так и другими организациями. В этом разделе описано, как с помощью **администратора источников данных ODBC** операционной системы Windows проверить версию установленных драйверов ODBC.  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-check-the-odbc-sql-server-driver-version-32-bit-odbc"></a>Проверка версии драйвера ODBC SQL Server (32-разрядная версия ODBC)  
  
-   В **администраторе источников данных ODBC**перейдите на вкладку **Драйверы** .  
  
     В столбце [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Версия **отображается запись для Microsoft** .  


> [!NOTE]  
>  Настраивая подключения для проверки подлинности Azure Active Directory для базы данных SQL, установите последнюю версию драйвера, например [версию 13.1 драйвера ODBC для SQL Server](https://www.microsoft.com/download/details.aspx?id=53339).   

  
## <a name="see-also"></a>См. также:  
 [Открытие администратора источника данных ODBC](../../database-engine/configure-windows/open-the-odbc-data-source-administrator.md)  
  
  
