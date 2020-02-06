---
title: Просмотр журнала ошибок SQL Server (SSMS)
description: Просмотр журнала ошибок SQL Server в среде SQL Server Management Studio (SSMS).
ms.custom: seo-dt-2019
ms.date: 09/29/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- viewing logs
- displaying logs
- errors [SQL Server], logs
- logs [SQL Server], SQL Server error logs
- logs [SQL Server], viewing
ms.assetid: 55f468ba-146c-4ab3-95cd-d35d051afd12
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: f6410575af0d05b8d407ba9f52cc116fbe2ac733
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "74165473"
---
# <a name="view-the-sql-server-error-log-in-sql-server-management-studio-ssms"></a>Просмотр журнала ошибок SQL Server в среде SQL Server Management Studio (SSMS)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
В журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записываются пользовательские и определенные системные события, которые могут пригодиться при устранении неполадок. 

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

