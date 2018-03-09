---
title: "Просмотр журнала ошибок SQL Server (среда SQL Server Management Studio) | Документы Майкрософт"
ms.custom: 
ms.date: 09/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- viewing logs
- displaying logs
- errors [SQL Server], logs
- logs [SQL Server], SQL Server error logs
- logs [SQL Server], viewing
ms.assetid: 55f468ba-146c-4ab3-95cd-d35d051afd12
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Active
ms.openlocfilehash: a8823906fc96755dd70862e0a362562b956d2739
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="view-the-sql-server-error-log-sql-server-management-studio"></a>Просмотр журнала ошибок SQL Server (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записываются пользовательские и определенные системные события, которые могут пригодиться при устранении неполадок. 

## <a name="view-the-logs"></a>Просмотр журналов

1. В среде SQL Server Management Studio выберите элемент **Обозреватель объектов**. Чтобы открыть **обозреватель объектов**, нажмите клавишу F8. Либо в главном меню щелкните **Вид** и выберите пункт **Обозреватель объектов**:
    
    ![Object_Explorer](../../relational-databases/performance/media/object-explorer.png) 

2. В **обозревателе объектов** подключитесь к экземпляру SQL Server и разверните его.
  
3. Найдите и разверните раздел **Управление** (при условии, что у вас есть разрешения на его просмотр).

4. Щелкните элемент **Журналы SQL Server** правой кнопкой мыши, выберите пункт **Вид**, а затем **журнал SQL Server**.

    ![View_SQLServer_Log_SSMS](../../relational-databases/performance/media/view-sqlserver-log-ssms.png) 
 
5. Появится **средство просмотра журнала** (возможно, придется немного подождать) со списком журналов для просмотра.
  
  ## <a name="see-also"></a>См. также раздел
  Дополнительные сведения см. в полезной статье [Нахождение файла с журналом ошибок SQL Server](https://www.mssqltips.com/) на сайте [MSSQLTips.com](https://www.mssqltips.com/sqlservertip/2506/identify-location-of-the-sql-server-error-log-file/).

