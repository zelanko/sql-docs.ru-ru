---
title: Пример источника данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], examples
ms.assetid: cbf15f32-0550-4c74-8088-8f7ac3855469
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f427074f7cd7153f448aaef43bc4ac5dca84c01
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63186314"
---
# <a name="data-source-example"></a>Образец источника данных
На компьютерах под управлением Microsoft® Windows NT® Server и Windows 2000 Server, Microsoft Windows NT Workstation и Windows 2000 Professional или Microsoft Windows® 95/98, данные компьютера источника хранится в реестре. В зависимости от того, какие параметры реестра ключа сведения хранятся в разделе, источник данных называется *источника данных* или *системный источник данных*. Пользовательские источники данных хранятся в разделе HKEY_CURRENT_USER и доступны только для текущего пользователя. Системные источники данных хранятся в разделе HKEY_LOCAL_MACHINE и может использоваться более чем одним пользователем, на одном компьютере. Они также могут использоваться службами всей системы, которые затем могут получить доступ к источнику данных, даже если пользователь не вошел в систему на компьютере. Дополнительные сведения о пользовательских и системных источников данных, см. в разделе [SQLManageDataSources](../../odbc/reference/syntax/sqlmanagedatasources.md).  
  
 Предположим, что у пользователя есть три источника данных пользователя: Только у сотрудников и инвентаризации, которые используют СУБД с Oracle; и платежных ведомостей, который использует СУБД Microsoft SQL Server. Значения реестра для источников данных могут быть:  
  
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
                         FastConnectOption : REG_SZ : No                          UseProcForPrepare : REG_SZ : Yes  
                         OEMTOANSI : REG_SZ : No  
                         LastUser : REG_SZ : smithjo  
                         Database : REG_SZ : Payroll  
                         Language : REG_SZ :  
```
