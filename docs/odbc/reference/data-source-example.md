---
title: "Пример источника данных | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data sources [ODBC], examples
ms.assetid: cbf15f32-0550-4c74-8088-8f7ac3855469
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 85eae404d4fa0ab739c699c8f120c76122c8ba67
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="data-source-example"></a>Пример источника данных
На компьютерах под управлением Microsoft® Windows NT® Server или Windows 2000 Server, Microsoft Windows NT Workstation или Windows 2000 Professional или Microsoft Windows 95/98, данные машина сведения об источнике хранится в реестре. В зависимости от того, какие параметры реестра ключа сведения хранятся в, источник данных называется *источника данных* или *системного источника данных*. Пользовательские источники данных хранятся в разделе HKEY_CURRENT_USER и доступны только для текущего пользователя. Системные источники данных хранятся в разделе HKEY_LOCAL_MACHINE и может использоваться больше одного пользователя на одном компьютере. Они также могут использоваться по службами всей системы, которые получают доступ к источнику данных даже если пользователь не вошел в систему на компьютере. Дополнительные сведения о пользовательских и системных источников данных см. в разделе [SQLManageDataSources](../../odbc/reference/syntax/sqlmanagedatasources.md).  
  
 Предположим, что у пользователя есть три пользовательские источники данных: персонала и инвентаризации, которые используют СУБД Oracle; и заработной платы, которая использует СУБД Microsoft SQL Server. Возможно, параметры реестра для источников данных:  
  
```  
HKEY_CURRENT_USER  
SOFTWARE  
          ODBC  
               Odbc.ini  
                    ODBC Data Sources  
                    Personnel : REG_SZ : Oracle  
                    Inventory : REG_SZ : Oracle  
                    Payroll : REG_SZ : SQL Server  
```  
  
 и значения реестра для источника данных заработной платы могут быть:  
  
```  
HKEY_CURRENT_USER  
     SOFTWARE  
          ODBC  
               Odbc.ini  
                    Payroll  
                         Driver : REG_SZ : C:\WINDOWS\SYSTEM\Sqlsrvr.dll  
                         Description : REG_SZ : Payroll database  
                         Server : REG_SZ : PYRLL1  
                         FastConnectOption : REG_SZ : No                          UseProcForPrepare : REG_SZ : Yes  
                         OEMTOANSI : REG_SZ : No  
                         LastUser : REG_SZ : smithjo  
                         Database : REG_SZ : Payroll  
                         Language : REG_SZ :  
```

