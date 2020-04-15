---
title: Пример исхода данных (англ.) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 48c87f0d9f0a48b7d216151178c15bb019c0cbaa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306525"
---
# <a name="data-source-example"></a>Образец источника данных
На компьютерах под управлением Microsoft® Windows NT® Server/Windows 2000 Server, Microsoft Windows NT Workstation/Windows 2000 Professional или Microsoft Windows® 95/98, информация об источнике данных машины хранится в реестре. В зависимости от того, под каким ключом реестра хранится информация, источник данных известен как *источник пользовательских данных* или *источник системных данных.* Источники пользовательских данных хранятся под ключом HKEY_CURRENT_USER и доступны только текущему пользователю. Системные источники данных хранятся под HKEY_LOCAL_MACHINE ключом и могут использоваться более чем одним пользователем на одной машине. Они также могут быть использованы общесистемными службами, которые затем могут получить доступ к источнику данных, даже если пользователь не входит в систему. Для получения более подробной информации об источниках пользовательских и системных данных [см.](../../odbc/reference/syntax/sqlmanagedatasources.md)  
  
 Предположим, что у пользователя есть три источника пользовательских данных: персонал и инвентаризация, которые используют Oracle DBMS; и платежная ведомость, которая использует DBMS сервера Microsoft S'L. Значения реестра для источников данных могут быть:  
  
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
  
 и значения реестра для источника данных Payroll могут быть:  
  
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
