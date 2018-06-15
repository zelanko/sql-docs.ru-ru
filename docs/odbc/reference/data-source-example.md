---
title: Пример источника данных | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], examples
ms.assetid: cbf15f32-0550-4c74-8088-8f7ac3855469
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 19e5596107f5bae9ceeab8ae105203e89584e854
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909189"
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
