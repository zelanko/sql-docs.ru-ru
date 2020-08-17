---
description: Образец источника данных
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f0d165279dc0b2f4b056d2e214461c7ef019956b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386050"
---
# <a name="data-source-example"></a>Образец источника данных
На компьютерах, работающих под управлением Microsoft® Windows NT® Server/Windows 2000 Server, Microsoft Windows NT Workstation/Windows 2000 Professional или Microsoft Windows® 95/98, сведения об источнике данных компьютера хранятся в реестре. В зависимости от того, в каком разделе реестра хранятся данные, источник данных называется *источником данных пользователя* или *системным источником данных*. Источники данных пользователя хранятся в ключе HKEY_CURRENT_USER и доступны только текущему пользователю. Системные источники данных хранятся в ключе HKEY_LOCAL_MACHINE и могут использоваться несколькими пользователями на одном компьютере. Они также могут использоваться службами на уровне системы, которые затем могут получить доступ к источнику данных, даже если на компьютере не вошел ни один пользователь. Дополнительные сведения о пользовательских и системных источниках данных см. в разделе [склманажедатасаурцес](../../odbc/reference/syntax/sqlmanagedatasources.md).  
  
 Предположим, что у пользователя есть три пользовательских источника данных: персонал и Инвентаризация, которые используют СУБД Oracle; и Payroll, которая использует Microsoft SQL Server СУБД. Для источников данных могут использоваться следующие значения реестра:  
  
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
  
 и значения реестра для источника данных о зарплате могут быть:  
  
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
